# 조인 (JOIN)

관계형 데이터베이스에서는 중복을 피하기위해 테이블을 쪼개서 여러테이블로 저장한다(정규화)

분리된 테이블에서 원하는 데이터를 가져오기 위해 관련있는 컬럼 기준으로 행을 합쳐주는 연산.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0fe3dbca-ce22-4cc5-a68d-d70e8717a5d5/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0fe3dbca-ce22-4cc5-a68d-d70e8717a5d5/Untitled.png)

**교차 조인 (CROSS JOIN - CARTESIN PRODUCT)**

교차 조인은 두 테이블의 카티션 프로덕트(곱집합)를 한 결과입니다. 특별한 조건없이 테이블 A의 각 행과 테이블 B의 각 행을 다 조합한 결과입니다.

### 내부조인(INNER JOIN)

두 테이블에서 전부 존재하는 데이터만 조회 = 교집합

2개(이상)의 테이블을 합쳐 새로운 테이블을 생성한다. 그 후 조건문에 맞는 레코드를 반환

### 외부조인(OUTER JOIN)

내부 조인은 공통 컬럼명 기반으로 결과 집합을 생성. 반면 외부조인은 조건문에 만족하지 않는 행도 표시해주는 조인.

지정된 쪽(left, right)의 모든 결과를 가져온 후, 반대편 테이블의 데이터를 매칭하고, 매칭 값이 없을시 NULL 값 매칭

- left, right, full
