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
    <summary>데이터의 특성 구하기 & NULL을 다루는 방법</summary>

# 데이터의 특성 구하기

## 집계함수

`COUNT(컬럼이름)`

- 컬럼에 해당하는 NULL이 아닌 row의 수
- `SELECT COUNT(weight) FROM member;`

`COUNT(*)`

- NULL에 상관없이, 모든 row의 수

`MAX(컬럼이름)`

- 컬럼 최댓값

`MIN(컬럼이름)`

- 컬럼 최솟값

`AVG(컬럼이름)`

- 컬럼 평균값 (NULL 제외)

`SUM(컬럼이름)`

- 컬럼 합계

`STD(컬럼이름)`

- 컬럼 표준편차

## 산술 함수 (Mathematical Function)

SQL에는 집계 함수 말고도, 단순한 산술 연산을 해주는 산술 함수가 있다.

`ABS`

- 절대값

`SQRT`

- 제곱근

`CEIL`

- 올림

`FLOOR`

- 내림

`ROUND`

- 반올림

## 집계 함수와 산술 함수의 차이점

(1) 집계 함수는 특정 컬럼의 여러 row의 값들을 동시에 고려해서 실행되는 함수

(2) 산술 함수는 특정 컬럼의 각 row 값마다 실행되는 함수

# NULL을 다루는 방법

데이터를 분석하는 사람 입장에서는 NULL이 달갑지 않은 존재임. 모든 row와 모든 column에 제대로 된 값이 들어가 있어야 NULL을 따로 처리해주지 않아도 되어서 편리하기 때문. 하지만 현실에서는 데이터에 NULL이 있는 경우가 종종 있음.

## NULL 조회

`SELECT * FROM member WHERE address IS NULL;`

## NULL을 제외하고 조회

`SELECT * FROM member WHERE height IS NOT NULL;`

## NULL을 좀 더 일반적인 단어로 바꿔주기

다른 직군의 사람들은 NULL을 잘 모를 수도 있기 때문에 조금 더 일반적인 단어로 바꿔줄 수 있다.

```sql
SELECT
	COALESCE(height, '####'),
	COALESCE(weight, '----'),
	COALESCE(address, '@@@@')
FROM member;
```

`COALESCE`는 값이 있으면 그 값을 그대로 리턴해 주고, NULL이 있으면 뒤에 파라미터로 넘긴 문자를 리턴해 준다.

# NULL에 관해 알아야 하는 사실

## 1. IS NULL 과 = NULL 은 다르다

**NULL은 어떤 값이 아니기 때문에 애초에 등호(=)를 사용해서 어떤 값과 비교할 수 있는 대상이 아님.**

그래서 IS NULL 이라는 키워드가 별도로 마련된 것.

NULL인지를 확인할 때는 = NULL을 쓰면 안 되고, 반드시 IS NULL을 써야 한다.

마찬가지로, != NULL 이나 <> NULL 도 쓸 수 없고, **IS NOT NULL**이라고 나타내야 한다.

## 2. NULL에는 어떤 연산을 해도 결국 NULL이다.

NULL에는 뭘 더하든, 빼든, 곱하든, 나누든지 간에 항상 NULL이다.

# 이상한 값 제외하는 법

경우에 따라서 이상한 값을 제외하는 방법은 다를 수 있는데, 여러 조건문을 잘 활용하면 된다.

## 나이 범위가 이상한 경우

`SELECT AVG(age) FROM member WHERE age BETWEEN 5 AND 100;`

과 같이 특정 범위의 나이만 포함시킬 수 있다.

## 주소가 이상한 경우

`SELECT * FROM member WHERE address NOT LIKE '%호';`

로 주소 확인 후, 해당하는 회원들에게 주소를 다시 제대로 입력해달라는 메일을 보낼 수도 있겠다.

  </details>
  <details>
    <summary>컬럼 다루기</summary>

# 컬럼끼리 계산하기

