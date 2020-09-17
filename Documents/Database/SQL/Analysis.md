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
    <summary>데이터 조회</summary>

# 데이터 조회의 핵심, SELECT과 WHERE

## 데이터 조회 기본 예시

`SELECT 컬럼명 FROM [DB명.]테이블명;`

`SELECT * FROM [practice_main.]member;`

- practice_main 데이터베이스에 있는 member 테이블에서 모든(\*) 컬럼을 가져와라

`SELECT age, gender FROM member;`

- member 테이블에서 age와 gender 컬럼을 가져와라

`SELECT * FROM member WHERE age > 20;`

- member 테이블에서 age 컬럼의 값이 20보다 큰 개체들의 모든 컬럼을 가져와라

# SQL 작성 형식

## 1. SQL 문 끝에는 항상 세미콜론(;)을 써줘야 한다

하나의 SQL 문 끝에는 세미콜론을 써줘야 한다.

SQL 문법 상 세미콜론이 **하나의 SQL 문을 종결하는 단위**이기 때문이다

## 2. SQL 문 안에는 공백이나 개행 등을 자유롭게 넣을 수 있다

`SELECT * FROM practice_main.member WHERE age > 20`

- 이런 식으로 엄청 많은 공백을 주거나,

```sql
SELECT * FROM practice_main.member
	WHERE age > 20
```

- 이런 식으로 SQL 문의 일부분을 한 줄 내리고, 탭을 입력한 후에 쓰는 것도 가능

어떤 방식으로 쓰든, 구분되어야 할 키워드들이 최소한 하나 이상의 공백으로 구분되어 있고, 세미콜론으로 마무리되어 있으면 실행에는 문제가 없다.

이런 점을 이용해서 길이가 긴 SQL 문을 쓸 때는 개행(줄바꿈), 탭 등을 적절하게 활용해서 가독성을 높이는 것이 좋다.

## 3. SQL 문의 대소문자 구분 문자

`SELECT * FROM practice_main.member WHERE age > 20`

위를 보면 MySQL에 기본으로 내장된 키워드들(보통 '예약어' 라 함)은 대문자로 써주고, 나머지 부분은 소문자로 써줬다.

**MySQL의 예약어는 대문자로 적는 것이 관례**이고, 보기에도 좋다.

데이터베이스 이름, 테이블 이름, 컬럼 이름 등은 대소문자를 가리지 않고, 실제로 존재하는 것의 이름을 적어주면 된다.

데이터베이스, 테이블, 컬럼 등의 이름을 짓는 것도 회사마다 일종의 컨벤션들이 있을텐데, 실무에서는 그런 컨벤션에 맞게 지어진 이름들을 작성하게 될 것

예약어들을 소문자로 쓴다고 실행이 안 되는 것은 아니다. 다만, 가독성을 위해 예약어만큼은 꼭 대문자로 쓰는 습관을 들이자.

## 4. 데이터베이스 이름과 테이블 이름

`practice_main.member`과 같이 데이터베이스 이름 뒤에 온점(.)을 붙이고 그 다음에 테이블 이름을 적어줬다. 이렇게 쓰면 해당 데이터베이스 안의 테이블을 가리키는 것인데, 서로 다른 데이터베이스에 같은 이름의 테이블이 존재할 수 있기 때문에 이렇게 써주는 게 좋다.

하지만 항상 이렇게 쓸 필요는 없다.

GUI에서 해당 데이터베이스를 클릭해서 활성화해두거나, 아예 SQL문으로 어떤 데이터베이스를 쓰겠다고 확실하게 정하는 것도 가능하다.

```sql
USE practice_main;
SELECT * FROM member
```

`USE practice_main;`은 practice_main 이라는 데이터베이스를 사용하겠다고 확실히 선언하는 것이다. 그리고 그 뒤로는 그냥 테이블 이름만 써도 괜찮다.

# 조건을 나타내는 다양한 방법

## DATA TYPE = INT

나이가 27 이상

- `SELECT * FROM member WHERE age >=27;`

나이가 30이상 39이하 (30대)

- `SELECT * FROM member WHERE age BETWEEN 30 AND 39;`

나이가 30대가 아닌

- `SELECT * FROM member WHERE age NOT BETWEEN 30 AND 39;`

