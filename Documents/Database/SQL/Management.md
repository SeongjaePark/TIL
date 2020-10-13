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
  <details>
    <summary>테이블 자체를 다루기</summary>

# 테이블 자체를 다루기

## 테이블 이름 변경, 복사본 만들기, 삭제

### 테이블 이름 변경

작성 양식

```sql
RENAME TABLE 기존_테이블_이름 TO 새로운_테이블_이름;
```

작성 예시

```sql
RENAME TABLE student TO undergraduate
```

### 복사본 만들기

작성 양식

```sql
CREATE TABLE 새로운_테이블_이름 AS SELECT * FROM 복사할_테이블_이름;
```

작성 예시

```sql
CREATE TABLE copy_of_undergraduate AS SELECT * FROM undergraduate;
```

기존 테이블을 직접 다루기가 무서울 때는 이렇게 기존 테이블을 복사한 테이블을 활용해서 다뤄볼 수 있다.

### 테이블 삭제하기

작성 양식

```sql
DROP TABLE 테이블명;
```

작성 예시

```sql
DROP TABLE copy_of_undergraduate;
```

## 테이블 컬럼 구조만 복사하기

작성 양식

```sql
CREATE TABLE 새로운_테이블_이름 LIKE 복사할_테이블_이름;
```

작성 예시

```sql
CREATE TABLE copy_of_undergraduate LIKE undergraduate;
```

컬럼 구조가 같은 다른 테이블의 row들 그대로 가져오기

```sql
INSERT INTO copy_of_undergraduate SELECT * FROM undergraduate;
```

일부 조건을 충족하는 row들만 가져오기

```sql
INSERT INTO copy_of_undergraduate
	SELECT * FROM undergraduate WHERE major = 101;
```

## INSERT INTO 문과 서브쿼리

SQL 문에서 하나의 부품처럼 사용되는 `SELECT` 문을 서브쿼리라고 한다.

지금까지는 `SELECT` 문 안에 또 `SELECT` 문이 있는 경우만 봤는데, 위의 SQL 문처럼 `INSERT INTO` 문에서 서브쿼리를 사용하는 것도 가능하다.

서브쿼리는 다음과 같은 식으로도 활용 가능하다

```sql
INSERT INTO freshman SELECT * FROM undergraduate WHERE grade = 1; # 1학년 테이블
INSERT INTO sophomore SELECT * FROM undergraduate WHERE grade = 2; # 2학년 테이블
INSERT INTO junior SELECT * FROM undergraduate WHERE grade = 3; # 3학년 테이블
INSERT INTO senior SELECT * FROM undergraduate WHERE grade = 4; # 4학년 테이블
```

만약 undergraduate 테이블에 학년을 나타내는 grade 컬럼이 있다고 가정하면, 이런 식으로 학년별 테이블을 새롭게 만들 수도 있다.

기존 테이블은 건드리지 않고, 기존 테이블의 특정 row들만으로도 새 테이블을 만들어야 할 때 사용하면 꽤 유용할 것이다.

다음과 같이 활용하는 것도 가능할 것이다

```sql
CREATE TABLE freshman AS SELECT * FROM undergraduate WHERE grade = 1; # 1학년 테이블
CREATE TABLE sophomore AS SELECT * FROM undergraduate WHERE grade = 2; # 2학년 테이블
CREATE TABLE junior AS SELECT * FROM undergraduate WHERE grade = 3; # 3학년 테이블
CREATE TABLE senior AS SELECT * FROM undergraduate WHERE grade = 4; # 4학년 테이블
```

## TRUNCATE 로 데이터 한 번에 날리기

때로는 기존 테이블의 데이터를 전부 다 삭제하고, 같은 테이블에서 다시 시작하고 싶을 수 있다.

이럴 때 물론 `DELETE` 문을 사용해도 되지만, `TRUNCATE` 문을 사용하는 방법이 있다.

DELETE 문 사용

```sql
DELETE * FROM 테이블명;
```

TRUNCATE 문 사용

```sql
TRUNCATE 테이블명;
```

테이블의 뼈대는 그대로 남아있지만 모든 row들이 삭제되는 것을 확인할 수 있다.

  </details>
</details>

<details>
  <summary>3) Foreign Key 제대로 사용하기</summary>

# Foreign Key 제대로 사용하기

## Foreign Key가 필요한 이유