## BMI 구하기

BMI = Body Mass Index = 몸무게(kg) / 키(m) ^(2)

```sql
SELECT email, height, weight, weight / ((height / 100) * (height / 100))
FROM member;
```

참고: NULL이 포함된 계산식의 결과는 항상 NULL이다.

# 컬럼에 alias 붙이기

## Alias

Alias = 별명, 별칭

```sql
SELECT
	email,
	height AS 키,
	weight AS 몸무게,
	weight / ((height / 100) * (height / 100)) AS BMI
FROM member;
```

AS를 사용하지 않고 컬럼 뒤에 스페이스바로 한 칸 뛰고 alias를 적어주어도 되지만, 알아보기 쉽게 AS를 써주자

## CONCAT

`CONCAT` 함수를 이용해 여러 컬럼의 값을 한 컬럼에 나타내줄 수 있다.

```sql
SELECT
	email,
	CONCAT(height, 'cm', ', ', weight, 'kg') AS '키와 몸무게',
	weight / ((height / 100) * (height / 100)) AS BMI
FROM member;
```

# 컬럼의 값 변환해서 보기

## CASE 문 활용해서 비만여부 체크하기

25 ≤ BMI: 과체중 또는 비만

18.5 ≤ BMI < 25 : 정상

BMI < 18.5 : 저체중

```sql
SELECT
	email,
	CONCAT(height, 'cm', ', ', weight, 'kg') AS '키와 몸무게',
	weight / ((height / 100) * (height / 100)) AS BMI,

(CASE
	WHEN weight IS NULL OR height IS NULL THEN '비만 여부 알 수 없음'
	WHEN weight / ((height / 100) * (height / 100)) >= 25 THEN '과체중 또는 비만'
	WHEN weight / ((height / 100) * (height / 100)) >= 18.5
		AND weight / ((height / 100) * (height / 100)) < 25
		THEN '정상'
	ELSE '저체중'
END) AS obesity_check

FROM member
ORDER BY obesity_check ASC;
```

# CASE 함수의 종류

## 1. 단순 CASE 함수

```sql
CASE 컬럼 이름
	WHEN 값 THEN 값
	WHEN 값 THEN 값
	WHEN 값 THEN 값
	ELSE 값
END
```

예시

```sql
SELECT email,
CASE age
	WHEN 29 THEN '스물 아홉 살'
	WHEN 30 THEN '서른 살'
	ELSE age
END
FROM member;
```

age 컬럼의 값이 29면 '스물 아홉 살', 30이면 '서른 살' 이라고 표현.

그리고 CASE 함수 중에서 ELSE age는 나머지 경우에는 모두 age 컬럼에 있던 값을 그대로 보여달라는 뜻임

이렇게 CASE문 바로 뒤에 컬럼 이름을 쓰고, 그 컬럼의 값과 어떤 값이 같은지(=)를 비교하는 CASE 함수를 **단순 CASE 함수**라고 한다.

## 2. 검색 CASE 함수

```sql
CASE
	WHEN 조건1 THEN 값
	WHEN 조건2 THEN 값
	WHEN 조건3 THEN 값
	ELSE 값
END
```

이런 CASE 함수에서는 일단 TRUE인 조건을 만나게 되면 거기에 있는 THEN 뒤의 값을 돌려주고, CASE 함수는 종료된다.

검색 CASE 함수는 단순 CASE 함수와 어떤 점이 다를까?

일반적으로 단순 CASE 함수에서는 등호 연산(=) 밖에 할 수 없다는 단점이 있다.

하지만 검색 CASE 함수에서는 사용자가 직접 원하는 대로 조건을 설정할 수 있기 때문에 좀 더 다양한 조건을 걸 수 있다.

# NULL을 다른 값으로 변환하는 다양한 함수

## 1. COALESCE 함수

COALESCE 함수는 괄호 속 인자 중에서 가장 첫번째로 NULL이 아닌 값을 반환한다.

