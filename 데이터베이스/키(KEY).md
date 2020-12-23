# 키 (KEY)

### 키(key) : 데이터베이스에서 조건에 만족하는 튜플을 찾거나 순서대로 정렬할 때 다른 튜플들과 구별할 수 있는 유일한 기준이 되는 Attribute(속성)

- Key = Identifier
- Tuple을 구분할 수 있는 기준이 되는 속성

---

### 특성

- 유일성 : 하나의 key 값으로 하나의 tuple만을 유일하게 식별
- 최소성 : key를 구성하는 속성을 하나만 제외시켜도 유일성이 깨진다.

### 종류

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a55b0bfd-c30b-4f3e-8deb-2a2378989ecf/_2020-05-14__6.30.47.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a55b0bfd-c30b-4f3e-8deb-2a2378989ecf/_2020-05-14__6.30.47.png)

- 슈퍼키(Super Key)
- 후보키(Candidate Key)
- 기본키(Primary Key)
- 대체키(Alternate Key)
- 외래키(Foreign Key)

---

## 슈퍼키 (Super Key)

- Tuple을 유일하게 구분하기 위하여 한 개 이상의 속성들의 집합으로 이루어진 키
- 유일성 : O / 최소성 : X
- 예 : {학번, 이름}, {이름, 주민등록번호} 등

## 후보키 (Candidate Key)

- Tuple을 유일할게 구분할 수 있는 최소 슈퍼키
- 모든 Relation은 하나 이상의 후보키를 갖는다.
- 하나의 속성으로 후보키가 될 수 없는 경우 : 두개 이상의 속성 집합이 후보키가 되고, 이러한 키를 복합키(Composit Key)라고 한다.
- 유일성 : O / 최소성 : O
- 예 : 학번, 주민등록번호 등

## 기본키 (Primary Key)

- 후보키 중 특별히 선정된 주키 (Main Key)
- 절대 중복되는 값이나 null 값을 가져서는 안된다. (개체 무결성의 조건)
- 동일한 값이 중복으로 저장될 수 없다.
- 유일성 : O / 최소성 : O
- 예 : 학번, 주민등록번호 등 중 택 1

## 대체키 (Alternate Key)

- 하나의 Relation에 존재하는 후보키 중 기본키를 제외한 나머지
- 유일성 : O / 최소성 : O

## 외래키 (Foreign Key)

- 참조되는 릴레이션의 기본키와 대응되어 릴레이션 간의 참조 관계를 표현하는 중요한 도구
- 외래키로 지정되면 참조 테이블의 기본키에 없는 값은 입력할 수 없다.
- 현실 세계의 개체 타입을 표현하는데 중요한 역할 수행

[참고 자료] 예시와 설명을 잘해놨음

[http://blog.naver.com/PostView.nhn?blogId=seungp916&logNo=220064778834&redirect=Dlog&widgetTypeCall=true](http://blog.naver.com/PostView.nhn?blogId=seungp916&logNo=220064778834&redirect=Dlog&widgetTypeCall=true)