Foreign Key란 한 테이블의 컬럼 중에서 **다른 테이블의 특정 row를 식별할 수 있는 컬럼**을 말한다. Foreign Key는 우리말로 **외래키**라고도 한다.

현재 강의에 대한 정보를 담고 있는 다음의 두 테이블이 있다.

### course 테이블

강의 정보들이 저장되어 있는 테이블

- id - INT NOT NULL AUTO_INCREMENT PRIMARY KEY
- title - 강의명. VARCHAR(30) NULL
- semester - 학기. VARCHAR(6) NULL
- maximum - 최대 수강인원. INT NULL
- professor - 교수명. VARCHAR(10) NULL

### review 테이블

강의 평가가 저장되어 있는 테이블

- id - INT NOT NULL AUTO_INCREMENT PRIMARY KEY
- course_id - course 테이블의 id 컬럼을 참조하는 Foreign Key. INT NULL
- star - 강의 평점. INT NULL
- comment - 강의리뷰. VARCHAR(500) NULL

현재 review 테이블의 course_id 컬럼은 course 테이블의 id 컬럼을 참조하고 있는 Foreign Key이다.

review 테이블 중에서 특정 row가 나타내는 강의평가가 **어느 수업에 대한 것인지**를 알려면

(1) review 테이블의 course_id 컬럼의 값을 보고

(2) course 테이블로 가서 그 값을 id 컬럼의 값으로 가진 row를 찾으면 된다.

이 경우 review 테이블의 course_id 라는 Foreign Key로 course 테이블의 Primary Key인 id 컬럼을 '참조'하고 있는 것이다.

이때 Foreign Key가 있는 review 테이블을 '자식 테이블(child table)'이나 '참조하는 테이블(referencing table)'이라고 하고,

Foreign Key에 의해 참조당하는 course 테이블을 '부모 테이블(parent table)', '참조 당하는 테이블(referenced table)'이라고 한다.

만약 DBMS 상에서 한 테이블의 컬럼을, '이것이 다른 테이블의 컬럼을 참조하는 Foreign Key다' 라고 설정해 놓으면 **'참조 무결성(Referential Integrity)'** 이라는 것을 지킬 수 있다.

'참조 무결성'이란 두 테이블 간에 참조 관계가 있을 때 각 데이터 간에 유지되어야 하는 정확성과 일관성을 의미한다. 'course_id 값이 3인 강의 평가들은 있는데 정작 course 테이블에는 id 값이 3인 수없이 없다?' 라는 건 참조 무결성이 훼손된 사례임

## Foreign Key 설정하기

Foreign Key는 참조 무결성을 지키기 위해서 필요하다.

하지만, 개념적으로 Foreign Key가 존재한다고 해서 참조 무결성이 지켜지는 것은 아니다.

이 컬럼이 Foreign Key다 라고 설정을 해 줘야만 참조 무결성을 지킬 수 있다.

### Foreign Key 설정 SQL 문

작성 양식

```sql
ALTER TABLE `데이터베이스명`.`자식테이블명`
ADD CONSTRAINT `ForeignKey_이름` # ADD 까지만 써줘도 실행이 되나, 그러면 Foreign Key 이름을 지정할 수 없다.
	FOREIGN KEY (`참조하는_컬럼명`)
	REFERENCES `데이터베이스명`.`부모테이블명` (`참조당하는_컬럼명`)
	ON DELETE RESTRICT
	ON UPDATE RESTRICT
```

Foreign Key 설정 또한 하나의 제약사항이기 때문에 그 이름을 정해줄 수 있다. ADD 뒤의 부분을 생략하면 자동으로 Foreign Key 설정의 이름이 정해진다.

ON DELETE 와 ON UPDATE 뒤에는 RESTRICT 뿐만 아니라, CASCADE, SET NULL, NO ACTION이 올 수 있다.

작성 예시

```sql
ALTER TABLE `course_rating`.`review`
ADD CONSTRAINT `fk_review_table`
	FOREIGN KEY (`course_id`)
	REFERENCES `course_rating`.`course` (`id`)
	ON DELETE RESTRICT
	ON UPDATE RESTRICT;
```

## SHOW CREATE TABLE 문으로 현재 테이블 어떻게 만들 수 있는지 보기

`SHOW CREATE TABLE` 문은 특정 테이블을 지금 바로 생성한다고 할 때 작성해야할 `CREATE TABLE` 문이 뭔지를 보여주는 유용한 SQL 문이다.