`SELECT COALESCE(height, 'N/A') FROM member;`

- height 컬럼의 NULL들을 'N/A'라는 문자열로 교체했는데, 이는 Not Available, Not Applicable의 줄임말로 테이블에서 어떤 값이 없거나 표현할 수 없는 값일 때를 나타내는 단어임.

`SELECT COALESCE(height, weight * 2.3, 'N/A') FROM member;`

- 이번에는 COALESCE 함수 안에 weight \* 2.3 이라는 식이 추가됨
- 사람의 키가 보통 몸무게에 2.3을 곱한 값이라고 가정한 것. 만약 height 컬럼이 NULL이면 해당 row의 weight 컬럼의 값을 가지고 키를 추론해본 것임
- height 컬럼도 NULL이고 weight 컬럼도 NULL인 row라면 'N/A'가 출력될 것임

## 2. IFNULL 함수

IFNULL 함수는 첫 번째 인자가 NULL인 경우에는 두 번째 인자를 표시하고, NULL이 아니면 해당 값을 그대로 표현한다.

`SELECT IFNULL(height, 'N/A') FROM member;`

## 3. IF 함수

IF 함수는 가장 첫 번째 인자로 어떤 조건식이 온다. 만약 그 조건식의 결과가 True라면 두 번째 인자를 리턴하고, False라면 세 번째 인자를 리턴한다.

`SELECT IF(height IS NOT NULL, height, 'N/A') FROM member;`

## 4. CASE 함수

```sql
SELECT
	CASE
		WHEN height IS NOT NULL THEN height
		ELSE 'N/A'
	END
FROM member;
```

# alias를 붙이고 바로 쓸 수 없는 이유

## 1. 띄어쓰기(스페이스)가 포함된 alias에는 따옴표를 붙여줘야 한다.

만약 컬럼에 스페이스가 포함된 alias를 붙이고 싶다면, 작은 따옴표나 큰 따옴표를 붙여서 alias 부분을 확실하게 표현해주어야 한다.

`SELECT name AS '상품 이름', price FROM item;`

이렇게 하지 않으면 스페이스를 기준으로 구문 해석이 이루어지는 SQL 특성 상 에러가 발생하니까 주의해야 한다.

## 2. SELECT 절에서 설정한 alias를 바로 사용할 수 없는 문제

```sql
SELECT
	email,
	CONCAT(height, 'cm', ', ', weight, 'kg') AS '키와 몸무게',
	weight / ((height / 100) * (height / 100)) AS BMI,

(CASE
	WHEN weight IS NULL OR height IS NULL THEN '비만 여부 알 수 없음'
	WHEN weight / ((height / 100) * (height / 100)) >= 25 THEN '과체중 또는 비만'
	WHEN weight / ((height / 100) * (height / 100)) >= 18.5
		AND weight / ((height / 100) * (height / 100)) < 25
		THEN '정상'
	ELSE '저체중'
END) AS obesity_check

FROM member
ORDER BY obesity_check ASC;
```

우리는 위와 같이 Alias와 CASE 문을 사용한 적이 있다.

그런데 우리는 BMI라는 Alias를 이미 붙였기에 ,CASE 문 안에서 반복되는 부분을 BMI로 표시해서 작성하려고 할 수 있다

하지만 이 경우 오류가 난다.

```sql
SELECT
	email,
	CONCAT(height, 'cm', ', ', weight, 'kg') AS '키와 몸무게',
	weight / ((height / 100) * (height / 100)) AS BMI,

(CASE
	WHEN weight IS NULL OR height IS NULL THEN '비만 여부 알 수 없음'
	WHEN BMI >= 25 THEN '과체중 또는 비만'
	WHEN BMI >= 18.5
		AND BMI < 25
		THEN '정상'
	ELSE '저체중'
END) AS obesity_check

FROM member
ORDER BY obesity_check ASC;
```