## DATA TYPE = DATE

가입일이 2019년 1월 1일 이후

- `SELECT * FROM member WHERE sign_up_day > '2019-01-01';`

가입일이 2018년

```sql
SELECT * FROM member
	WHERE sign_up_dat BETWEEN '2018-01-01' AND '2018-12-31';
```

# 문자열 패턴 매칭 조건

## **주소가 서울인 회원**

- `SELECT * FROM member WHERE address LIKE '서울%';`

LIKE는 특정 컬럼 값의 패턴이 '서울%'처럼 생긴 것만 조회

%는 임의의 문자열 길이를 뜻함(0도 포함). 즉, 위의 표현식은 서울로 시작하는 모든 문자열을 뜻함

## 주소가 고양시인 회원

- `SELECT * FROM member WHERE address LIKE '%고양시%';`

고양시 라는 단어 앞 뒤로 임의의 길이를 가진 문자열이 있는 문자열을 뜻함

쉽게 말해, 고양시 가 들어간 모든 문자열을 나타냄

# 그 밖의 알아야 할 표현식

## 1. 같지 않음 (!=, <>)

남자가 '아닌' 회원 조회

- `SELECT * FROM member WHERE gender != 'm';`
- `SELECT * FROM member WHERE gender <> 'm';`

## 2. 이 중에 있는 ~ (IN)

나이가 딱 20살, 또는 30살인 회원들만 조회

- `SELECT * FROM member WHERE age IN (20, 30);`

## 3. 한 글자를 나타내는 \_

LIKE 뒤의 언더바 하나는 문자 하나를 나타낸다.

이메일 주소가 c로 시작하고, 그 뒤에 다섯 글자가 더 있는 row들 조회

- `SELECT * FROM member WHERE email LIKE 'c_____@%';`

# DATE 데이터 타입 관련 함수

## 1. 연도, 월, 일 추출하기

### (1) 1992년에 태어난 회원들만 조회하기

`SELECT * FROM member WHERE YEAR(birthday) = '1992';`

**YEAR 함수**를 사용하면 날짜 값에서 연도만 뽑아낼 수 있음

### (2) 여름(6, 7, 8월)에 가입한 회원들만 조회하기

`SELECT * FROM member WHERE MONTH(sign_up_day) IN (6, 7, 8);`

**MONTH 함수**를 사용하면 날짜값에서 월만 뽑아낼 수 있음.

### (3) 각 달의 후반부(15~31일)에 가입했던 회원들만 조회하기

`SELECT * FROM member WHERE DAYOFMONTH(sign_up_day) BETWEEN 15 AND 31;`

**DAYOFMONTH 함수**는 날짜값에서 일만 뽑아낼 수 있음.

## 2. 날짜 간의 차이 구하기

### 특정 날짜 기준

`DATEDIFF(날짜 a, 날짜 b)` 를 사용하면 '날짜 a - 날짜 b'를 해서 그 차이 일수를 알려준다.

member 테이블에서 각 회원이 가입한 일자가 2019년 1월 1일을 기준으로 며칠 뒤인지를 알아보자.

`SELECT email, sign_up_day, DATEDIFF(sign_up_day, '2019-01-01') FROM member;`

이렇게 하면 이메일 컬럼, 가입일 컬럼, 그리고 가입일에서 2019년 1월 1일을 뺀 컬럼, 이렇게 세 가지 컬럼을 조회할 수 있다.

이처럼 꼭 테이블에 있던 컬럼이 아니더라도 조회할 때는 이런 식으로 새로운 컬럼을 붙여서 볼 수도 있다.

### 오늘 날짜 기준

`DATEDIFF`와 `CURDATE()` 함수 사용

`SELECT email, sign_up_day, CURDATE(), DATEDIFF(sign_up_day, CURDATE()) FROM member;`

- 세번째 컬럼으로 오늘의 날짜를, 그리고 네번째 컬럼으로 '가입일 - 오늘의 날짜'를 볼 수 있다.

### 가입 시점의 나이

`SELECT email, sign_up_day, DATEDIFF(sign_up_day, birthday) / 365 FROM member;`

'가입일 - 생일' 값을 365로 나눠주면 가입 시기의 나이를 알 수 있다.