예를 들어, 위에 언급된 review 테이블을 만들고 Foreign Key 설정을 해준 뒤 `SHOW CREATE TABLE` 문을 실행하면 다음과 같은 결과가 나타난다.

```sql
CREATE TABLE `review` (
	`id` int NOT NULL AUTO_INCREMENT,
	`course_id` int DEFAULT NULL,
	`star` int DEFAULT NULL,
	`comment` varchar(500) DEFAULT NULL,
	PRIMARY KEY (`id`)
	KEY `fk_review_table_idx` (`course_id`),
	CONSTRAINT `kf_review_table` FOREIGN KEY (`course_id`) REFERENCES `course` (`id`) ON DELETE RESTRICT ON UPDATE RESTRICT
) ENGINE=InnnoDB AUTO_INCREMENT=37 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci
```

이 중 주목할 부분은 CONSTRAINT 가 포함되어 있는 줄이다. 이 부분을 보면 Foreign Key 설정에 관한 명령이 포함되어 있는 것을 알 수 있다.

이처럼, `CREATE TABLE` 문을 작성할 때부터 Foreign Key 설정을 해서 테이블을 처음에 만들 때부터 Foreign Key 설정을 해줄 수 있는 것이다.

## Foreign Key 로 보장되는 참조 무결성

참조하고 있는 부모 테이블의 컬럼에 존재하지 않는 값을 자식 테이블의 Foreign Key 컬럼에 추가하려고 하면 다음과 같은 형식으로 오류가 난다.

Error Code: 1452. Cannot add or update a child row:

a foreign key constraint fails (`course_rating`.`review`, CONSTRAINT .... )

이는 Foreign Key 제약사항을 만족시키지 못했기 때문에 자식 테이블에 행을 추가/갱신 할 수 없었다는 말이다.

이렇듯 Foreing Key 설정을 할 경우 자식 테이블의 Foreign Key에 추가하려는 값이 부모 테이블의 참조되는 컬럼에 없는 엉뚱한 값, 즉 참조 무결성을 해치는 경우를 방지할 수 있다. 예를 들면, 부모 테이블인 course 테이블에 존재하지 않는 수업에 대한 강의평가가 자식 테이블인 review 테이블에 추가될 수 없게 되는 것이다.

## 부모 테이블의 row가 삭제될 때

이번에는 참조 무결성을 부모 테이블인 course 테이블의 관점에서 생각해 보자.

만약 부모 테이블의 row가 삭제된다면, 그 row를 참조하던 자식 테이블의 row들은 어떻게 될까?

예를 들면, course 테이블에서 하나의 수업이 사라지면, review 테이블에 있는 그 수업에 대한 강의평가들은 어떻게 처리되는 것일까?

부모 테이블의 row가 삭제될 때 이를 참조하던 자식 테이블의 row들이 남아있는 경우 참조 무결성이 깨지게 되는데, 이러한 경우 어떻게 해야 하는지에 대한 정해진 답은 없다.

다만 이런 상황에서 자식 테이블의 row들을 어떻게 처리해야 할 지 사용자가 일종의 정책을 정할 수 있다.

크게 3가지 정책이 있다.

> 자신이 처한 상황에 적합한 정책을 사용할 수 있도록 각각의 정책을 확실하게 이해해야 한다.

### RESTRICT 정책

Foreign Key 제약에서 `ON DELETE` 가 RESTRICT 로 설정되어 있을 경우, 자신을 참조하고 있는 자식 테이블의 row가 하나라도 있는 부모 테이블의 row는 삭제될 수 없다. 삭제하려 할 경우 Foreing Key 제약사항을 위반하기 때문에 삭제할 수 없다는 오류가 나타난다.

만약에 삭제하고 싶다면, 그 row를 참조하고 있는 자식 테이블의 모든 row를 삭제한 후에야 가능한 것이다.

참고로 NO ACTION 정책은 RESTRICT와 같은 의미의 정책이다.

### CASCADE 정책

CASECADE 는 '폭포수처럼 떨어지다', '연쇄 작용을 일으키다' 라는 의미를 가지고 있다.

CASCADE 정책을 사용하면, 부모 테이블을 삭제할 때, 그것을 참조하고 있는 자식테이블의 row들도 함께 삭제된다.

CASCADE 정책을 사용할 때에는, 소중한 자료가 사라질 가능성을 내포하고 있음을 명심하고 사용해야 한다.

### SET NULL 정책

