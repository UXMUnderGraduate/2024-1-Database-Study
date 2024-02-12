# Database 1/32

Date: 2024년 2월 7일
Tags: Database study

<aside>
💡 Database System Concepts

</aside>

/

# Database-management System(DBMS)

- 데이터베이스 관리 시스템
    - 상호 연관된 데이터와 데이터에 접근하기 위한 프로그램들
- 데이터베이스
    - 데이터들의 집합, 기업에 필요한 정보를 가지고 있음
- 목표
    - 편리하고 효율적이게 데이터베이스 정보를 저장하고 회수하는 방법을 제공
        - 대부분의 조직에서 정보는 중요하기 때문에, 프로그래머들은 데이터를 관리하는 거대한 양의 개념과 기술을 발전시켰고, 그것이 이 책의 핵심

## Database-System Applications

```
응용프로그램의 핵심은 데이터 그 자체이다
(계산을 제공하는 프로그램이 아니라)
```

데이터베이스는 다음과 같은 데이터 모음을 관리한다

- 높은 가치가 있는 데이터
- 비교적 거대한 데이터
- 다양한 사용자와 응용프로그램에게 종종 동시에 접근당하는 데이터

복잡성 관리의 핵심은 **추상화**의 개념이다

- 추상화는 복잡한 기기나 시스템을 사용자가 내부 작동방식을 이해하지 않고 사용할 수 있게 한다 (엔진 작동방식을 몰라도 차를 운전 가능)

### two modes

- 온라인 거래 처리
- 데이터 분석

데이터 분석 기술은 데이터에서 규칙과 패턴을 발견, 예측 모델을 만드려고 시도함

## Purpose of Database System

컴퓨터에 정보를 보관하는 방법중 한가지는 운영체제 파일에 저장하는 것이다.

파일에서 적절한 기록을 추출하고 추가하기 위해 다양한 응용 프로그램이 필요한데, 파일 처리 시스템에 정보를 보관하는것은 다음과 같은 단점이 있다.

- 데이터 중복과 불일치
- 데이터 접근의 불편함
- 데이터 고립
- 무결성 문제
- 원자성 문제
- 동시 접근 문제
- 보안 문제

이러한 문제들이 **데이터베이스의 초기 개발**와 파일 기반 응용 프로그램 ⇒ **데이터베이스 시스템**으로 전환을 촉발했다.

## View of Data

데이터베이스 시스템의 주요 목적은 사용자에게 데이터가 저장되고 유지되는 세부 사항을 숨기고, 추상적인 견해를 제공하는데에 있다.

- Data Models
    - Relational Model
        - 데이터베이스 응용 프로그램의 기초 역할
        - 데이터는 테이블 형태로 표시
        
        ![Untitled](Database%201%2032%2051c23441ff0d43b89fca3380ef19fe55/Untitled.png)
        
    - Entity-Relationship Model
    - Semi-structured Data Model
    - Object-Based Data Model

- Data Abstraction

데이터를 효율적으로 검색하기 위해 데이터베이스 시스템 개발자들은 복잡한 데이터 구조를 사용했고, 개발자는 사용자와 시스템의 상호작용을 단순화 하기위해 여러 수준의 데이터 추상화를 통해 복잡성을 숨긴다

- Physical level
    - 데이터가 어떻게 저장 되었는지 설명
    - 복잡한 낮은 수준의 데이터 구조를 자세히 설명
- logical level
    - 무슨 데이터가 저장 되었는지, 어떤 관계가 데이터 사이에 존재하는지
    - 비교적 간단한 구조의 관점에서 전체 데이터베이스를 설명 → 물리적 데이터 독립
- View level
    - 전체 데이터베이스의 일부만을 설명
    - 동일한 데이터베이스에 대해 많은 시점 제공

![Untitled](Database%201%2032%2051c23441ff0d43b89fca3380ef19fe55/Untitled%201.png)

데이터 모델은 데이터베이스 사용자 뿐만 아니라 개발자에게도 low-level 구현을 숨긴다.

