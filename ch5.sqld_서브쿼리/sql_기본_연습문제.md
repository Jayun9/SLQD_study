## 문제 1. PRODUCTS 테이블에서 LIST_PRICE의 가격이 평균 가격보다 큰 행(집합)의 PRODUCT_ID, PRODUCT_NAME, LIST_PRICE 컬럼을 구하는 SELECT문을 작성하고 PRODUCT_NAME으로 정렬하라. 

![image-20210421131217884](.\sql기본연습문제image\image-20210421131217884.png)

- 나의 풀이

```sql
SELECT 
	PRODUCT_ID
	, PRODUCT_NAME
	, LIST_PRICE
FROM PRODUCTS
WHERE LIST_PRICE >= (
						SELECT AVG(LIST_PRICE)
    					FROM PRODUCT
)
ORDER BY PRODUCT_NAME;
```

- 정답

```sql
SELECT A.PRODUCT_ID
	, A.PRODUCT_NAME
	, A.LIST_PRICE
FROM PRUDCTS A
WHERE A.LIST_PRICE > (
						SELECT AVG(K.LIST_PRICE)
    					FROM PRODUCTS K
)
ORDER BY A.PRODUCT_NAME;
```

틀린점

1. 큰 이라 = 없애기

2. 꼭 틀린건 아니지만 별칭 줘서 가독성 높이기



## 문제 2. CUSTOMERS 테이블에서 CREDIT_LIMIT의 값이 가장 큰 10건의 행을 출력하라. (단, CUSTOMERS 테이블의 모든 칼럼을 출력하고 CREDIT_LIMIT이 동일하다면 NAME을 칼럼을 기준으로 오름차순 정렬로 출력하라)

![image-20210421133501887](.\sql기본연습문제image\image-20210421133501887.png)

- 나의 풀이

```SQL
SELECT A.* 
FROM CUSTOMERS A
WHERE A.CREDIT_LIMIT = (
						SELECT MAX(B.CREDIT_LIMIT)
    					FROM CUSTOMERS B
)
ORDER BY NAME
ROWNUM = 10;
```

- 답

```sql
SELECT *
FROM (
	SELECT *
    FROM CUSTOMERS C
    ORDER BY CREDIT_LIMIT DESC, NAME
)
WHERE ROWNUM <= 10;
```

1. CREDIT_LIMT이 같은게 아니니까 인라인 뷰를 사용해야 함. 
2. ROWNUM 은 WHERE 절에서 같이 사용해야 함. 