## 3. 날짜 더하기 빼기

더하기: `DATE_ADD()`

뺴기: `DATE_SUB()`

`DATE_ADD(sign_up_day, INTERVAL 300 DAY)`

- 가입일로부터 300일 지난 날

`DATE_SUB(sign_up_day, INTERVAL 250 DAY)`

- 가입일로부터 250일 전 날짜

## 4. UNIX Timestamp 값

날짜뿐만 아니라 시간까지 포함하는 칼럼은 DATETIME이라는 데이터 타입을 사용한다.

DATETIME 타입의 칼럼에는 보통 '2018-12-31 23:54:59' 이런 식으로 값들이 저장되어 있다.

그런데 어떤 테이블에는 날짜와 시간이 이렇게 예쁜 형식이 아니라, 1553526000 이런 식으로 큰 숫자값이 적혀있는 경우들이 많다. 이런 형식의 날짜시간 값을 **UNIX Timestamp**라고 한다.

UNIX Timestamp는 특정 날짜의 특정 시간을 **1970년 1월 1일을 기준으로, 총 몇 초가 지났는지**로 나타낸 값이다.

`UNIX_TIMESTAMP()` : DATE 타입의 값을 Unix Timestamp로 바꿔주는 함수

`FROM_UNIXTIME()` : Unix Timestamp 값을 사람이 읽을 수 있는 날짜 형태로 바꿔주는 함수

# 여러 개의 조건 달기

## AND

남자이면서 주소가 서울이고, 25세 이상 29세 이하인 회원 조회

```sql
SELECT * FROM member
WHERE gender = 'm'
	AND address LIKE '서울%'
	AND age BETWEEN 25 AND 29;
```

## OR

봄(3~5월) 또는 가을(9~11월)에 가입한 회원 조회

```sql
SELECT * FROM member
WHERE MONTH(sign_up_day) BETWEEN 3 AND 5
	OR MONTH(sign_up_day) BETWEEN 9 AND 11;
```

## AND, OR 혼합

키가 180 이상인 남자 혹은 키가 170 이상인 여자

```sql
SELECT * FROM member
WHERE (gender = 'm' AND height >= 180)
	OR (gender = 'f' AND height >= 170);
```

이렇게 AND 와 OR를 함께 사용할 때에는 먼저 실행해야 되는 부분을 괄호로 감싸주는 게 좋다.

# 여러 조건을 걸 때 주의할 점

## 1. OR를 사용할 때 주의사항

`SELECT * FROM member WHERE id = 1 OR id =2;`

이렇게 적는 게 맞는 표현인데, 간혹 아래와 같이 잘못 적는 경우가 있다.

- `SELECT * FROM member WHERE id = 1 or 2;`

실수로 쓴 `WHERE id = 1 or 2` 이 부분은

1. id = 2 가 TRUE
2. 2

이 두 부분을 나눌 수 있는데, 두 번째 부분이 문제가 된다.

MySQL에서는 0을 False, 0 이외의 숫자는 모두 True로 간주한다.

따라서 두 번째 부분은 항상 True가 되어버린다.

즉, `WHERE id = 1 OR 2`는 곧 `WHERE id = 1 OR TRUE` 와 같은 뜻인데, 이렇게 되면 결국 어떤 row든 다 이 조건을 만족하게 되어버림. 그래서 모든 row가 출력됨

## 2. AND와 OR 간의 우선순위

(1) 성별이 여자이거나 (OR) 나이가 30세 미만

'이면서' (AND)

(2) 키는 180 이상인

회원을 조회하려고 한다.

```sql
SELECT * FROM memeber
WHERE gender = ='f' OR age < 30 AND height > 180;
```

이렇게 조회하면 height 컬럼의 값이 180 이하인 회원들도 많이 보인다.

그 이유는 SQL 문이 실행될 때, AND가 OR보다 우선순위가 더 높기 때문이다.

즉, AND가 OR 보다 먼저 실행된다는 것.

그래서

(1) 성별이 여자이거나(OR)

(2) 나이가 30세 미만이면서(AND) 키가 180 이상인

회원을 조회하게 되는 것

따라서 사용자가 '먼저 실행되기를 원하는 조건'을 괄호로 씌워주는 것이 좋다. 그 이유는 괄호는 AND보다도 우선순위가 높기 때문이다.

