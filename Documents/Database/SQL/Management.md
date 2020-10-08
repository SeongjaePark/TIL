본 정리 자료는 **코드잇 - SQL 데이터베이스**를 수강하며 배운 SQL 데이터베이스 지식을 정리한 내용입니다.

[코드잇 SQL 데이터베이스 코스](https://www.codeit.kr/courses/sql-database)

SQL로 하는 데이터 관리

<details>
  <summary>1) 데이터베이스와 테이블 구축</summary>
  
  # 데이터베이스 생성하기

`CREATE DATABASE 데이터베이스명;` 을 이용하면 데이터베이스를 생성할 수 있다.

다만, 이미 같은 이름의 데이터베이스가 존재한다면 오류가 난다. 이러한 오류를 피하기 위해서 다음과 같은 SQL 문을 사용할 수 있다.

`CREATE DATABASE IF NOT EXISTS 데이터베이스명;` 이미 같은 이름이 데이터베이스가 존재한다 할 지라도, 오류 표시 보다는 경고 표시 정도가 뜬다.

# 사용할 데이터베이스 지정하기

`USE 데이터베이스명;`

보통 실무에서 하나의 데이터베이스 서버 안에는 여러 개의 데이터베이스를 두고 사용한다. 그래서 데이터베이스 서버에 처음 접속하고 난 후에는, 가장 먼저 **어느 데이터베이스에서 작업을 할 것인지**를 지정해줘야 한다.

이렇게 하면 DBMS가 그 데이터베이스를 작업 중인 데이터베이스로 인식하게 되고, 그 후부터는 그렇게 지정된 데이터베이스 안에 있는 존재를 SQL 문에서 가리킬 때, 데이터베이스 이름을 적어 주지 않아도 된다는 장점이 있다.

예를 들어, A라는 데이터베이스에 animal 이라는 테이블이 있고, B 데이터베이스 안에 banana 라는 테이블이 있따.

이때, `USE A;` 를 실행하고 나면 animal 테이블의 내용을 조회하고 싶을 때 `SELECT * FROM A.animal;` 처럼 굳이 데이터베이스 이름을 붙이지 않고 `SELECT * FROM animal;` 이라고만 써도 잘 조회된다. 이미 A 데이터베이스를 사용하는 것으로 DBMS가 인식하고 있기 때문이다.

이때 B 데이터베이스는 사용하고 있지 않기 때문에, banana 테이블을 조회하려면 `SELECT * B.banana;`와 같이 데이터베이스 이름을 명시해줘야 한다.

USE 문을 써도 다른 데이터베이스 안의 것들을 언제든지 조회할 수 있다.

# 컬럼의 데이터 타입에 관하여

테이블을 생성할 때에는 각 컬럼마다 저장될 값에 알맞은 데이터 타입을 설정한다. 각 컬럼에 적절한 데이터 타입을 잘 설정하는 일은 아주 중요하다. 데이터 타입을 잘 설정해야 저장 용량을 효율적으로 활용할 수 있고, 나중에 row 수가 많아질 때는 성능에 영향을 미치기도 하기 때문이다.

사용할 수 있는 데이터 타입에는 DBMS 마다 조금씩 차이가 있는데, MySQL의 데이터 타입 중 일반적으로 쓰이는 것들은 다음 세 카테고리로 분류할 수 있다.

**Numeric Types(숫자형 타입)**

**Date and Time Types(날짜 및 시간 타입)**

**String Types(문자열 타입)**

이 밖에도 여러 카테고리가 있다.

## 1. Numeric Types (숫자형 타입)

숫자를 나타내기 위해 사용되는 데이터 타입이다.

숫자형 타입은 다시 **정수형 타입**과 **실수형 타입**으로 나눌 수 있다.

### (1) 정수형 타입

말 그대로 정수값을 저장하는 타입이다. 구체적인 타입마다 나타낼 수 있는 정수값의 범위에 차이가 있다.

1. **TINYINT**
   - 작은 범위의 정수를 저장할 때 쓰는 데이터 타입
   - 최소 -128 ~ 최대 127까지의 정수를 저장할 수 있는 타입
   - SIGNED는 '양수, 0, 음수'를 나타낼 수 있고, UNSIGNED는 '0과 양수'를 나타낼 수 있다. 이러한 원리는 다른 정수형 타입에도 똑같이 적용된다. 참고로, TYNYINT 라고만 썼을 때는 SIGNED가 붙은 것으로 자동 해석된다.
   - TINYINT SIGNED: -128 ~ 127
   - TINYINT UNSIGNED: 0 ~ 255
2. **SMALLINT**
   - TINYINT 보다 조금 더 큰 범위의 정수를 나타낼 때 쓰는 데이터 타입
   - SMALLINT SIGNED: -32768 ~ 32767
   - SMALLINT UNSIGNED: 0 ~ 65535
3. **MEDIUMINT**
   - MEDIUMINT SIGNED: -8388608 ~ 8388607
   - MEDIUMINT UNSIGNED: 0 ~ 16777215
4. **INT**
   - INT SIGNED: -2147483648 ~ 2147483647
   - INT UNSIGNED: 0 ~ 4294967295
5. **BIGINT**
   - BIGINT SIGNED: -9223372036854775808 ~ 9223372036854775807
   - BIGINT UNSIGNED: 0 ~ 18446744073709551615