실행 결과창을 보면 BMI 라는 컬럼이 Unknown이라고 뜬다.

왜 이 부분이 작동하지 않는 걸까? SQL 문의 실행원리에 대해 잘 알아야 이해할 수 있다.

BMI는 우리가 SELECT 절 안에서 설정한 alias이다. 그런데 BMI 컬럼이 Unknown 이라고 뜨는 건 CASE 함수가 실행될 때는 BMI 라는 alias가 아직 인식되지 않은 상태라고 봐야 한다.

하지만 CASE 문에서 매번 이렇게 똑같은, 그리고 긴 표현을 쓰는 건 보기에 안 좋을 것 같다.

해결 방법이 있는데, 이는 다른 챕터들을 좀 더 배운 뒤 알아보도록 하자.

  </details>
  <details>
    <summary>고유한 값 & 문자열 함수</summary>

# 고유한 값만 보기

## DISTINCT

`DISTINCT` 함수를 이용하면 하나의 컬럼에서 어떤 고유한 값들이 존재하는지 한 눈에 볼 수 있다.

`SELECT DISTINCT(gender) FROM member;`

- 성별 고유한 값만 보기 ('m', 'f')

`SELECT DISTINCT(SUBSTRING(address, 1, 2)) FROM member;`

- SUBSTRING 함수를 이용해 address 컬럼에서 첫번째 문자열부터 2개의 문자를 추출함
- 서울, 경기 등과 같은 문자가 추출되고 DISTINCT를 통해서 고유한 값만 리턴된다.

# 고유한 값의 개수 구하기

## COUNT

`SELECT COUNT(DISTINCT(gender)) FROM member;`

- gender 컬럼에 존재하는 고유한 값의 개수를 구해준다.

`SELECT COUNT(DISTINCT(SUBSTRING(address, 1, 2)) AS region_count FROM member;`

- 회원들이 사는 주요 지역의 고유한 값 개수를 구해준다. (개수를 구하기 전에 이상한 값의 유무에 주의하자)

# 문자열 관련 함수들

## 1. LENGTH 함수

`LENGTH` 함수는 문자열의 길이를 구해준다.

`SELECT *, LENGTH(address) FROM member;`

## 2. UPPER, LOWER 함수

`UPPER`는 문자열을 모두 대문자로 바꿔서 보여주는 함수고,

- `SELECT email, UPPER(email) FROM member;`

`LOWER`는 문자열을 모두 소문자로 바꿔서 보여주는 함수다.

- `SELECT email, LOWER(email) FROM member;`

## 3. LPAD, RPAD 함수

문자열의 왼쪽 또는 오른쪽을 특정 문자열로 채워주는 함수이다.

LPAD는 LEFT + PADDING(채우기)의 줄임말, RPAD 는 RIGHT + PADDING의 줄임말

예를 들어 `LPAD(age, 10, '0')`는 age 컬럼의 값을 왼쪽에 문자 0을 붙여서 총 10자리로 만드는 함수임. 보통 어떤 숫자의 자릿수를 맞출 때 자주 사용하는 함수.

그런데 age 컬럼의 데이터 타입은 숫자를 나타내는 INT 형이었다.

비록 숫자이더라도 문자열 함수 안에 인자로 넣어주면 그 값이 자동으로 문자열로 형 변환되어 계산된다.

## 4. TRIM, LTRIM, RTRIM 함수

이 함수들은 문자열에 존재하는 공백을 제거하는 함수들이다.

LTRIM: 왼쪽 공백 삭제

RTRIM: 오른쪽 공백 삭제

TRIM: 왼쪽, 오른쪽 양쪽 다 공백 삭제

이 함수들이 문자열 내부(중간)에 존재하는 공백을 없애는 건 아니라는 사실에 주의하자.

  </details>
  <details>
    <summary>그루핑</summary>

# 그루핑해서 보기 1

## GROUP BY 이용해서 그루핑(Grouping)하기