![Untitled](Database%201%2032%2051c23441ff0d43b89fca3380ef19fe55/Untitled%202.png)

다음과 같은 코드는 instructor 라고 불리는 4가지 필드를 가진 새로운 유형을 정의한다.

- Instances and Schemas
    - instance
        - 특정 순간에 데이터베이스에 저장된 수집된 정보의 모음
    - schema
        - 데이터베이스의 전반적인 디자인, 변수 선언에 해당
        
        physical schema : 논리적 스키마 밑에 숨어있음, 프로그램에 영향 X, 쉽게 변경 가능
        
        logical schema : 프로그래머가 논리적 스키마를 사용하여 프로그램을 구성 → 중요
        

### Database Languages

- Data-Definition Language
    - 데이터베이스 스키마를 지정
        - 도메인 제약
        - 참조 무결성
        - 권한 부여
    - SQL Data-Definition Language
        
        ![Untitled](Database%201%2032%2051c23441ff0d43b89fca3380ef19fe55/Untitled%203.png)
        
- Data-Manipulation Language
    
    사용자가 데이터에 접근하거나 관리할 수 있는 언어
    
    - 데이터베이스에 저장된 정보의 검색
    - 데이터베이스에 새로운 정보 삽입
    - 데이터베이스에 정보 지정
    - 데이터베이스에 저장된 정보 수정
    
    Procedural DMLs → 필요한 데이터를 얻는 방법
    
    Declarative DMLs → 어떤 데이터가 필요한지 확인
    
    - SQL Data-Manipulation Language
    
    ![Untitled](Database%201%2032%2051c23441ff0d43b89fca3380ef19fe55/Untitled%204.png)
    
    ![Untitled](Database%201%2032%2051c23441ff0d43b89fca3380ef19fe55/Untitled%205.png)
    

### Database Design

- 대규모 정보를 관리하도록 설계되어 있음
- 데이터베이스 스키마 설계를 포함
    1. 데이터가 어떻게 활용될 것인지 요구사항을 확인, 구조화를 지정하는 개념적 프레임 작업
    2. 데이터 모델 선택, 요구사항을 스키마로 작성
    

### Database Engine

- storage manager
    
    디스크에 데이터를 저장 → 데이터 이동 속도 느림
    
    디스크와 메인 메모리간의 데이터 이동을 최소화 → 데이터 구조화
    
    > 데이터베이스에 저장된 low-level의 데이터와 프로그램및 쿼리간의 인터페이스 제공
    > 
    
    - 권한 부여 및 무결성 관리자
    - 거래 관리자
    - 파일 관리자
    - 버퍼 관리자
- query processor
    
    데이터 엑세스를 단순화
    
    사용자가 view level에서 작업 가능
    
    시스템의 구현 방식을 몰라도 됨
    
    - DDL interpreter
    - DML compiler
    - Query evaluation engine
- transaction manager
    
    데이터베이스 접근을 신경쓰지 않게 해줌
    

### Database and Application Architecture

![Untitled](Database%201%2032%2051c23441ff0d43b89fca3380ef19fe55/Untitled%206.png)

- 연습문제
    
    1.1 복잡하고 다양한 구조와 관계를 가진 데이터를 포함한다.
    
    복잡성을 관리하기 어렵다
    
    1.3 
    
    1. 요구사항 분석
    2. 데이터 모델링
    3. 데이터베이스 설계
    4. 데이터베이스 구현
    5. 데이터 적재
    6. 배포
    
    1.5
    
    1.7 데이터 중복 보호, 데이터 무결성 보장, 데이터베이스에 데이터 저장, 동시성 제어 및 트랜젝션 관리
    
    1.9
    
    1. 목적 : 웹에서 특정 정보를 검색 / 데이터베이스 안에서 정보를 검색
    2. 형식 : 짧은 텍스트 문장 / 쿼리 언어(SQL)
    
    1.11 Transaction manager, Buffer manager
    
    1.13 NoSQL 등장, 자동관리기능 추가
    
    1.15 사용자 정보 테이블, 게시물 테이블, 태그 테이블