### (2) 실수형 타입

정수뿐만 아니라, 소수점이 붙어있는 수 또한 표현할 수 있어야 할 경우 실수형 타입을 사용한다.

실수형 타입은 그 타입마다 얼마나 넓은 범위의 수를 나타낼 수 있는지 뿐만 아니라, 소수점 뒤에 얼마나 많은 개수의 자리수가 존재할 수 있는지가 다르다.

1. **DECIMAL**
   - 일반적으로 자주 쓰이는 실수형 타입. 보통 DECIMAL(M, D) 형식으로 나타냄.
   - M은 최대로 쓸 수 있는 전체 숫자의 자리수이고, D는 최대로 쓸 수 있는 소수점 뒤에 있는 자리의 수를 의미
   - EX) DECIMAL (5, 2) 라면 -999.99 부터 999.99 까지의 실수를 나타낼 수 있음
   - M은 최대 65, D는 30까지의 값을 가질 수 있음
   - DECIMAL 이라는 단어 대신 DEC, NUMERIC, FIXED를 써도 됨
2. **FLOAT**
   - 3.402823466E+38 ~ -1.175494351E-38, 0, 1.175494351E-38 ~ 3.402823466E+38 범위의 실수 표현 가능
3. **DOUBLE**
   - 1.7976931348623157E+308 ~ -2.2250738585072014E-308, 0, 2.2250738585072014E-308 ~ 1.7976931348623157E+308 범위의 실수 표현 가능
   - FLOAT에 비해 더 넓은 범위의 수를 나타낼 수 있을 뿐만 아니라, 그 정밀도 또한 더 높은 타입이다. (소수점 뒤에 최대로 허용가능한 자리수가 더 많음)

## 2. 날짜 및 시간 타입 (Date and Time Types)

데이터베이스에서는 날짜 및 시간 정보를 다뤄야 하는 경우가 정말 많다.

### (1) DATE

날짜를 지정하는 데이터 타입

날짜는 '2020-10-07' 이런 형식의 연, 월, 일 순으로 값을 나타낸다.

### (2) DATETIME

날짜와 시간을 저장하는 데이터 타입

'2020-10-07 11:01:53' 이런 식으로 연, 월, 일, 시, 분, 초를 나타낸다.

### (3) TIMESTAMP

날짜와 시간을 저장하는 데이터 타입

'2020-10-07 11:02:14' 이런 식으로 연, 월, 일, 시 ,분, 초를 나타낸다. 그럼 DATETIME 타입과는 어떤 점이 다를까?

TIMSTAMP 타입은 타임 존(time_zone) 정보도 함께 저장한다는 점이 다르다. UTC 기준. 한국은 UTC+9

만약 MySQL 서버의 시간대 설정을 바꾸면, DATETIME 타입 컬럼의 값은 그대로 유지되지만, TIMESTAMP 타입 컬럼의 값은 바뀐 시간대에 맞게 변경된다.

만약 타임 존 정보를 굳이 함께 저장할 필요가 없다면 DATETIME 타입을, 타임 존 정보도 함께 저장하고 싶다면 TIMESTAMP 타입을 설정하면 된다.

### (4) TIME

시간을 나타내는 데이터 타입.

'11:08:31' 형식으로 시, 분, 초를 나타낸다.

## 3. 문자열 타입 (String Type)

문자열을 저장하기 위한 타입

이름, 댓글, 구매 후기 등 문자열 형태의 데이터는 정말 다양하다

### (1) CHAR

문자열을 나타내는 기본 타입으로 Character의 줄임말.

CHAR(30) 이런 형식으로 나타낸다.

괄호 안의 숫자는 문자를 최대 몇 자까지 저장할 수 있는지를 나타낸다.

CHAR 타입의 괄호 안에는 0부터 255까지의 숫자를 적을 수 있다.

### (2) VARCHAR

VARCHAR(30) 이런 식으로 문자열의 최대 길이를 지정할 수 있는 문자열 타입이다.

괄호 안에 최소 0 부터 최대 65,535를 쓸 수 있다.

VARCHAR은 CHAR보다 허용되는 최대 저장 길이가 더 크다는 점 말고 다른 차이점도 있다.

CHAR는 고정 길이 타입이고, VARCHAR는 가변 길이 타입이라는 점이다. VARCHAR 이라는 단어 자체가 Character VAring의 줄임말로 가변 문자열을 나타낸다.

CHAR(10), VARCHAR(10)이 있을 때, CHAR(10)은 어떤 길이의 문자열이 저장되더라도 항상 그 값이 10만큼의 저장 용량을 차지한다. 하지만 VARCHAR(10)의 경우 만약 값이 'Hello' 이런 5자라면 저장 용량도 5만큼 차지한다. **저장 용량이 설정된 최대 길이에 맞게 고정되는 게 아니라, 실제 저장된 값이 맞게 최적화 되는 것이다.** 대신 VARCHAR 타입으로 값이 저장될 때는 해당 값의 사이즈를 나타내는 부분(1byte 또는 2byte)이 저장 용량에 추가된다.

따라서 값의 길이가 크게 변하지 않을 컬럼에는 CHAR 타입을 사용하고, 길이가 들쑥날쑥할 컬럼에는 VARHAR 타입을 쓰는 게 좋다.