`SELECT gender, COUNT(*), AVG(height), MIN(weight) FROM member GROUP BY gender;`

각 그룹의 성별, 개체 수, 평균 키, 몸무게 최솟값 이 출력된다.

COUNT, AVG, MIN과 같은 집계함수는 그루핑을 통해 생성된 각 그룹의 수치적인 특성을 구해준다.

# GROUP BY를 안 썼을 때는?

그루핑은 SQL에서 데이터를 분석할 때 아주 중요한 개념이기 때문에 확실하게 이해하고 넘어가야 한다.

특히 GROUP BY를 써서 그루핑을 하고 난 후에, 생성된 각 그룹(하나의 row로 표현되었던)에 대해서 AVG, MIN 등의 집계 함수가 각각 동작한다는 것을 잘 기억해야 한다.

GROUP BY를 쓰지 않을 때는 테이블의 전체 row가 하나의 그룹이고, 이 하나의 그룹에 대해서 집계 함수가 작동한다.

# 그루핑해서 보기 2

## 회원들의 주소를 주요 지역을 기준으로 그루핑하기

```sql
SELECT
	SUBSTRING(address, 1, 2) as region,
	COUNT(*)
FROM member
GROUP BY SUBSTRING(address, 1, 2);
```

## 여러 개의 컬럼을 기준으로 그루핑하기

```sql
SELECT
	SUBSTRING(address, 1, 2) as region,
	gender,
	COUNT(*)
FROM member
GROUP BY
	SUBSTRING(address, 1, 2),
	gender;
```

그루핑 기준을 늘릴수록 더욱 세분화된 그루핑이 가능하다.

# 그루핑해서 보기 3

## HAVING

HAVING을 이용해서 특정 조건에 부합하는 회원만 조회해 보자. (서울 거주 남성)

```sql
SELECT
	SUBSTRING(address, 1, 2) as region,
	gender,
	COUNT(*)
FROM member
GROUP BY
	SUBSTRING(address, 1, 2),
	gender
HAVING
	region = '서울'
	AND gender = 'm';
```

이 때 WHERE을 사용하면 오류가 난다.

## WHERE와 HAVING

**WHERE**는 테이블에서 **맨 처음 row들을 조회할 때** 조건을 설정하기 위한 구문임

반면에 **HAVING**은 이미 조회된 row들을 다시 그루핑했을 때, **생성된 그룹들 중에서 다시 필터링**할 때 쓰는 구문임

# GROUP BY 를 쓸 때 지켜야 하는 규칙

## 예시

```sql
SELECT SUBSTRING(address, 1, 2) AS region, gender, COUNT(*) FROM member
GROUP BY SUBSTRING(address, 1, 2), gender
HAVING region IS NOT NULL
ORDER BY region ASC, gender DESC;
```

지금 (1) 주요 지역, (2) 성별의 조합을 기준으로 그루핑이 이루어졌다.

이렇게 GROUP BY를 사용할 때에는 중요한 규칙이 하나 있는데,

GROUP BY를 사용할 때는

**SELECT 절에는**

**(1) GROUP BY 뒤에서 사용한 컬럼들**

**또는 (2) COUNT, MAX 등과 같은 집계 함수만** 쓸 수 있다.

이건 거꾸로 말해 GROUP BY 뒤에 쓰지 않은 컬럼 이름을 SELECT 뒤에 쓸 수 없다는 말임

왜 그런 것일까?

그루핑을 하면 각 그룹에 대한 정보가 한 줄로 표시되는데

GROUP BY 뒤에 쓰지 않은, 즉 그루핑 기준으로 사용하지 않은 컬럼명을 SELECT 절 뒤에 써서 조회하려고 하면,

각 그룹의 row들 중에서 해당 컬럼의 값을 어느 row에서 가져와야할 지 결정할 수가 없다.

하지만 그루핑 기준으로 사용하지 않은 컬럼명도 집계함수의 인자로 사용하는 건 괜찮다.

