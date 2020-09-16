본 정리 자료는 **코드잇 - SQL 데이터베이스**를 수강하며 배운 SQL 데이터베이스 지식을 정리한 내용입니다.

[코드잇 SQL 데이터베이스 코스](https://www.codeit.kr/courses/sql-database)

<details>
  <summary>1) 데이터베이스 기본 개념</summary>
  <details>
    <summary>데이터베이스와 테이블</summary>

# 데이터베이스와 테이블

## 데이터베이스란?

일정한 체계 속에 저장된 데이터의 집합

데이터는 보통 데이터베이스 안에서 테이블(Table)이라는 형태로 저장됨.

데이터베이스에 저장된 데이터로 시장과 고객을 잘 분석해야 기업이 잘될 수 있음

# 테이블의 row와 column

## 테이블

테이블이란 표 형태로 저장된 데이터의 집합

row는 '행' 이라는 뜻으로, 테이블에서 하나의 개체는 이 row로 표현됨

column은 '열'이라는 뜻으로, 테이블에서 각 개체가 가지는 하나의 속성은 이 column으로 표현됨

  </details>
  <details>
    <summary>DBMS와 SQL</summary>

# DBMS와 SQL

## DBMS (DataBase Management System)

데이터베이스 관리 시스템.

데이터베이스를 관리하는 프로그램

사용하는 DBMS에 따라서 데이터베이스의 종류가 다름

모든 DBMS에서는 SQL이라는 언어를 사용

### SQL (Structured Query Language)

DBMS에 명령을 내리기 위해 사용하는 언어

SQL은 국제 표준이 있어서, 어떤 DBMS에서든 사용할 수 있음

하지만 문제는, 모든 DBMS가 이 표준을 완벽하게 지키지는 않는다는 것

하지만 데이터를 다루는 대부분의 주요 기능은 DBMS마다 큰 차이가 없다

# SQL 국제 표준과 MySQL

## SQL 국제 표준

1970년대 초 IBM에 의해서 System/R이라는 DBMS와 , 이것을 사용하기 위해 필요한 언어인 SEQUEL(Structured English Query Language)가 만들어졌는데, 이후 SEQUEL(씨퀄)은 상표권 문제 때문에 그 이름이 SQL(Structured Query Language)로 변경됨.

2020.09 기준 2019 개정안이 최신임.

## MySQL이란?

MySQL은 페이스북, 유튜브 등을 비롯한 유명 서비스에서 활발히 사용되고 있는 DBMS임

MySQL은 MySQL B이라는 회사에서 개발되었는데, MySQL AB는 2008년 Sun Microsystems에 인수되고, 이 Sun Microsystems는 2010년 Oracle에 인수됨. 이에 따라 자연스럽게 MySQL 또한 Oracle의 소유가 되었음.

MySQL은 오픈 소스 소프트웨어로 누구나 자유롭게 사용할 수 있지만, 만약 MySQL의 소스 코드를 가져다가 일부를 수정하고 자신의 제품의 일부로 만들어서 재배포하는 상황에서 그 소스코드를 공개하지 않으려는 기업이 있다면 이 경우에는 Oracle엑서 제공하는 상업용 라이센스가 필요하다

Oracle은 자사의 기존 DBMS인 오라클과 기업 인수를 통해 얻은 MySQL 둘다 잘 서비스하고 있다고 한다. 둘 다 기술적으로 장단점이 다르고 상호보완적이 면이 있다.

### 오라클

은행, 거래소 등과 같이 데이터 처리의 정확성, 운영의 안정성 등이 엄격하게 요구되는 분야에서 주로 사용되고 있음

신뢰도가 중요한 비즈니스 분야에 적합하게 설계되어 있고, 해당 영역에서의 역사가 길다

### MySQL

우리가 흔히 쓰는 앱, 웹 사이트 같은 서비스를 만들 때 많이 사용 됨

무료로 사용할 수 있고, 좀 더 가볍다.

여러 DBMS 중에서도 특히 일반 사용자가 사용하기 편하다는 평가를 받는다.

요구하는 컴퓨터 성능도 작은 편이라 부담도 덜 함