### (3) TEXT

문자열을 저장하는 데이터 타입으로, 최대 65535자까지 저장할 수 있다.

이외에도 16,777,215자까지 저장할 수 있는 MEDIUMTEXT, 4294967295자까지 저장할 수 있는 LONGTEXT 타입이 있다.

VARCHAR 타입과 TEXT 계열의 타입은 내부 구현에서 일부 차이가 있는데, 일단은 정말 길이가 긴 문자열을 저장하려면 TEXT 계열의 타입을 써야한다는 정도만 기억하자

# CREATE TABLE

CREATE TABLE을 이용하여 테이블과 컬럼들을 만들어줄 수 있다.

데이터베이스명, 테이블명, 그리고 컬럼명 앞뒤로 작은 따옴표 ' 가 아니라 백틱(backtick) ` 을 써줘야 한다는 사실에 주의해야 한다.

작성 양식

```sql
CREATE TABLE `데이터베이스명`.`테이블명` (
	`컬럼명1` 데이터타입 속성,
	`컬럼명2` 데이터타입 속성,
	...
	PRIMARY KEY (`컬럼명`)); # 이렇게 설정하지 않고, 컬럼 뒤에 속성으로 PRIMARY KEY 를 적어주어도 된다.
```

작성 예시

```sql
CREATE TABLE `practice`.`new_table` (
	`id` INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
	`name` VARCHAR(20) NULL, # NULL이 들어가도 된다는 의미. NULL은 생략해주어도 자동으로 적용된다.
	`student_number` INT NULL,
	`major` VARCHAR(15) NULL,
	`email` VARCHAR(50) NULL,
	`phone` VARCHAR(15) NULL,
	`admission_date` DATE NULL));
```

## 백틱과 따옴표

DBMS에서는 데이터베이스, 테이블, 컬럼 등과 같은 구성요소를 보통 **object(객체)** 라고 한다. 그리고 이런 object에 붙여준 이름을 **identifier(식별자)** 라고 한다. MySQL에서 **백틱**은 해당 단어가 identifier 임을 나타내는 기호이다.

그런데 사실 아래 SQL 문처럼 식별자에 굳이 백틱을 쓰지 않아도 SQL 문은 잘 실행된다.

```sql
CREATE TABLE 데이터베이스명.테이블명 (
	컬럼명1 데이터타입 속성,
	컬럼명2 데이터타입 속성,
	...
	PRIMARY KEY (컬럼명));
```

그럼 굳이 왜 백틱을 쓰는 걸까?

(1) 백틱을 쓰면 어느 단어가 사용자가 직접 이름을 지은 부분인지를 보다 확실하게 나타내줄 수 있음

(2) 이미 SQL 문법에 정해진 키워드로 이름을 지속 싶을 때는 백틱을 쓰는 것이 필수임

- 예를 들어, SELECT 라는 이름의 테이블을 만든다고 할 경우 SELECT를 백틱으로 감싸지 않으면 문법 오류로 인해 실행되지 않는다.
- 하지만 굳이 SQL 문법에 이미 존재하는 키워드로 이름을 짓는 것은 나중에 혼동의 위험성이 있기 때문에 하지 않는 것이 좋다.

# 테이블에 row 추가하기

## 모든 컬럼에 값이 있는 row 추가

작성 양식

```sql
INSERT INTO 테이블명 (컬럼명1, 컬럼명2, 컬럼명3, ...) # 만약 모든 컬럼에 값이 있는 row를 추가할 때는 컬럼명 부분을 전부 생략해줘도 된다. (대신 컬럼명 순서에 맞게 값을 넣어주어야 함)
	VALUES (값1, 값2, 값3, ...);
```

작성 예시

```sql
INSERT INTO student
(addmission_date, email, id, major, name, phone, student_number)
    VALUES ('2019-03-01', '1234@mail.com', 1, 'psychology', 'seongjae', '010-xxxx-xxxx', 20191919);

```

## 특정 컬럼들에만 값이 있는 row 추가

작성 양식은 같다.

작성 예시

```sql
INSERT INTO student
(addmission_date,  major, name, student_number)
    VALUES ('2020-01-01', '컴퓨터공학', 'DevPark', 20202020);

```

위 SQL 문에 포함되어 있지 않은 컬럼에는 NULL이 들어가게 된다.

다만, id 컬럼의 경우 따로 값을 넣어주지 않아도, AUTO_INCREMENT 속성을 할당했기 때문에, 이전 row의 id 값보다 1 큰 값이 자동으로 입력된다. 따라서 id 컬럼의 모든 값이 고유한 지를 확인할 필요가 없어진다.

참고로 AUTO_INCREMENT 속성은 정수형 데이터 타입의 컬럼에만 설정할 수 있다.

# 테이블의 row 갱신하기

작성 양식

```sql
UPDATE 테이블명 SET 컬럼명1 = 새로운값1, 컬럼명2 = 새로운값2 WHERE 특정row의조건;
```

테이블의 row를 갱신할 때에는 WHERE 절 뒤에 갱신하려는 row에 해당하는 조건(예: id=1)을 잘 적는 것이 중요하다.