# SELECT 문의 실행 순서

## 더 앞에 나와야 하는 순서

1. SELECT
2. FROM
3. WHERE
4. GROUP BY
5. HAVING
6. ORDER BY
7. LIMIT

## 각 절들이 해석 및 실행되는 순서

1. FROM: 어느 테이블을 대상으로 할 것인지를 먼저 결정한다.
2. WHERE: 해당 테이블에서 특정 조건(들)을 만족하는 row들만 선별한다.
3. GROUP BY: row들을 그루핑 기준대로 그루핑한다. 하나의 그룹은 하나의 row로 표현된다.
4. HAVING: 그루핑 작업 후 생성된 여러 그룹들 중에서, 특정 조건(들)을 만족하는 그룹들만 선볋
5. SELECT: 모든 컬럼 또는 특정 컬럼들을 조회한다. **SELECT 절에서 컬럼이름에 alias를 붙인 게 있다면, 이 이후 단계(ORDER BY, LIMIT)부터는 해당 alias를 사용할 수 있다.**
6. ORDER BY: 각 row를 특정 기준에 따라서 정렬한다.
7. LIMIT: 이전 단계까지 조회된 row들 중 일부 row들만을 추린다.

### 참고

MySQL 에서는 HAVING에서 SELECT의 alias가 적용되는데, 이는 SQL 표준이 아닌 예외적인 모습이다.

# 그루핑해서 보기 4

## WITH ROLLUP 이용해서 부분총계 구하기

ROLLUP = 말다, 소매를 걷어 올리다.

세부 그룹들을 좀 더 큰 단위의 그룹으로 중간중간에 합쳐준다.

먼저 써준 컬럼이 더 상위 기준이 됨. 상위 기준 안에서 각 그룹들을 합친 결과를 출력해 줌

```sql
SELECT SUBSTRING(address, 1, 2) as region, gender, COUNT(*)
FROM member
GROUP BY SUBSTRING(address, 1, 2), gender WITH ROLLUP
HAVING reigon IS NOT NULL
ORDER BY region ASC, gender DESC;
```

## 주의할 점

`HAVING region IS NOT NULL`

이 부분에서 region 컬럼의 값이 NULL인 경우를 제외하고 있는데,

부분총계 컬럼은 합쳐진 컬럼의 값을 NULL로 표시하기 때문에

HAVING 구문에 의해서 원래 region 컬럼이 NULL이 아님에도 불구하고 전체 총계까지도 제외하고 표시되어 버린다.

(1) 원래 region 컬럼이 NULL인 row들은 아예 제외하고 (2)부분 총계는 빠짐없이 보고 싶은데 `HAVING region IS NOT NULL`을 쓰자니 (2)를 만족하지 못하고, 안 쓰면 (1)을 만족하지 못한다.

'원래의 NULL' vs '부분 총계임을 나타내기 위해 사용된 NULL'을 구분할 수 있으면 좋을 것 같은데 어떻게 할 수 있을까?

# WITH ROLLUP에 관해 더 알아보기

## 1. GROUP BY 뒤 기준들의 순서에 따라 WITH ROLLUP의 결과도 달라진다.

일단 member 테이블의 row 들을 총 3가지 컬럼을 기준으로 그루핑해보자.

```sql
SELECT YEAR(birthday) AS b_year, YEAR(sign_up_day) AS s_year, gedner, COUNT(*)
FROM member
GROUP BY YEAR(birthday), YEAR(sign_up_day), gender WITH ROLLUP
ORDER BY b_year DESC;
```

그루핑이 여러 개일 때는 WITH ROLLUP이 점차적으로 넓은 범위의 부분 총계를 보여준다.

마지막 row 에는 모든 컬럼이 NULL인, 즉 세 가지 기준을 모두 고려하지 않은 부분 총계를 보여준다. = 전체 총계

여기서 중요한 점은