SET NULL 정책은 부모 테이블의 row 가 삭제되었을 때, 그 row를 참조하던 자식 테이블의 Foreign Key 컬럼의 값을 모두 NULL로 바꾸는 정책이다. 그렇게 되면 이 row들은 부모 잃은 row들이 된다.

부모 테이블의 row를 삭제하고 싶지만, 그것을 참조하던 자식 테이블의 row들을 남겨두고 싶다면 SET NULL 정책을 사용해야 한다.

## 부모 테이블의 row에서 참조 당하는 컬럼이 갱신될 때는?

부모 테이블의 row에서 참조 당하는 컬럼이 갱신될 때 사용하는 정책들 모두 의미가 똑같으며, `ON UPDATE` 에 적용한다.

### RESTRICT

부모 테이블 중 자식 테이블에 의해 참조 당하는 row의 참조 당하는 컬럼(예: id) 값을 갱신할 수 없으며, 변경하려고 Foreign Key 제약 사항 위반으로 할 경우 에러가 난다.

### CASCADE

부모 테이블 중 자식 테이블에 의해 참조 당하는 row들의 참조 당하는 컬럼 값을 변경할 경우, 이를 참조하던 자식 테이블의 Foreign Key 값도 그에 맞게 갱신된다.

### SET NULL

부모 테이블 중 자식 테이블에 의해 참조 당하는 row들의 참조 당하는 컬럼 값을 갱신할 경우, 이를 참조하던 자식 테이블의 Foreign Key 값은 NULL로 바뀐다.

정리하면, ON DELETE에서든 ON UPDATE 에서든 RESTRICT, CASCADE, SET NULL 정책이 가지는 의미는 동일하다.

그리고 ON DELETE와 ON UPDATE 각각에 서로 다른 정책을 설정할 수 있다.

## 논리적 Foreign Key, 물리적 Foreign Key

실무에서는 주문 테이블 - 배송 테이블, 회원 테이블 - 댓글 테이블, 부서 테이블 - 직원 테이블 처럼

많은 테이블들이 Foreign Key를 매개로 해서 관계를 맺고 있고, 여러 테이블들을 하나로 합치는 JOIN을 이 Foreign Key를 기준으로 하는 것이 일반적이기 때문에, 현재 데이터베이스에 존재하는 Foreign Key들을 잘 파악하는 것이 중요하다.

그런데 실무에서 데이터베이스 테이블을 살펴보다보면 **어떤 테이블의 특정 컬럼이 Foreign Key로 설정되어야 할 것 같은데 Foreign Key로 설정되지 않은 경우**를 보게 될 수도 있다.

어떤 테이블의 한 컬럼이 논리적으로 다른 테이블의 컬럼을 참조해야 해서 개념 상 Foreign Key에 해당하는 것과, 실제로 해당 컬럼을 Foreign Key로 설정해서 두 테이블 간의 참조 무결성을 지킬 수 있게 되는 것은 별개이다.

그래서 이 둘을 나누어서 개념상, 논리적으로 성립하는 Foreign Key를 **논리적(Logical) Foreign Key**라고 하고,

DBMS 상에서 실제로 특정 컬럼을 Foreign Key로 설정해서 두 테이블 간의 참조 무결성을 보장할 수 있게 됐을 때, 그 컬럼을 **물리적(Physical) Foreign Key**라고 한다.

데이터베이스에 들어갈 여러 테이블들을 설계하다 보면 당연히 여러 논리적 Foreign Key 들이 생길 수 밖에 없다. 하지만 실무에서는 논리적 Foreign Key라고 해서 꼭 그것을 물리적 Foreign Key로 설정하는 것은 아니다. 물리적 Foreign Key로 설정한다면 참조 무결성이 보장되니까 좋을텐데 왜 설정하지 않는 것일까?

### 1. 성능 문제

실제 서비스에 의해 사용되고 있는 데이터베이스의 테이블들은 단 1초 내에도 수많은 조회(SELECT), 갱신(UPDATE), 삭제(DELETE) 작업이 일어나고 있을 수 있다. 이럴 때 SQL 문 하나하나가 얼마나 빨리 실행되는지가 사용자의 만족도에 큰 영향을 미치게 될 것이다.