WHERE 절을 적지 않을 경우, 모든 row의 정보가 갱신된다는 점에 주의해야 한다!

작성 예시

```sql
UPDATE student
	SET major = '멀티미디어학과', name = '홍길동'
WHERE id = 2;
```

## 컬럼의 기존 값을 기준으로 갱신하기

만약 기말고사 문제 중 배점 3점짜리 문제 하나에 오류가 있어서 모두 정답 처리를 했다고 해보자.

이 문제로 이미 점수를 얻어 간 학생이 없다고 가정하면, 모든 학생의 점수에 +3점을 해줘야 할 것이다.

이때 테이블을 어떻게 갱신해야 할까?

```sql
UPDATE final_exam_result SET score = 93 WHERE id = 1;
UPDATE final_exam_result SET score = 87 WHERE id = 2;
UPDATE final_exam_result SET score = 90 WHERE id = 3;
```

이런 식으로 여러 줄의 UPDATE 문을 일일이 실행하는 것은 너무 번거롭고, 실수도 잦을 것이다.

UPDATE 문을 사용할 때는 기존 값을 그대로 활용하는 방법이 있다.

```sql
UPDATE final_exam_result SET score = score + 3;
```

이렇게 써주면 모든 row의 score 컬럼의 값이 기존 값보다 3이 더 큰 값으로 갱신된다.

이렇게 컬럼의 이름의 활용해서 기존 값을 기반으로 갱신하는 경우도 많다.

# 테이블의 row 삭제하기

작성 양식

```sql
DELETE FROM 테이블명 WHERE 삭제할row조건;
```

DELETE 또한 WHERE 절을 쓰지 않으면 모든 row들이 삭제된다는 점에 주의해야 한다!

작성 예시

```sql
DELETE FROM student WHERE id = 4;
```

## 물리 삭제 VS 논리 삭제

어떤 row를 삭제하는 방법에는 크게 2가지 방법이 있다.

바로 '물리 삭제'와 '논리 삭제' 이다.

**물리 삭제**: 그냥 row를 바로 삭제해버리는 것

**논리 삭제**: 삭제해야할 row를 삭제하지 않고, '삭제 여부'를 나타내는 별도의 컬럼을 두고, 거기에 '삭제되었음'을 나타내는 값을 넣는 것.

**논리 삭제 예시** (컬럼을 미리 추가해 두었다고 가정)

```sql
UPDATE order SET is_cancelled = 'Y'
# 이렇게 is_cancelled, is_deleted 와 같이 삭제 여부를 나타내는 별도의 컬럼을 두고,
# 'Y' 등과 같이 삭제되었음을 나타내는 값을 넣는 것이다.
```

### 논리 삭제를 하는 이유?

사용자 취향 파악, 범죄 수사 등에 활용 (탈퇴한 사람의 기록) 등 다양한 이유가 있을 수 있다.

### 논리 삭제의 단점

나중에 삭제되지 않고 유효한 row들만 조회해야할 때는

```sql
SELECT * FROM WHERE is_cancelled != 'Y';
SELECT * FROM WHERE is_deleted != 'Y';
```

처럼 WHERE 절에 별도의 조건을 추가 해줘야 해서 번거롭다는 단점이 있다.

그리고 실제로 row를 삭제하는 것이 아니기 때문에 아무리 삭제를 해도 데이터베이스 내의 저장 용량은 줄어들지 않는다는 단점이 있다.

이런 단점을 보완하기 위해 기본 정책은 논리 삭제로 두되,

- 이미 데이터 분석에 활용되었거나
- 고객이 동의한 데이터 보유 기간이 지난 row들은

정기적으로 물리 삭제하는 방법을 활용하기도 한다.

</details>

<details>
  <summary>2) 테이블 다루기</summary>
  <details>
    <summary>컬럼 구조 변경</summary>

# 컬럼 구조 변경

## 컬럼 정보를 한 눈에 보여주는 DESCRIBE

DESCRIBE 문을 쓰면 테이블의 컬럼 정보를 한 눈에 볼 수 있다.

```sql
DESCRIBE 테이블명; # DESCRIBE를 그냥 DESC 라고 줄여서 써도 된다.
```

이렇게 치면 해당 테이블의 컬럼 구조, 각 컬럼의 데이터 타입, 속성을 볼 수 있다.

그럼 각 컬럼에 대한 다음과 같은 정보가 나타난다.

Field: 컬럼의 이름

Type: 컬럼의 데이터 타입

Null: 컬럼의 Null 속성 유무

Key: Primary Key, Unique 속성 여부

Default: 컬럼의 기본값

Extra: AUTO_INCREMENT 등의 기타 속성

## 컬럼 추가

작성 양식

```sql
ALTER TABLE 테이블명 ADD 추가할_컬럼명 데이터타입 속성;
```

작성 예시

```sql
ALTER TABLE student ADD gender CHAR(1) NULL;
```

## 컬럼 이름 변경

작성 양식

```sql
ALTER TABLE 테이블명
	RENAME COLUMN 원래의_컬럼명 TO 새로운_컬럼명;
```

작성 예시

```sql
ALTER TABLE student
	RENAME COLUMN student_number TO registration_number;
```

## 컬럼 삭제

작성 양식