**WITH ROLLUP**이 GROUP BY 뒤에 나오는 그루핑 기준의 등장 순서에 **맞춰서** 계층적인 부분 총계를 보여준다는 것이다.

이는 **GROUP BY 뒤에 나오는 그루핑 기준의 순서에 따라 WITH ROLLUP이 출력하는 결과가 달라진다**라는 말이다.

만약 다른 기준을 고려하지 않고 생일에 따른 부분 총계를 보고 싶으면 GROUP BY 바로 뒤에 생일을, 가입일자를 기준으로 한 부분 총계를 보고 싶으면 GROUP BY 바로 뒤에 가입일자를 써주면 되는 것이다.

## 2. NULL임을 나타내기 위해 쓰인 NULL vs. 부분 총계를 나타내기 위해 쓰인 NULL

우리는 WITH ROLLUP을 이용해서 부분 총계를 출력할 때,

우리가 NULL을 볼 때 (1) 이게 원래 있는 NULL을 나타내는 건지, (2) 부분 총계임을 나타내기 위해 쓰인 NULL인 건지 구분 할 수 없다.

이를 구분할 수 있게 해주는 함수가 바로 `GROUPING` 이라는 함수이다.

```sql
SELECT YEAR(sign_up_day) AS s_year, gender, SUBSTRING(address, 1, 2) AS region,
GROUPING(YEAR(sign_up_day)), GROUPING(gender), GROUPING(SUBSTRING(address, 1, 2)),
COUNT(*)
FROM member
GROUP BY YEAR(sign_up_day), gender, SUBSTRING(address, 1, 2) WITH ROLLUP
ORDER BY s_year DESC;
```

`GROUPING` 함수는 그 인자를 그루핑 기준에서 고려하지 않은 부분 총계인 경우에 1을 리턴하고, 그렇지 않은 경우 0을 리턴한다.

원래 NULL이 있던 곳에는 0이 출력되고, 부분 총계를 나타내기 위해 NULL이 쓰인 곳은 1이 출력된다.

즉, `GROUPING` 함수는

(1) 실제로 NULL을 나타내기 위해 쓰인 NULL인 경우에는 0,

(2) 부분 총계를 나타내기 위해 표시된 NULL은 1

을 리턴해서 둘을 구분하게 해주는 함수이다.

  </details>
</details>

<details>
  <summary>5) 테이블 조인을 통한 깊이있는 데이터 분석</summary>
  <details>
    <summary>Foreign Key & 테이블 조인</summary>

# Foreign Key

## Foreign Key란?

테이블 간의 관계에서 다른 테이블의 특정 row를 식별할 수 있게 해주는 컬럼을 **Foreign Key**라고 한다. 우리 말로는 **외래키**라고도 한다.

이럴 때

1. 참조를 하는 테이블을 **자식 테이블**
2. 참조를 당하는 테이블을 **부모 테이블**

이라고 한다.

보통 자식 테이블의 Foreign Key가 부모 테이블의 Primary Key를 참조한다.

Foreign Key는 다른 테이블의 특정 row를 식별할 수 있어야 하기 때문에 주로 다른 테이블의 Primary Key를 참조할 때가 많다.

## Foreign Key 설정하는 이유

MySQL의 테이블 스키마 설정 창의 Foreign Keys 탭에서 Foreign Key를 설정할 수 있다.

Foreign Key를 설정하면 부모 테이블에 없는 개체에 대한 엉뚱한 정보를 추가하는 것을 미연에 방지할 수 있다.

- 예: 존재하지 않는 상품에 대한 재고 정보를 추가하려고 할 때

# 테이블 조인

## 조인이란?

실전에서는 여러 테이블을 다룰 수 있어야 하고, 테이블 간의 연관 관계를 파악하고 여러 테이블을 하나로 합쳐서 볼 수 있어야 한다.

여러 테이블을 합쳐서 하나의 테이블인 것처럼 보는 행위를 **조인(join)**이라고 한다.

