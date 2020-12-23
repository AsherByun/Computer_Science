# 정규화(Normalization)

# 정규화(Normalization) 란?

- 관계형 데이터베이스의 설계에서 중복이 최소화하되도록 데이터를 구조화하는 프로세스
- 불필요한 데이터(Redundancy)를 없앨 수 있고, 데이터 삽입, 삭제, 수정 시 발생하는 각종 이상현상(Anamolies)을 방지할 수 있다.
- 데이터 저장을 논리적으로 한다 → 테이블의 구성이 논리적이고 직관적이여야 한다

## 정규화의 장점

- 최소의 데이터로 최적의 데이터베이스 구축 및 중복성 제거
- 종속성 삭제로 데이터의 일관성과 무결성 보장
- 릴레이션에서 발생가능한 이상현상 제거(삽입,삭제,갱신등)→삽입시 널값,삭제시 다른게삭제,갱신시 데이터 불일치→다른값들도 다 바껴야됨
- 중복의 최소화로 저장공간 효율

## 정규화의 단점

- Join 연산이 늘어난다 ⇒ 데이터를 불러오는 시간이 오래걸린다.
- 메모리 많이 필요.
- 과다한 검색 조건문이 발생

# 정규화의 단계

## 1-NF

- 모든 속성의 도메인이 원자 값으로만 구성되어 있어야 한다.

    → 새로운 행(로우)를 더만들면 된다.

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b9f16c15-ab17-4057-b280-b65c8810c45f/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b9f16c15-ab17-4057-b280-b65c8810c45f/Untitled.png)

    해결 후

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a20e59a9-3e36-46da-b464-25376524261a/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a20e59a9-3e36-46da-b464-25376524261a/Untitled.png)

## 2-NF

- 1-NF만 만족시키면 삽입, 갱신, 삭제 이상이 생길 수 있다.
- 완전 함수적 종속을 만족시켜야한다 → 기본키중에 특정 컬럼(부분적 종속)이 없어야 한다.
- 두 개 이상의 부분 함수 종속성을 가지는 column을 다른 Table로 나누어 준다.
- 2-NF를 만족시켜도 이상현상이 발생할 수 있다. (이행적 함수 종속 때문)

    이 문제를 제 3정규화에서 해결한다.

    Student 컬럼의 값을 알면 Age의 값을 알 수 있습니다. 따라서 Age가 두 번 들어가는 것은 불필요한 것으로 볼 수 있습니다.

    기본키(student,subject) → student만 알면 age를 알수있다

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/13e73ded-9075-47ab-b56a-1bdda274950f/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/13e73ded-9075-47ab-b56a-1bdda274950f/Untitled.png)

    **Student Table**

    [https://t1.daumcdn.net/cfile/tistory/99589D3359E789FA30](https://t1.daumcdn.net/cfile/tistory/99589D3359E789FA30)

    **Subject Table**

    [https://t1.daumcdn.net/cfile/tistory/99C5183359E789FB14](https://t1.daumcdn.net/cfile/tistory/99C5183359E789FB14)

## 3-NF

- 기본키를 제외한 속성들 간의 이행적 함수 종속이 없어야 한다 → 기본키 이외의 다른 컬림이 그외 컬럼을 결정할 수 없는 것!
- 이행적 함수 종속 : X→Y and Y→ Z ⇒ X→Z
- X→Y, X→Z 가 아닌 X→Y, Y→Z를 =표현하는 두개의 테이블을 만든다.
- 3-NF를 만족시켜도 이상현상이 발생할 수 있다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/db47dbfa-0981-4d2b-8f5e-d6f6a868c2a4/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/db47dbfa-0981-4d2b-8f5e-d6f6a868c2a4/Untitled.png)

해결 후

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cd33b5f9-5186-44b3-a105-f1525c658b8b/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cd33b5f9-5186-44b3-a105-f1525c658b8b/Untitled.png)

## BCNF(Boyce-Codd Normal Form)

- 모든 결정자가 후보키 집합에 속한 정규형
- 3-NF를 만족시키고 Relation의 후보키가 1개라면 BCNF 이다.

    하지만 후보키가 2개 이상이라면 BCNF가 아니다.

    [BCNF를 위반하는 경우] C→B 때문에 위반.

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/95521253-3778-42e6-9d7d-1d27cd33423f/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/95521253-3778-42e6-9d7d-1d27cd33423f/Untitled.png)

- BCNF를 위반하는 Relation 분해 과정
    1. BCNF를 위반하는 nontrivial FD X→Y 를 찾는다.
    2. 두개의 Relation으로 분해한다.

        (1) XY로 구성된 relation

        (2) X와 나머지 속성으로 구성된 relation

교수(일반 컬럼)이 후보키(학생,과목)을 결정하는 경우

→ 교수가 강의하는 과목명이 변경시 → 후보키를 갱신

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6c3ad7dd-6fc0-4d68-9e21-aab450db1f59/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6c3ad7dd-6fc0-4d68-9e21-aab450db1f59/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/58b69c8e-5a9e-4ed1-b96b-e4774eeec064/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/58b69c8e-5a9e-4ed1-b96b-e4774eeec064/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/36e6ccdb-0d63-4163-90a8-99c3eac2e37c/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/36e6ccdb-0d63-4163-90a8-99c3eac2e37c/Untitled.png)

[참고 자료] 예시와 설명이 매우 좋음

[1NF ~ 3NF] [https://yaboong.github.io/database/2018/03/09/database-normalization-1/](https://yaboong.github.io/database/2018/03/09/database-normalization-1/)

[BCNF] [https://yaboong.github.io/database/2018/03/10/database-normalization-2/](https://yaboong.github.io/database/2018/03/10/database-normalization-2/)

출처:

[https://3months.tistory.com/193](https://3months.tistory.com/193)