```sql
ALTER TABLE 컬럼명 DROP COLUMN 삭제할_컬럼명; # COLUMN 부분 생략 가능
```

작성 예시

```sql
ALTER TABLE student DROP addmission_date;
```

## 컬럼 데이터 타입 변경

작성 양식

```sql
ALTER TABLE 테이블명 MODIFY 컬럼명 데이터타입;
```

작성 예시

```sql
ALTER TABLE student MODIFY major INT;
```

이떄, 컬럼의 값들이 변경하려고 하는 데이터 타입에 맞지 않으면 오류가 난다. 따라서 변경하려는 데이터 타입에 맞게 컬럼의 값들을 수정해줘야 한다.

```sql
UPDATE student SET major = 3 WHERE major = '심리학과'
UPDATE student SET major = 5 WHERE major = '수학과'
UPDATE student SET major = 1 WHERE major = '컴퓨터공학과';
```

## UPDATE 가 안 되는 경우

Workbench에서 위의 UPDATE 문에서 오류가 나는 경우

Response 탭에서 에러 메세지를 보면 이렇게 나타난다.

'Error Code: 1175. You are using safe update mode and you tried to update a table without a WHERE that uses a KEY column. To disable safe mode, toggle the option in Preferences -> SQL Editor and reconnect.'

내가 Workbench에서 safe update 모드를 사용하고 있기 때문에, KEY column을 사용해서 테이블을 갱신해야 한다는 것이다.

여기서 KEY column이란 Primary Key를 의미한다.

safe update 모드란 '안전한 갱신'을 보장하기 위한 모드로,

```sql
UDPATE student SET major = 1;
```

처럼 모든 row의 특정 컬럼을 갱신해버리는 SQL 문이나,

```sql
UPDATE student SET major = 1 WHERE major = '컴퓨터공학과';
```

처럼 WHERE 절에 Primary Key가 사용되지 않은 UPDATE 문이 실행되지 않도록 한다.

이건 UPDATE 문을 주의 깊게 사용하지 않을 때 발생할 수 있는 위험한 결과를 방지하기 위한 DBMS 상의 모드이다.

이 모드를 끄려면 Workbench의 Preferences 에 가서 Safe Updates 의 체크박스를 해제하고 확인한 뒤, 접속을 끊고 재연결 하면 된다.

  </details>
  <details>
    <summary>컬럼 속성 주기</summary>

# 컬럼 속성 주기

## 컬럼에 NOT NULL 속성 주기

데이터 타입 뿐만 아니라, 컬럼의 속성을 변경할 때에도 MODIFY를 쓴다

작성 양식

```sql
ALTER TABLE 테이블명 MODIFY 컬럼명 데이터타입 NOT NULL;
```

작성 예시

```sql
ALTER TABLE student MODIFY name VARCHAR(35) NOT NULL; # 데이터 타입과 속성을 동시에 바꿀 수도 있다
ALTER TABLE student MODIFY registration_number INT NOT NULL;
ALTER TABLE student MODIFY major INT NOT NULL; # 데이터 타입을 바꾸지 않더라도, 데이터 타입을 써주지 않으면 문법 오류가 난다
```

아래와 같이 NOT NULL 속성을 부여받은 컬럼의 값이 없는 새로운 row를 추가하려고 하면 다음과 같은 오류가 난다.

```sql
INSERT INTO student (email, phone, gender)
	VALUES ('abc@naver.com', '010-1234-5678', 'm');
```

Error Code 1364. Field 'name' doesn't have a default value

## 컬럼에 DEFAULT 속성 주기

NULL 속성을 가진 컬럼의 경우, default value가 NULL 로 되어있어, 값을 주지 않으면 값이 NULL이 된다.

반면, NOT NULL 속성을 가진 컬럼의 경우, default value가 없어 값을 주지 않으면 오류가 생긴다. 하지만, default value를 정해줌으로써 값을 따로 주지 않아도 오류가 생기지 않게 할 수 있다.

작성 양식

```sql
ALTER TABLE 테이블명 MODIFY 컬럼명 데이터타입 NULL속성여부 DEFAULT 디폴트값;
# NULL 속성 여부를 생략해도 오류가 나지는 않으나,
# NOT NULL 속성을 가졌던 컬럼의 경우 NULL 속성을 가진 것으로 변경된다.
```

작성 예시

```sql
ALTER TABLE student MODIFY major INT NOT NULL DEFAULT 101;
```

이렇게 컬럼의 디폴트 값을 정해주면, 해당 컬럼의 값이 없는 새로운 row 를 추가하더라도 디폴트 값이 들어간다.

이때 NOT NULL 속성을 가진 컬럼의 경우도 더 이상 오류가 나지 않고 해당 컬럼에 디폴트 값이 추가된다.

## DATETIME, TIMESTAMP 타입의 컬럼에 값을 넣는 2가지 방식

테이블에 어떤 row가 추가되거나 갱신되었을 때, 그 추가 혹은 갱신 시각을 저장해야 할 때가 있다.

예를 들어,

- 게시글 업로드 시각,
- 댓글이 달린 시각,
- 댓글을 수정한 시각

등의 정보가 그 예시다.

### 1. NOW() 함수 사용하기

어떤 SNS에서 사용자가 업로드한 게시물 정보를 저장한 post 테이블이 있고, 아래와 같은 컬럼들로 구성되어 있다고 하자.

