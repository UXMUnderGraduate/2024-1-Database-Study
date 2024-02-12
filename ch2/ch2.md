# Database 2/32

Date: 2024년 2월 12일
Tags: Database study

# Introduction to the Relational Model

### Structure of Relational Databases

- Relation → 테이블
- tuple → 행
- attribute → 열
- 예시
    
    특정 행이 연관되어 있는 table
    
    각 행을 instance라고 부름
    
    값을 모르거나 존재하지 않으면 null value 라고 부름
    
    > Relation은 tuple의 집합
    > 
    
    > domain은 attribute(열)의 이름 ex)dept_name
    > 
    
    > 다른 domain과 관련이 없는 domain은 atomic(원자적)
    > 
    
    ![Untitled](Database%202%2032%205081b26b9c374ef7a267fa1d91d29bec/Untitled.png)
    
    ![Untitled](Database%202%2032%205081b26b9c374ef7a267fa1d91d29bec/Untitled%201.png)
    

### Database Schema

> 데이터베이스 내에서 데이터가 어떤 구조로 저장되는지 정의
> 

Database Schema : 데이터베이스의 논리적 설계

Database instance : 데이터베이스의 스냅샷 (변수에 해당)

Relation Schema는 attribute와 해당 domain으로 구성되어 있다.

- 예시
    
    ![Untitled](Database%202%2032%205081b26b9c374ef7a267fa1d91d29bec/Untitled%202.png)
    
    ⇒ teaches (ID, course id, sec id, semester, year)
    
    ![Untitled](Database%202%2032%205081b26b9c374ef7a267fa1d91d29bec/Untitled%203.png)
    

### Keys

> 조건에 만족하는 튜플을 찾거나, 순서대로 정렬할 때 다른 튜플들과 구별할 수 있는 기준이 되는 속성
> 

- 종류
    - superkey : 유일성을 만족하는 키
    - candidate keys : 슈퍼키중에 최소성을 만족하지 못하는 키
    - primary key
        - 후보키 중에서 선택된 최소성과 유일성을 만족하는 키
        - 테이블에서 오직 1개만 존재 가능
        - 중복된 값을 가질수 없음
    - foreign key : 참조되는 테이블의 기본 키
    
    ![스크린샷 2024-02-12 오후 5.22.31.png](Database%202%2032%205081b26b9c374ef7a267fa1d91d29bec/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2024-02-12_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_5.22.31.png)
    

### Schema Diagrams

primaty key와 foreign key를 포함한 박스 형태로 다이어그램을 그림

![Untitled](Database%202%2032%205081b26b9c374ef7a267fa1d91d29bec/Untitled%204.png)

- primary key는 밑줄로 표시
- foreign key는 부모, 자식 테이블간 화살표로 표시

### Relational Query Languages

Query Languages : 사용자가 데이터베이스에 정보를 요청하는 언어

- Imperative query language : 데이터베이스에 특정 작업을 수행하도록 지시
- functional query language : 데이터베이스의 데이터/ 다른 함수의 평가
- declarative query language : 특정 정보를 설명

### Relational Algebra (관계 대수)

기존 테이블에서 새로운 테이블을 생성하는 절차적 언어 문법

- Select : 해당하는 값만 가져옴
    - σdept name = “Physics” (instructor )
- Project : 특정한 내용을 출력함
    - ΠID, name, salary(instructor)
- Cartesian-Product : 나올수 있는 조합의 경우의 수
    - instructor × teaches
- Join : 두개의 테이블에서 관련된 튜플을 결합
    - [σinstructor.ID=teaches.ID](http://xn--instructor-prh.id=teaches.id/)(instructor × teaches)
- Assignment : 중간결과 표현을 임시로 저장 가능
    - courses fall 2017 ← Πcourse_id(σsemester=“Fall”∧year=2017 (section))
- Rename : 테이블 이름이나 속성 이름을 변경
    - ρx (E)

- 연습문제
    
    2.1 Person_name
    
    2.3 같은 시간대에 여러가지 종료시각이 있는 경우 키의 복잡성이 증가
    
    2.5 카티션 프로덕트를 했을 때 : 6열, (students 행 수 * advisor 행 수)행
    
    S_id와 ID가 일치하는 튜플만 출력
    
    2.7 a. *πbranch_name(σbranch_city=’Chicago’(branch))*
    
     b. *πID(σbranch_name=’Downtown’(borrower ⋈ loan))*
    
    2.9
    
    2.11 s_id가 계속 primary key로 있을 수 있다. 학생의 테이블에 advisor가 추가되는 것이므로 advisor 테이블에 영향을 끼치지 않을 것이다
    
    2.13 
    
    ![Untitled](Database%202%2032%205081b26b9c374ef7a267fa1d91d29bec/Untitled%205.png)
    
    2.15
    
    1. *π*loan number(*σ*amount>10000(loan))
    2. *π*ID(*σ*balance>6000(depositor⋈account))
    3. *π*ID(*σ*balance>6000∧branch name=′*Uptown*(depositor⋈account))
    
    2.17 
    
    1. imperative : 저수준을 다루므로 성능을 높일 수 있다
    2. functional : 함수의 조합으로 구성되기 때문에 상태관리가 단순하다
    3. declarative : 코드 추상화 수준이 높아져 가독성이 높다