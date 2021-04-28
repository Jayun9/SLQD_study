# sql 기본

## 1. select

```sql
select {컬럼명} from {테이블명} where {조건}
```

### dual

x만 정의 되어 있는 테이블 

```sql
select (10 +5) / 2 as var from dual
```

### distinct

```sql
select distinct {컬럼명} from {테이블명} 
```



## 2. insert

값 추가

```sql
insert intno {테이블명} (컬럼명1, 컬렴명2) values (값1, 값2)
```



## 3. update

값 갱신

```sql
update {테이블명} set {컬럼명} = {갱신할 값} where {조건}
```



## 4. delete

삭제

```sql
delete from {테이블명} where {조건}
```



## 5. view

자주 조회하는데 복잡한 쿼리 논리적으로 view 테이블로 설정해서 함께 공유해서 봄. 

### inline

```sql
selet a.*
	from
		(selct ~) a;
```

view 테이블 생성

```sql
create or replace view {만들 테이블 이름} as (select ~)
```

view 테이블 사용은 일반 테이블 사용하듯이 하면 된다. 