원래 의도했던 결과를 얻기 위해서는 아래와 같이 작성하면 된다.

```sql
SELECT * FROM member
WHERE (gender = 'f' OR age < 30) AND height > 180;
```

이처럼 먼저 실행되기 원하는 부분에 괄호를 씌워주면 된다.

이렇게 **조건에 괄호를 씌워주면** AND와 OR 사이의 우선순위를 신경쓰지 않아도 되고, 나중에 SQL 문을 다시 읽었을 때도 이해하기 편하다는 장점이 있다.

조건 단위로 괄호를 씌워주는 습관을 들이면 좋다!

# 문자열 패턴 매칭 조건을 사용할 때 주의할 점

## 1. 이스케이핑(escaping) 문제

문자열 컬럼에 퍼센트 기호(%)가 포함된 row를 찾아야 되는 경우

`LIKE '%%%'` 이렇게 적어주게 되면 임의의 길이를 가진 문자열로 해석되어 모든 문자열이 다 포함된다.

LIKE에서 쓰이는 표현식이 아니라, 문자로서의 %를 나타내려면

`LIKE '%\%%'` 와 같이 표현해주어야 한다.

% 앞에 역슬래쉬(백슬래쉬, backslash) 기호를 붙여줬다.

원래 특정 의미('임의의 길이를 가진 문자열')를 나타내던 문자(%)를 그 특정 의미가 아니라, 일반적인 문자처럼 취급하는 행위를 **이스케이핑(escaping)**이라고 한다.

**어떤 문자가 그것에 부여된 특정한 의미, 기능으로 해석되는 게 아니라 그냥 단순한 문자 하나로 해석되도록 하는 것**을 이스케이핑 이라고 하는 것.

MySQL에서 이스케이핑을 하는 방법은 해당 문자 앞에 역슬래쉬를 붙여주는 것이다.

### (1) ' (작은 따옴표) 이스케이핑

`LIKE '%\'%'`

### (2) \_(언더바) 이스케이핑

`LIKE '%\_%'`

### (3) "(큰 따옴표) 이스케이핑

`LIKE '%\"%'`

## 2. 대소문자 구분 문제

소문자 g가 포함된 문자열을 조회하고 싶다

`LIKE '%g%'` 이렇게 사용할 경우 대문자 G가 포함되어 있는 row 도 조회된다.

이는 MySQL의 기본 설정 때문임.

MySQL에서 테이블에 적용된 설정 중 Info 에서 **Table collectoin** 항목을 보면, 문자열이 서로 동일한지를 비교할 때 적용되는 설정을 나타낸다. **utf8mb4_0900_ai_ci**라는 값이 써 있다. 여기서 **ci**는 **case-insensitive**의 약자로, 문자열이 동일한지 확인할 때 대소문자를 구별하지 않겠다는 뜻임

만약 이 설정을 다른 걸로 변경하면 대소문자 구분을 하도록 바꿀 수도 있겠지만, 데이터베이스 관리자가 아니라면 MySQL 설정을 마음대로 바꿔서는 안되고, 애초에 그럴 수 있는 권한도 없을 것이다.

따라서 어떤 설정에서든 대소문자 구분을 할 수 있는 방법이 필요하다.

`LIKE BINARY '%g%'` 와 같이 문자열 패턴 앞에 BINARY를 붙이면 된다.

BINARY를 붙여준다는 것은 해당 문자열의 0과 1의 조합의 값이 정확히 일치하는 것을 찾으라는 뜻임.

소문자g와 대문자 G는 같은 알파벳이기는 하지만 컴퓨터에서 0과 1의 조합으로 저장될 때 다른 값으로 저장된다. 그리고 BINARY를 붙이는 건 단지 알파벳 비교 뿐만 아니라 대소문자 구분까지 할 수 있도록 0과 1을 보는 수준까지 문자열 비교를 수행하라는 뜻임

  </details>
  <details>
    <summary>데이터 정렬</summary>

# 데이터 정렬해서 보기

## SQL 에서 정렬

'row들을', '특정 컬럼을 기준으로', '순서대로 출력'

키를 기준으로 정렬

```sql
SELECT * FROM member
ORDER BY height ASC;
```