IT 분야에서 LAMP(Linux + Apache + MySQL + PHP/Perl/Python)라고 하는 개발 플랫폼의 조합이 관용어로 쓰일 정도로 많은 개발자들이 보편적으로 쓰는 DBMS라고 함

# DBMS와 서버-클라이언트 구조

## 클라이언트와 서버

DBMS에는 주요 구성 요소인 두 종류의 프로그램이 있음.

1. **client(클라이언트 프로그램)** : 사용자가 server에 접속해서 원하는 데이터베이스 관련 작업을 할 수 있도록, SQL을 입력할 수 있는 화면 등을 제공하는 프로그램
2. **server(서버 프로그램)**: client로부터 SQL 문 등을 전달받아 데이터베이스 관련 작업을 직접 처리하는 프로그램. (DBMS라고 할 때, 좁은 의미로 이 server 부분만을 가리키는 경우도 있음)

대부분의 DBMS가 client를 통해 server에 접속하는 구조로 되어 있음.

server 안에 DB가 포함되어 있는데, 사실 데이터베이스는 DBMS와 분리된 것이 아니라, 이렇게 server가 직접 저장하고 관리하는 데이터의 집합이다.

결국 DBMS를 사용한다는 것은, **실행되고 있는 server에 client를 이용해서 접속한 후, 원하는 명령을 내린다는 뜻**

### MySQL Workbench

MySQL은 CLI(Command Line Interface) 환경에서 사용할 수도 있지만, Oracle이 공식 제공하는 GUI 환경인 **MySQL Workbench**라는 프로그램을 통해서도 사용할 수 있음

  </details>
  <details>
    <summary>MySQL 데이터베이스</summary>

# 데이터베이스 생성하기

MySQL에서는 데이터베이스를 스키마(Schema)라고 부르기도 함

'쿼리 창'에 SQL문을 입력하여 데이터베이스를 생성한다. `CREATE DATABASE 데이터베이스이름`

꼭 지켜야 하는 규칙은 아니지만, 관습적으로 명령을 대문자로 사용한다고 한다.

테이블이나 db 명과 구분되어 가독성이 더 높다고 한다.

# sys 데이터베이스

workbench를 실행할 때, 따로 생성하지 않았던 **sys**라는 데이터베이스가 이미 존재함.

sys 데이터베이스는 MySQL **서버의 성능 관련 정보**들을 가지고 있는 데이터베이스

## DBMS 사용 용도

사실 DBMS는 사용하는 사람에 따라 사용 용도가 크게 달라짐.

기획자/마케터:

- 데이터베이스에 저장된 데이터를 잘 이용해서 시장 및 고객을 분석

백엔드 개발자 또는 데이터베이스 관리자:

- 데이터가 빠르고 안정적으로, 조회 및 저장될 수 있도록 개발 및 관리

특히 백엔드 개발자 또는 데이터베이스 관리자의 입장에서는 DBMS가 성능 저하 없이 효율적으로 작업을 처리하고 있는지를 체크하는 것이 중요함.

MySQL에서는 이러한 정보를 확인할 수 있는 기본 데이터베이스 중 하나가 **sys**

  </details>
</details>

<details>
  <summary>2) 테이블 생성하기</summary>

# CSV 파일로 테이블 생성하기

MySQL에서는 Table Data Import Wizard를 통해서 CSV(Comma Separated Values) 형식의 파일을 테이블로 불러들일 수 있다.

MySQL에서 각 행의 데이터 타입을 뜻하는 Field Type(Data Type) 에는 int(정수), text(문자열), double(실수) 등이 있다.

# 생성된 테이블 살펴보기

MySQL에서 테이블 오른쪽 스패너 버튼을 클릭하면 테이블 정보를 살펴볼 수 있다.

column의 이름과 데이터 타입을 알 수 있다.

각 column의 이름과 데이터 타입을 함께 고려하면 각 column에 어떤 값들이 들어가 있는지 쉽게 예상할 수 있다

# Primary Key 설정하기

## Primary Key(기본 키)

테이블에서 하나의 row를 고유하게 식별할 수 있게 해주는 column

Primary Key에 해당하는 column 옆에 있는 PK의 체크박스를 체크해주면 column 왼쪽에 있는 아이콘이 열쇠 모양으로 바뀐다.