- id: PRIMARY KEY 역할을 하는 컬럼. AUTO_INCREMENT 속성을 가짐
- title: 게시물의 제목
- content: 게시물의 내용
- upload_time: 게시물 최초 업로드 시각
- recent_modified_time: 게시물 최근 갱신 시각

이 테이블에 다음과 같이 게시물 하나가 추가된다

```sql
INSERT INTO post (title, content, upload_time, recent_modified_time)
	VALUES('~~~ 탐방기', '오늘은 ~~~ ...', NOW(), NOW());
```

위 SQL 문을 보면 upload_time 컬럼, recent_modified_time 컬럼에 NOW() 라는 함수의 리턴값을 넣았다.

테이블을 조회해보면 두 컬럼에 현재 시각이 들어가 있다.

만약 이 포스트의 내용을 다시 갱신한다고 해보자.

```sql
UPDATE post
	SET content = '오늘 간 곳은 ~~~ ...',
			recent_modified_time = NOW()
	WHERE id = 1;
```

content 컬럼을 갱신할 때 동시에, recent_modified_time 컬럼의 값도 NOW 함수의 리턴값으로 갱신해주면 된다.

이렇게 NOW 함수를 쓰면 현재 시간을 편하게 구할 수 있다.

그런데 이 방법 말고도 컬럼에 현재 시각을 넣는 다른 방법도 있다.

### 2. 컬럼에 DEFAULT CURRENT_TIMESTAMP / ON UPDATE CURRENT_TIMESTAMP 속성 설정하기

DATETIME 타입 또는 TIMESTAMP 타입의 컬럼에는

DEFAULT CURRENT_TIMESTAMP 라는 속성과 ON UPDATE CURRENT_TIMESTAMP 라는 속성을 줄 수 있다.

다음과 같이 post 테이블의 upload_time 컬럼과 recent_modified_time 컬럼에 위의 두 속성을 추가할 수 있다.

```sql
ALTER TABLE post
	MODIFY upload_time DATETIME DEFAULT CURRENT_TIMESTAMP,
	MODIFY recent_modified_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP;
```

upload_time 컬럼에는 DEFAULT CURRENT_TIMESTAMP 속성만 줬고,

recent_modified_time 컬럼에는 DEFAULT CURRENT_TIMESTAMP 속성과 ON CURRENT_TIMESTAMP 속성을 둘다 줬다.

이제 테이블에 새로운 row를 추가해보자.

```sql
INSERT INTO post (title, content)
	VALUES ('오랜만에 ~~', '벌써 가을 ~~ ...');
```

title, content 컬럼에만 값을 주고, upload_time, recent_modified_time 컬럼에는 값을 주지 않았다는 것을 알 수 있다.

그런데 post 테이블을 확인해보면 새로운 row에 upload_time, recent_modified_time 컬럼에 별도로 값을 주지 않았는데도 현재 시간이 값으로 잘 들어가 있다.

두 컬럼에 DEFAULT CURRENT_TIMESTAMP 속성을 줬기 때문이다.

그리고 나서 이 row의 content 컬럼 값을 갱신한다.

```sql
UPDATE post
	SET content = '등산 .. ~~'
	WHERE id = 2;
```

마찬가지로, 최근 갱신 시각을 나타내는 recent_modified_time 컬럼에는 따로 값을 지정하지 않았다.

다시 post 테이블을 확인해보면 recent_modified_time 컬럼에 값을 주지 않았는데도 최근 갱신 시간이 들어가 있다.

recent_modified_time 컬럼에 ON UPDATE CURRENT_TIMESTAMP 라는 속성을 주었기 때문이다.

### 정리

만약 각 row마다 시간값에 관한 처리를 다르게 해줘야 하는 경우라면 NOW 함수를 쓰는 것이 좋을 것이다.

하지만 그럴 필요가 없는 상황이고, 굳이 날짜/시간 값을 별도로 신경쓰기가 싫다면 해당 컬럼에 DEFAULT CURRENT_TIMESTAMP 속성, ON UPDATE CURRENT_TIMESTAMP 속성을 설정해서 DBMS가 알아서 관리하도록 하는 게 편할 것이다.

## 컬럼에 UNIQUE 속성 주기

컬럼 속성 중 UQ 는 Unique 속성을 나타내는데, 컬럼에 이 속성을 추가하면 그 컬럼에 같은 값을 가진 또 다른 row가 추가되는 것을 막아준다.

작성 양식

```sql
ALTER TABLE 테이블명 MODIFY 컬럼명 데이터타입 UNIQUE;
```

작성 예시

```sql
ALTER TABLE student MODIFY registration_number INT NOT NULL UNIQUE;
```

이렇게 컬럼에 UNIQUE 속성을 추가한 후,

```sql
INSERT INTO student (name, registration_number)
	VALUES ('홍길동', 20112405);
```

이미 registration_number에 존재하는 값을 가진 row를 추가한다. 그럼 다음과 같은 오류가 발생한다.

Error Code: 1062, Duplicate entry '20112405' for key 'student.registration_number'

이는 registration_number 컬럼에 중복되는 값을 가진 row가 있기 때문에, 새 row가 추가될 수 없다는 것이다.