이 조인을 잘해야 제대로 된 데이터 분석을 할 수 있다.

## 다른 종류의 테이블 조인하기

```sql
SELECT
	item.id,
	item.name,
	stock.item_id,
	stock.inventory_count
FROM item LEFT OTUER JOIN stock
ON item.id = stock.item_id;
```

`ON [item.id](http://item.id) = stock.item_id`

- item 테이블의 id 컬럼과 stock 테이블의 item_id 컬럼에서 값을 비교하여 서로 값이 같은 값끼리 가로로 연결하라는 뜻이다.

`FROM item LEFT OUTER JOIN stock`

- 두 테이블을 조인하는 방식을 정하는 부분인데, LEFT OUTER JOIN의 경우 왼쪽 테이블을 기준으로, 해당하는 오른쪽 테이블의 정보를 불러오는 방식이다. 만약 오른쪽 컬럼에서 해당 정보가 없다면 그 부분에는 NULL이 입력된다.
- 반대로 오른쪽 테이블을 조인 기준으로 삼고 싶다면 RIGHT OUTER JOIN을 사용하면 된다.

## 조인할 때 테이블에 alias 붙이기

```sql
SELECT
	i.id,
	i.name,
	s.item_id,
	s.inventory_count
FROM item AS i LEFT OUTER JOIN stock AS s
ON i.id = s.item_id;
```

SQL에서는 컬럼에 alias를 붙여 주었듯이 테이블에도 alias를 붙여줄 수 있다.

그 방식은 컬럼에 alias를 붙여줄 때와 같다. `item AS i` , `stock AS s`

**주의할 점**: 테이블에 alias를 붙여줄 경우에는, SQL 문에서 테이블 이름이 등장하는 다른 모든 부분들에도 alias를 사용해주어야 한다.

- `i.id`, `i.name`, `s.item_id`, `s.inventory_count`

그렇지 않으면 오류가 발생한다.

## 컬럼의 alias와 테이블의 alias

컬럼의 alias와 테이블의 alias에는 약간의 용도 차이가 있다.

우선 **컬럼의 alias**는 각 컬럼이 실제로 우리에게 그 **alias로 변환되어서 보여지게 하기 위한 용도**로 쓰인다.

**테이블의 alias**는 조회 결과에서 보기 위한 게 아니라, **SQL 문의 전체 길이를 줄여서 가독성을 높이기 위해** 사용된다.

## INNER JOIN

```sql
SELECT
	i.id,
	i.name,
	s.item_id,
	s.inventory_count
FROM item AS i INNER JOIN stock AS s
ON i.id = s.item_id;
```

INNER JOIN은 LEFT OUTER JOIN이나 RIGHT OUTER JOIN 과는 다르게, **기준이 되는 테이블이 따로 없다**

두 테이블 모두, 기준 컬럼에 일치하는 값이 있는 row들만 연결해줌.

그래서 LEFT OUTER JOIN이나 RIGHT OUTER JOIN 에서처럼 기준 컬럼의 값이 NULL이 되는 경우가 없다.

INNER JOIN은 집합으로 치면, 두 테이블 간의 **교집합**과 같다고 보면 된다.

## Foreign Key가 아닌 컬럼 기준으로 조인을 하기도 한다

만약에 Foreign Key를 기준으로 조인을 하게 되면 OUTER JOIN(LEFT 또는 RIGHT)와 INNER JOIN의 결과가 일치하게 된다.

하지만 꼭 Foreign Key를 기준으로 조인을 해야 하는 것은 아니다.

Foreign Key가 아닌 컬럼을 기준으로 해서 조인할 수도 있는데, 이렇게 하면 보통

1. LEFT OUTER JOIN
2. RIGHT OUTER JOIN
3. INNER JOIN

세 가지 조인의 결과가 모두 달라진다.

  </details>
	<details>
		<summary></summary>
	</details>
</details>