**물리적 Foreign Key가 있는 자식 테이블의 경우에는, INSERT, UPDATE 문 등이 실행될 때 약간의 속도 저하가 발생할 가능성이 있다.** 왜냐하면 INSERT, UPDATE 문이 실행될 때 혹시라도 참조 무결성을 깨뜨리는 변화가 발생하지는 않을 지 추가적으로 검증해줘야 하기 때문이다. 즉, 물리적 Foreign Key를 설정하게 되면, 데이터의 참조 무결성을 보장해주는 대신, 성능 부분에서는 약간의 양보가 필요한 것이다.

만약 데이터의 참조 무결성보다는 일단 당장 빠른 성능이 중요하다면 물리적 Foreign Key를 굳이 설정하지 않기도 한다. 그리고 이렇게 일단은 INSERT, UPDATE 문 등이 보다 더 빠르게 실행되도록 하고, 참조 무결성을 어기는 데이터들은 정기적으로 별도 확인 후에 삭제해주는 방식을 택하기도 한다.

### 2. 레거시(Legacy) 데이터의 참조 무결성이 이미 깨진 상태라면?

IT 세계에는 레거시(Legacy)라는 용어가 있다. '유물, 유산' 이라는 뜻을 가진 단어인데, IT 세계에서는 프로그램의 기존 코드, 기존 데이터 등을 나타낼 때 사용하는 말이다.

데이터베이스 쪽 분야에서는 레거시 데이터라는 말을 흔히 사용하는데, 어떤 회사에 개발자로 입사했을 때 이미 그 회사에 쌓여있던 데이터라고 생각하면 된다. 만약 이런 레거시 데이터들을 살펴봤는데 회사가 그 동안 물리적 Foreign Key 없이 데이터를 쌓아와서 참조 무결성을 어기는 row들이 생겨버린 상황이라고 해보자.

이런 경우에는 어떤 선택을 해야 할까? 일단 참조 무결성을 어기는 row들을 과감하게 지워버린 후에 물리적 Foreign Key를 설정하는 방법이 있을 것이다. 하지만 만약 참조 무결성을 어기는 row들의 수가 많고, 그것들도 소중한 데이터라서 함부로 삭제할 수 없는 상황이라면 어떻게 해야할까?

물론 이후부터는 참조 무결성을 지키면서 데이터를 저장하도록 할 수는 있다. 하지만 아무리 그 뒤로 참조 무결성을 지킨다고 해도 이미 레거시 데이터 때문에 전체적인 차원에서의 참조 무결성을 깨져버린 상태다.

바로 이런 현실적인 이유 때문에 그냥 물리적 Foreign Key 없이, 참조 무결성을 지키는 것을 포기하고 서비스를 운영하는 곳들도 생겨나게 된다. 참조 무결성이 깨지더라도 일단 소중한 데이터들을 삭제하지 말자는 생각인 것이다.

위에서 언급된 이유 등으로 인해 실무에서는 **논리적 Foreign Key를 굳이 물리적 Foreign Key로 설정하지 않는 경우도 많다.**

하지만 분명한 것은 데이터의 **참조 무결성(Referential Integrity)**를 완벽하게 지켜야 하는 서비스(은행, 학적 관리 서비스 등)에서는 논리적 Foreign Key를 반드시 물리적 Foreign Key로 설정해야 한다. 100%의 정확성이 요구되는 서비스에서 참조 무결성이 깨져버린다면 최악의 상황이 될 것이기 때문이다.

## Foreign Key를 삭제하는 방법

한 번 설정한 Foreign Key는 필요가 없어진 경우 삭제할 수도 있고, 삭제하고 다른 Foreign Key를 걸 수도 있다.

Foreign Key를 삭제하기 전에 우선 테이블에 어떤 Foreign Key가 있는지 확인해 볼 수 있다.

이전에 언급된 `SHOW CREATE TABLE` 문을 활용하면 된다. 이를 통해서 Foreign Key 제약사항의 이름을 확인하면 된다.

그리고 Foreign Key를 삭제하려면 이렇게 쓰면 된다.

```sql
ALTER TABLE 테이블명
	DROP FOREIGN KEY ForeignKey_이름;  # DROP CONSTRAINT ForeignKey_이름 으로 적어주어도 잘 삭제된다.
```

## 데이터베이스의 설계사항, 스키마

데이터베이스에 어떤 테이블들이 있고, 각 테이블의 컬럼 구조와 각 컬럼의 데이터 타입 및 속성이 어떻게 되고, 테이블 간의 관계는 어떻게 되는 지 등과 같은, **데이터베이스에 관한 모든 설계사항**을 스키마(Schema)라고 한다.