바뀐 PK 설정을 적용하려면 우측 하단의 apply 버튼을 눌러야 한다. 그러면 Pimary Key를 변경하는 SQL문이 나오며, 다시 한 번 apply 버튼을 누르면 적용된다.

# Primary Key의 종류

Primary Key는 테이블에서 특정 row 하나를 식별하는 역할을 한다.

특정 컬럼을 Primary Key로 설정하면 Primary Key에 같은 값이 있는 row가 추가되는 것을 DBMS가 자동으로 박아주기 때문에 중복된 row가 생길 위험성이 사라진다.

이러한 Primary Key의 종류에는 크게 두 가지가 있다.

## Natural Key

실제로 어떤 개체가 갖고 있는 속성을 나타내는 칼럼이 Primary Key가 됐을 때 이를 Natural Key라고 한다. 예) 주민등록번호

## Surrogate Key

어떤 개체의 속성을 직접적으로 나타내는 컬럼이 아닌, Primary Key로 쓰이기 위해 위적으로 생성된 컬럼

주로 1부터 순차적으로 증가하는 숫자가 들어가게 됨

각 상황마다 적절한 키가 달라진다.

Natural Key는 그 값이 나중에 변경되면 모든 row의 값을 다시 수정해줘야 한다는 문제가 있기 때문에 보통은 Surrogate Key를 선택하는 경우가 더 많다.

# Not Null의 의미

MySQL에서 특정 컬럼의 PK 체크박스에 체크를 할 때 그 컬럼의 NN 체크박스도 동시에 체크가 된다.

이때 NN 은 Not Null을 의미한다.

NULL이라는 것은 그 부분에 값이 없다는 것이다.

주의할 점은 NULL은 0과 다르며, 비어있는 문자열과도 다르다.

NN 체크박스에 체크가 되어있다는 뜻은, 이 컬럼에는 반드시 어떤 값이 들어있어야 한다는 것을 의미한다.

NN이 설정된 컬럼에 NULL이 들어가 있는 row를 추가하려고하면 데이터베이스에서 에러를 내버린다.

Primay Key인 컬럼은 특정 row를 식별하기 위한 컬럼이기 때문에 반드시 Not Null이어야 한다. 따라서 PK 체크박스를 체크할 때 NN 체크박스도 동시에 체크되도록 Workbench에서 자동으로 처리해준 것이다.

# Primary Key와 Auto Increment 속성

## AI (Automatic Inrecement)

Surrogate Key는 보통 1부터 시작해서 1씩 증가하는 정수값을 가진다.

그렇다면 매번 새롭게 추가되는 row의 Surrogate Key인 컬럼의 값은 row의 그것보다 1이 더 큰 정수가 되어야 한다. 대부분의 DBMS에는 매번 새로운 row가 될 때마다 해당 컬럼에 이전보다 1이 더 큰 정수를 자동으로 넣어주는 기능이 존재한다.

컬럼 옆에 있는 AI 체크박스에 체크를 해주고 apply 해주면 이러한 속성이 적용된다.

따라서 row를 삽입할 때 개체의 실제 속성을 나타내는 컬럼의 값만 직접 작성하고 Surrogate Key로 사용하는 컬럼에는 신경쓸 필요가 없다.

# 날짜 관련 컬럼은 DATE 타입으로

CSV 파일을 테이블로 불러올 때 날짜 관련 정보가 TEXT 타입으로 인식될 수 있는데, 이를 DATE 타입으로 바꿔주면 나중에 이 컬럼의 날짜 값을 가지고 1년 후의 날짜를 구하는 등의 작업들을 좀 더 편하게 할 수 있다.

</details>

<details>
  <summary>3) 데이터 조회로 기본 다지기</summary>
  <details>
    <summary></summary>
  </details>
</details>

<details>
  <summary>4) 데이터 분석 단계로 나아가기</summary>
  <details>
    <summary></summary>
  </details>
</details>

<details>
  <summary>5) 테이블 조인을 통한 깊이있는 데이터 분석</summary>
  <details>
    <summary></summary>
  </details>
</details>