이처럼, 반드시 각 row마다 고유한 값을 가져야 하는 컬럼이 있다면 UNIQUE 속성을 주면 된다.

## Primary Key와 Unique 속성의 차이

어떤 컬럼의 값이 각 row마다 달라야할 때 Unique 속성을 준다.

그런데 Primary Key도 이런 성질을 가지고 있었다.

Primary Key는 테이블에서 특정 row 하나를 식별할 수 있도록 해주는 컬럼이다. 그리고 이를 위해 Primary Key에 해당하는 컬럼은 각 row마다 다른 값을 가져야 한다.

### Primary Key와 Unique 속성의 차이?

일단 Primary Key 는 테이블당 오직 하나만 존재할 수 있다.

이에 반해 Unique 속성은 각각의 컬럼들이 가질 수 있는 속성이기 때문에 한 테이블에 여러 개의 Unique 속성들이 존재할 수 있다.

중요한 차이점 중 하나는 Priamry Key는 NULL을 가질 수 없지만, Unique는 NULL을 허용한다는 점이다.

- Primary Key는 애초에 그 목적이 테이블에서 하나의 row를 식별하기 위해 사용되는 컬럼인데, 여기에 NULL이 있어버리면 특정 row를 검색해야할 때 등호(=) 연산을 수행할 수 없기 때문에 NULL을 허용하지 않는 것으로 추측된다고 한다.

Primary Key에 NULL이 있는 row가 존재한다면,

```sql
SELECT * FROM member WHERE id = n;
```

와 같은 SQL 문을 실행할 때 그 row를 찾을 수 없게 된다. 만약 n 부분에 NULL을 넣는다고 해도 안 된다. 왜냐하면 WHERE NULL = NULL은 True를 리턴하지 않기 때문이다. SQL에서 NULL은 어떤 값이 아니라 '값이 없는 상태'를 의미하는 단어일 뿐이다. 그래서 같은 NULL 끼리 비교해도 같다는 결과가 나오지 않는다.

```sql
SELECT * FROM member WHERE id IS NULL;
```

과 같이 NULL 여부를 확인할 수 있는 별도의 SQL 문을 사용할 수는 있지만, 단지 NULL이 있는 해당 row 하나만을 위해 이렇게 별도로 해야한다는 건 바람직하지 않다. 이런 이유 때문에 Primary Key에서는 NULL이 허용되지 않는다.

이 뿐만 아니라, Primary Key 는 다른 테이블의 Foreign Key에 의해 참조될 수도 있는 컬럼이다.

그리고 보통은 이런 Foreign Key를 기준으로 두 테이블을 조인하는 경우가 많은데, 이때 부모 테이블의 Primary Key 가 NULL이라면 그 row를 참조해야 하는 자식 테이블의 row들과 제대로 조인될 수가 없다.

왜냐하면 조인을 할 때도

```sql
SELECT * FROM table_a INNERJOIN table_b ON table_a.referenced_col = table_b.referencing_col;
```

이런 식으로 ON 절에 등호를 붙여서 조인 기준을 설정하는 것이 일반적이기 때문이다. 이 경우에도 NULL = NULL은 True를 리턴하지 않기 때문에 NULL이 있는 row끼리는 조인이 되지 않는다.

### 정리

Primary Key는 그 존재 목적과 실무적인 이유 등으로 인해 당연히 NULL이 들어가면 안 된다

이에 반해, Unique 속성은 각 row마다 각자 다른 값을 가지도록 강제하는 것이다. 그리고 이때 각 row마다 해당 컬럼의 값이 다르다면, NULL도 Unique 하다고 인정되기 때문에 Unique 속성이 있는 컬럼에는 NULL이 허용되는 것이다.

Cf) MySQL에서 Unique 속성은 중복되는 값은 허용하지 않지만, 여러 row가 NULL인 상태는 허용한다. ex) 사원번호가 중복되는 것은 허용하지 않지만, 아직 사원번호가 부여되지 않은 신입사원들의 정보를 입력할 수 있음.

## 테이블에 CONSTRAINT(제약) 걸기

하나의 테이블에는 시간이 지나면서 점점 더 많은 row들이 쌓이게 된다. 주의할 점은, 테이블에 이상한 row가 추가되는 것을 막아야 한다는 것이다. 예를 들어, 꼭 있어야 할 값이 없거나, 이상한 값이 있는 row가 추가되는 것을 막아야 한다.

테이블에 CONSTRAINT(제약)을 추가하면 이상한 row가 추가되는 것을 막을 수 있다.

작성 양식

```sql
ALTER TABLE 테이블명
	ADD CONSTRAINT 제약_이름 CHECK (제약 내용);
```

작성 예시

```sql
ALTER TABLE student
	ADD CONSTRAINT st_rule CHECK (registration_number < 30000000);
```

이렇게, registration 컬럼에는 30000000 보다 작은 값만 들어갈 수 있도록 제약을 걸었다.

```sql
INSERT INTO student (name, registration_number)
	VALUES ('홍길동', 30000000);
```

위와 같이 제약 사항을 위반하는 row를 추가하면, 다음과 같이 제약사항이 위반되었다는 오류가 뜬다.

Error Code: 3819. Check constraint 'st_rule' is violated.

### 제약 사항을 삭제하는 법