스키마는 실무에서 정말 자주 사용되는 용어 중 하나이다.

어떤 데이터베이스를 새롭게 구축해야할 때는 가장 처음 '스키마'를 짜야한다. 그리고 스키마를 짜는 것을 데이터베이스 모델링 또는 데이터베이스 디자인 이라고 한다.

데이터베이스라는 건 결국 첫 설계가 향후에 환경 변화에 맞춰 데이터베이스를 수정할 때 얼마나 더 유연하고 편리하게 할 수 있는지에 큰 영향을 미치게 된다. 즉, 처음부터 스키마를 잘 짜는 게 중요하다.

스키마에는 두 가지 종류가 있다.

### 개념적 스키마 (Conceptual Schema)

위에서 설명한 내용이 개념적 스키마에 해당하는 내용이다.

하나의 조직, 하나의 기관, 하나의 서비스 등에서 필요로 하는 데이터베이스 설계사항을 의미한다.

보통 스키마 라고 하면 이 개념적 스키마를 의미한다.

### 물리적 스키마 (Physical Schema)

물리적 스키마는 전혀 다른 의미의 스키마로, 데이터를 실제로 컴퓨터의 저장장치에 어떤 방식으로 저장할 지를 결정하는 스키마이다. 예를 들어, 만약 member 라는 테이블이 있고 그 안에 id, name, age 등의 컬럼이 있을 때 각 컬럼의 값들을 어떤 방식으로 저장할 지에 관한 설계사항이다. 그래서 물리적 스키마는 저장 스키마(Storage Schema), 내부 스키마(Internal Schema)라고도 한다.

사실 물리적 스키마는 일반 개발자나 사용자가 다룰 일이 업삳. **MySQL, Oracle과 같은 DBMS를 만드는 개발자들이 다루는 개념**이다. 똑같은 개념적 스키마라도 DBMS에 따라 그 물리적 스키마가 전혀 다를 수 있다. 같은 데이터라도 컴퓨터에 실제로 어떻게 저장할 지는 DBMS에 따라 다르기 때문이다. 바로 이 물리적 스키마 부분에서 각 DBMS의 장단점, 특성들이 드러나게 되는 것이다.

일반적으로는 스키마가 개념적 스키마를 의미한다는 것을 잘 기억하면 된다. 그런데 위의 스키마에 관한 내용은 모두 스키마에 관한 일반론적인 설명이다. 스키마라는 단어의 의미에 혼동을 주는 요소가 하나 있는데, 각 DBMS들의 사용 설명서를 읽어보면, 제각각 스키마라는 단어를 조금씩 다르게 사용하고 있다는 것이다.

일단 MySQL 에서는 스키마를 그냥 Database와 같은 의미로 혼용하고 있다.

Oracle에서 스키마는 하나의 사용자가 만든 각종 객체(테이블, 뷰 등)의 집합을 의미한다.

스키마라는 단어를 '데이터베이스 설계사항'으로 이해하고, 혹시라도 다른 의미로 사용되는 것 같은 경우에는 특정 DBMS에서만 가지는 의미가 아닐 지 한 번 직접 찾아보면 될 것이다.

## Foreign Key로 빠르게 파악하는 테이블 간의 관계

각 Foreign Key가 무슨 테이블에 있고, 어느 테이블의 어느 컬럼을 참조하는지를 파악하면 테이블 간의 관계, 나아가 데이터 저장 현황을 빠르게 파악할 수 있다.

만약 물리적 Foreign Key로 별도로 설정하지 않아서 논리적 Foreign Key만 존재하는 상황이라면 해당 데이터베이스의 스키마에 관한 문서, 도면, 파일 등을 참고하는 게 좋다. 비록 물리적 Foreign Key로 설정하지 않았더라도 논리적 Foreign Key는 스키마를 짜는 데이터베이스 모델링 단게에서 모두 고려되기 때문이다.

만약 이미 운영 중인 데이터베이스를 맡게 된다면 이런 Foreign Key들을 빨리 파악하는 것이 중요하다.

데이터베이스에 데이터가 어떤 식으로 저장되고 있는지 파악한다면, 그 후로는 데이터를 더 잘 저장하고 관리할 수 있을 것이다. 데이터를 조회 및 분석할 때 좋은 결과를 얻기 위해서는, 애초에 필요한 데이터를 잘 저장하고 관리할 수 있어야 한다.

</details>