- 오름차순으로 정렬됨.
- ASC - ascending. 안 적어주어도 기본적으로 오름차순으로 정렬된다.
- 안 적어두면 햇갈릴 수 있으니, 적어두는 게 좋다.

```sql
SELECT * FROM member
ORDER BY height DESC;
```

- 내림차순으로 정렬됨
- DESC - descending

몸무게가 70 이상인 남자 회원을 키 오름차순으로 정렬

```sql
SELECT * FROM member
WHERE gender = 'm'
	AND weight >= 70
ORDER BY height ASC;
```

- SQL 문법 상 WHERE 는 ORDER BY 보다 앞에 와야 한다.

## 여러 기준으로 정렬

ORDER BY 는 이름을 먼저 쓴 컬럼을 우선으로 해서 정렬이 차례대로 수행된다.

가입 년도를 기준으로 내림 차순으로 정렬하고, 같은 년도에 가입한 회원들은 이메일을 기준으로 오름차순 정렬

```sql
SELECT * FROM member
ORDER BY YEAR(sign_up_day) DESC, email ASC;
```

# 정렬할 때 주의할 점

정렬 기준의 데이터 타입이 (1) 숫자형(INT 등)인 경우와, (2) 문자열형(TEXT 등)인지에 다라 결과가 달라진다.

INT 타입의 값은 숫자의 대소(크고 작음)를 기준으로 정렬이 수행되지만,

TEXT 타입의 값은 한 문자, 한 문자씩 그 문자 순서를 비교해서 정렬이 수행된다.

따라서, **숫자값이 담긴 컬럼을 정렬 기준으로 할 때는 그 컬럼의 데이터 타입이 숫자형인지, 문자열형인지를 잘 살펴봐야 한다.**

## CAST

이미 TEXT 타입인 컬럼에 있는 숫자값들을 그냥 INT 등의 숫자형 타입으로 보고 정렬할 수도 있다. 정렬할 때 그 컬럼의 값의 데이터 타입을 일시적으로 변경해 주면 된다.

`CAST` 함수를 사용하면 되는데, 보통 프로그램이 세계에서 어떤 변수의 데이터 타입을 바꿀 때 사용되는 단어이다.

`CAST(data AS signed)` data 컬럼에 존재하는 값들의 데이터 타입을 일시적으로 **signed**라는 데이터 타입으로 변환하라는 뜻임

singed는 양수와 음수를 포함한 모든 정수를 나타낼 수 있는 데이터 타입이다.

만약 값에 소수점이 포함되어 있다면, `CAST(data AS decimal)` 과 같이 사용 가능

# 데이터 일부만 추려보기

`LIMIT` 사용

최근에 가입한 회원 10명 조회

```sql
SELECT * FROM member
ORDER BY sign_up_day DESC
LIMIT 10;
```

최근에 가입한 9번째, 10번째 회원 조회

```sql
SELECT * FROM member
ORDER BY sign_up_day DESC
LIMIT 8, 2 # 인덱스가 8인 개체부터 2개 (인덱스는 0부터 시작)
```

# LIMIT과 Pagination

웹사이트들을 보면 사이트 화면 하단에 1, 2, 3, 4, 5 등 페이지를 클릭할 수 있는 버튼을 흔히 볼 수 있음

- 1페이지: 1~10번까지의 내용
- 2페이지: 11~20번까지의 내용
- 3페이지: 21~30번까지의 내용

보통 위와 같이 구성되어 있는데, 새로운 페이지를 누르면 그때마다 10개의 새로운 내용들을 로드(load) 하게 된다.

이런 걸 **페이지네이션(Pagination)**이라고 한다. 전체 결과를 한 번에 로드하는 게 아니라, 이렇게 페이지 단위로 쪼개서 그때그때 요청이 있을 때마다 부분 결과를 조금씩 로드하는 방식을 말한다.

꼭 숫자 클릭 방식이 아니라 하더라도, 스크롤을 내리면 잠시 뒤에 새로운 내용이 더 등장하는 방식도 비슷하다.

Pagination은 개발자에게도 중요한 주제이다. 실제로는 각 페이지 당 내용을 최대한 빠르게 로드하기 위한 추가적인 기법들이 필요하다.

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