작성 양식

```sql
ALTER TABLE 테이블명 DROP CONSTRAINT 제약_이름;
```

작성 예시

```sql
ALTER TABLE student DROP CONSTRAINT st_rule;
```

### 2개 이상의 조건이 담긴 제약 만들기

작성 양식

```sql
ALTER TABLE 테이블명
	ADD CONSTRAINT 제약_이름
	CHECK (조건1 AND 조건2);
```

작성 예시

```sql
ALTER TABLE student
	ADD CONSTRAINT st_rule
	CHECK (email LIKE '%@%' AND gender IN ('m', 'f'));
```

이제 이 테이블에

```sql
INSERT INTO student (name, email, gender)
	VALUES ('홍길동', '이상한이메일', 'm');
```

또는

```sql
INSERT INTO student (name, email, gender)
	VALUES ('홍길동', 'gildongh@naver.com', 'z');
```

와 같이 제약 조건 중 어느 하나라도 위반하는 row를 추가하려고 하면 오류가 뜨게 된다.

## 그 밖의 컬럼 관련 작업들

한 축구팀의 선수 정보를 관리하는 player_info 테이블이 있다고 가정하자.

- role: 선수의 역할(공격수, 수비수 등). CHAR(5)
- name: 선수의 이름. INT
- id: PRIMARY KEY. INT

이 테이블의 컬럼 구조를 좀 더 보기 좋게 만들어 보자.

### 1. 컬럼 가장 앞으로 당기기

Primary Key 역할을 하는 id 컬럼이 가장 뒤에 있어서 보기에 어색하다.

```sql
ALTER TABLE player_info
	MODIFY id INT NOT NULL AUTO_INCREMENT FIRST;
```

이렇게 컬럼 정보의 맨 뒤에 FIRST 라고 써주면, 해당 테이블의 가장 첫 번째 컬럼이 된다.

이런 식으로 테이블에서는 보통 Primary Key에 해당하는 컬럼을 가장 앞에 두는 것이 일반적이다.

### 2. 컬럼 간의 순서 바꾸기

선수 역할을 나타내는 role 컬럼이 선수 이름을 나타내는 name 컬럼보다 이후에 나오는 것이 더 자연스러울 것 같다.

role 컬럼을 name 컬럼 이후에 위치하도록 해보자.

```sql
ALTER TABLE player_info
	MODIFY role CHAR(5) NULL AFTER name;
```

컬럼 속성 가장 마지막에 AFTER name 이라고 썼다. 표현 그대로 name 컬럼 바로 다음으로 위치를 바꾸라는 뜻이다.

### 3. 컬럼의 이름과 컬럼의 데이터 타입 및 속성 동시에 수정하기

컬럼의 이름을 수정할 때는 `RENAME COLUMN A TO B` 절을,

컬럼의 타입 및 속성을 수정할 때는 `MODIFY` 절을 사용한다고 배웠다.

이 두 가지 작업을 한 번에 수행해주는 절이 바로 `CHANGE` 절이다.

role 컬럼의 (1) 이름을 position 으로 바꾸고, (2) 동시에 그 데이터 타입을 CHAR(5) 에서 VARCHAR(2)로, 그 속성도 NULL 에서 NOT NULL로 바꾸자.

```sql
ALTER TABLE player_info
	CHANGE role position VARCHAR(2) NOT NULL;
```

이렇게 컬럼의 이름과, 데이터 타입 및 속성을 동시에 바꾸고 싶을 때는 CHANGE 절을 사용하면 편리하다.

### 4. 여러 작업 동시에 수행하기

`ALTER TABLE` 문 뒤에는 컬럼에 관한 작업을 하는 절들을 여러 개 두는 것이 가능하다.

(1) id 컬럼의 이름을 registration_number로 수정

(2) name 컬럼의 데이터 타입을 VARCHAR(20)으로, 속성을 NOT NULL로 수정

(3) position 컬럼을 테이블에서 삭제

(4) 새로운 컬럼 2개(height, weight) 추가

위의 4가지 작업을 동시에 수행하는 SQL 문을 작성해 보자.

```sql
ALTER TABLE player_info
	RENAME COLUMN id TO registration_number,
	MODIFY name VARCHAR(20) NOT NULL,
	DROP COLUMN position,
	ADD height DOUBLE NOT NULL,
	ADD weight DOUBLE NOT NULL;
```

위의 SQL 문처럼, 각 작업마다 굳이 매번 `ALTER TABLE` 을 써줄 필요 없이, 여러 가지 작업을 하나의 `ALTER TABLE` 문 안에서 한 번에 수행하는 것이 가능하다.

위의 SQL 문 중에서 작업 (1)과 작업 (2)를 수행하는 절을 `CHANGE` 절로 아래와 같이 쓸 수도 있다

```sql
ALTER TABLE palyer_info
	CHANGE id registration_number INT NOT NULL AUTO_INCREMENT,
	CHANGE name name VARCHAR(20) NOT NULL;
```

컬럼의 이름만 바꾸거나, 컬럼의 데이터 타입 및 속성만 바꿀 때에도 이런 식으로 `CHANGE` 절로도 처리할 수 있다.

  </details>
</details>

<details>
  <summary>3) Foreign Key 제대로 사용하기</summary>
</details>
