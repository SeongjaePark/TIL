본 정리 자료는 **코드잇에서 파이썬 모듈과 패키지 토픽**을 수강하며 배운 지식을 정리한 내용입니다.

[코드잇 파이썬 모듈과 패키지 토픽](https://www.codeit.kr/courses/python-intermediate/topics/python-module-and-package)

<details>
  <summary>1. 모듈</summary>

# 모듈

## 모듈이란?

모듈은 여러 기능을 모아둔 파이썬 파일이다.

만약 프로그램의 모든 기능을 한 파일에 모아 두게 되면, 어떤 부분이 어떤 역할을 하는지, 기능을 수정하고 싶으면 어떤 부분을 바꿔야 하는지 알기가 힘들다.

그래서 프로그램을 짤 때는 코드를 파일 단위 (모듈)로 나누어 주는 게 좋다.

파이썬에서는 이런 파일 하나를 모듈이라고 한다.

이렇게 코드를 모듈화시키면

(1) 한 파일에서 구현하고자 하는 게 명확해져서 코드를 짜고 관리하기가 쉬워짐

(2) 코드를 재사용할 수 있음

예를 들어, 평면도형의 면적을 구해 주는 함수들을 모아서 area 라는 모듈을 만들 수 있다.

area.py

```python
PI = 3.14

# 원의 면적을 구해 주는 함수
def circle(radius):
	return PI * radius * radius

# 정사각형의 먼적을 구해 주는 함수
def square(length):
	return length * length
```

모듈은 파일 이름에서 .py 확장자를 빼고 부른다.

## 모듈 임포트 (import)

모듈에 저장된 기능을 가져다 쓰기 위해서는 모듈을 임포트(import) 하면 된다. 모듈을 임포트하는 방법은 여러 가지가 있다.

### `import <module>`

모듈 전체를 임포트한다. 모듈 안에 있는 변수 또는 함수는 . 으로 접근할 수 있다.

run.py

```python
import area

print(area.square(2)) # 4
print(area.PI) # 3.14
```

### `from <module> import <member(s)>`

모듈에서 필요한 것들만 임포트한다. 불러온 변수나 함수를 접근할 때 앞에 module. 을 붙이지 않는다.

run.py

```python
from area import square, PI

print(square(3)) # 9
print(PI) # 3.14
```

### `from <module> import *`

모듈에서 모든 걸 임포트한다.

run.py

```python
from area import *

print(PI) # 3.14
print(square(4)) # 16
```

그런데 이 임포트 방식을 사용하면 어떤 함수가 어떤 모듈에서 왔는지 알 수가 없고, 자신도 모르게 쓸데없는 것들을 가져올 수 있다.

그래서 이 방식은 **파이썬 커뮤니티에서 권장하지 않는** 방식이다. 모듈을 사용할 때는 모듈을 그대로 가져오거나 모듈에서 필요한 것들만 가져오는 것이 추천된다.

### `as` 키워드

임포트 문 뒤에 `as` 라는 키워드(특별한 의미를 가지고 있는, 이미 예약된 문자열)를 붙여서 임포트하는 것의 이름을 바꿔줄 수 있다.

run.py

```python
# 모듈 이름을 바꿈
import area as ar
print(ar.square(5)) # 25

# 함수 이름을 바꿈
from area import square as sq
print(sq(3)) 9
```

## 모듈과 클래스

모듈에는 변수와 함수 뿐만 아니라, 클래스가 있는 경우도 많다.

예를 들어 어떤 프로그램에서는 원과 정사각형의 면적만 계산해야 하는 게 아니라 원과 정사각형을 직접 만들어서 사용해야 한다. 그러면 새로운 파일을 만들고 그 파일에서 원과 정사각형 클래스들을 정의해 주면 된다.

shapes2d.py

```python
# 원 클래스
class Circle:
	def __init__(self, radius):
		self.radius = radius

	def area(self):
		return 3.14 * self.radius

# 정사각형 클래스
class Square:
	def __init__(self, length):
		self.length = length

	def area(self):
		return self.length * self.length
```

그리고 다른 파일에서 이 클래스들을 사용하려면 이전과 같이 `import` 키워드를 사용하면 된다.

run.py

```python
import shapes2d

circle = shapes2d.Circle(2)
print(circle.area()) # 12.56

from shapes2d import Square

square = Square(3)
print(square.area()) # 9
```

물론 `as` 키워드를 사용해서 임포트하는 것의 이름을 바꿔줄 수도 있다.

run.py

```python
from shapes2d import Square as Sq

square = Sq(3)
print(square.area()) # 9
```

## 현재 파일에서 사용 가능한 기능은?

### 네임 스페이스

네임 스페이스는 파일에서 정의된 모든 이름들을 뜻한다.

`dir()` 함수는 파일의 네임스페이스를 리턴해준다.

### 모듈 안에 정의된 이름들 확인

`print(dir(area))`

area 모듈 안에 정의된 이름들을 확인할 수 있다.

### 모듈 임포트

```python
import area
print(dir())
```

이 경우 네임 스페이스에 area 라는 모듈명만 추가된다. (모듈 안에 정의된 변수나 함수는 추가 x)

```python
import area as ar
print(dir())
```

이 경우 네임 스페이스에 area 대신 ar 이 추가된다.

### 모듈의 함수 임포트

```python
from area import circle, square
print(dir())
```

이 경우 네임 스페이에 circle 함수와 square 함수가 추가된다.

### 여러 번 정의된 함수 호출

파이썬에서는 한 파일에서 같은 이름으로 여러 번 정의된 함수를 호출하면 가장 나중에 정의된 함수가 호출된다.

```python
from area import square, circle

def square(length):
	return 4 * length

print(square(3)) # 12

```

이름이 중복되면 이름이 어떤 함수를 참조 하는지 가 알기 힘들다. 그래서 한 네임 스페이스 안에는 같은 이름이 중복되지 않는 게 좋다.

이름이 중복되지 않게 하려면

```python
import area

def square(length):
	return 4 * length

print(area.square(3)) # 9
print(square(3)) # 12
```

이처럼 모듈 자체를 임포트하여 사용하는 방법이 있고,

```python
from area import square as sq

def square(length):
	return 4 * length

print(sq(3)) # 9
print(square(3)) # 12
```

이처럼 `as` 키워드를 사용하여 이름을 다른 것으로 바꿔주는 방법이 있다.

## 스탠다드 라이브러리

모듈은 여러 가지 기능을 정리해 둔 파이썬 파일이다.

파이썬에서는 개발자들이 많이 쓸법한 기능들이 이미 모듈로 만들어져 있다.

우리가 파이썬을 설치하면 스탠다드 라이브러리가 딸려온다. 스탠다드 라이브러리에는 다음과 같은 것들이 포함되어 있다.

- int, float, string 같은 자료형
- print, dir 같은 내장 함수
- 유용한 기능을 제공하는 모듈들 (스탠다드 모듈)

## 유용한 스탠다드 모듈들

  <details>
    <summary>스탠다드 모듈</summary>

### math

math는 기본적인 수학 모듈이다. 여러 수학적인 함수를 제공해준다.

```python
import math

# 코사인 함수 (모든 삼각함수는 라디안을 사용한다)
print(math.cos(0)) # 1.0

# 로그 함수
print(math.log10(100)) # 2.0
```

### random

random 모듈은 임의의 숫자를 생성하기 위한 다양한 함수들을 제공해 준다.

```python
import random

# 임의의 정수 1 <= N <= 20
print(random.randint(1, 20))

# 임의의 소수 0 <= x <= 1
print(random.uniform(0, 1))

```

### datetime

datetime 모듈은 날짜와 시간을 다루기 위한 다양한 클래스를 갖추고 있다.

```python
import datetime

# 현재 시간과 날짜
today = datetime.datetime.now()
print(today) # 2020-10-14 14:13:31.028298

# 출력값을 "요일, 월 일 연도"로 포매팅
print(today.strftime("%A, %B, %dth %Y")) # Wednesday, October, 14th 2020

# 특정 시간과 날짜
pi_day = datetime.datetime(2020, 3, 14, 13, 6, 15)
print(pi_day) # 2020-03-14 13:06:15

# 두 datetime의 차이
print(today - pi_day) # 214 days, 1:07:16.028298
```

### OS

OS는 Operating System, 즉 운영채제의 약자다. os 모듈을 통해서 파이썬으로 운영체제를 조작하거나 운영체제에 대한 정보를 가져올 수 있다.

```python
import os

# 현재 어떤 계정으로 로그인 돼있는지 확인
print(os.getlogin())

# 현재 파일의 디렉토리 확인
print(os.getcwd())

# 현재 프로세스 ID 확인
print(os.getpid())
```

### os.path

os.path 모듈은 파일 경로를 다룰 때 쓰인다.

```python
import os.path

# 프로젝트 디렉토리 경로 'Users/@@@/PycharmProjects/stadard_moduels'
# 현재 파일 경로 'Users/@@@/PycharmProjects/standard_moduels/main.py'

# 주어진 경로를 절대 경로로
print(os.path.abspath('..'))
# /Users/@@@/PycharmProjects

# 주어진 경로를 현재 디렉토리를 기준으로 한 상대 경로로
print(os.path.relpath('/Users/@@@/PycharmProjects'))
# ..

# 주어진 경로들을 병합
print(os.path.join('Users/@@@/PycharmProjects', 'standard_moduels'))
# Users/@@@/PycharmProjects/standard_moduels

```

### re

프로그래밍에서 Regular Expression (RegEx, re, 한국어로는 정규 표현식) 은 특정한 규칙/패턴을 가진 문자열을 표현하는 데 사용된다.

```python
import re

# 알파벳으로 구성된 단어들만 매칭
pattern = re.compile('^[A-Za-z]+$')
print(pattern.match('I'))  # <re.Match object; span=(0, 1), match='I'>
print(pattern.match('love')) # <re.Match object; span=(0, 4), match='love'>
print(pattern.match('python3')) # None

# 숫자가 포함된 단어들만 매칭
pattern = re.compile('.*\d+')
print(pattern.match('I'))  # None
print(pattern.match('love')) # None
print(pattern.match('python3')) # <re.Match object; span=(0, 7), match='python3'>

```

### pickle

pickle 을 사용하면 파이썬 오브젝트(객체)를 바이트(byte) 형식으로 바꿔서 파일에 저장할 수 있고, 저장된 오브젝트를 읽어올 수도 있다.

```python
import pickle

# 딕셔너리 오브젝트
obj = {'my': 'dictionary'}

# obj를 filename.pickle 파일에 저장
with open('filename.pickle', 'wb') as f:
	pickle.dump(obj, f)

# filename.pickle에 있는 오브젝트를 읽어옴
with open('filename.pickle', 'rb') as f:
	obj = pickle.load(f)

print(obj)
# {'my': 'dictionary'}

```

### json

json 모듈은 pickle 과 비슷하지만 오브젝트를 JSON 형식으로 바꿔준다.

JSON 형식에 맞는 데이터 (기본 데이터 타입들, 리스트, 딕셔너리)만 바꿀 수 있다.

```python
import json

# 딕셔너리 오브젝트
obj = {'my': 'dictionary'}

# obj를 filename.json 파일에 저장
with open('filename.json', 'w') as f:
    json.dump(obj, f)

# filename.json에 있는 오브젝트를 읽어옴
with open('filename.json', 'r') as f:
    obj = json.load(f)

print(obj)
# {'my': 'dictionary'}
```

### copy

copy 모듈은 파이썬 오브젝트를 복사할 때 쓰인다.

```python
# 리스트를 복사하려면 슬라이싱을 사용하거나 copy.copy() 함수를 사용해야 함
a = [1, 2, 3]
b = a
c = a[:]
d = copy.copy(a)
a[0] = 4
print(a, b, c, d)
# [4, 2, 3] [4, 2, 3] [1, 2, 3] [1, 2, 3]

# 하지만 오브젝트 안에 오브젝트가 있는 경우 copy.copy() 함수는 가장 바깥에 있는 오브젝트만 복사함
# 오브젝트를 재귀적으로 복사하려면 copy.deepcopy() 함수를 사용해야 함
a = [[1,2,3], [4,5,6], [7,8,9]]
b = copy.copy(a)
c = copy.deepcopy(a)
a[0][0] = 4
print(a)
# [[4, 2, 3], [4, 5, 6], [7, 8, 9]]
print(b)
# [[4, 2, 3], [4, 5, 6], [7, 8, 9]]
print(c)
# [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

### sqlite3

sqlite3 모듈을 통해 파이썬에서 SQLite 데이터베이스를 사용할 수 있다.

```python
import sqlite3

# 데이터베이스 연결
conn = sqlite3.connect('example.db')

# SQL 문 실행
c = conn.cursor()
c.execute('''SELECT ... FROM ... WHERE ... ''')

# 가져온 데이터를 파이썬에서 사용
rows = c.fetchall()
for row in rows:
	print(row)

# 연결 종료
conn.close()

```

  </details>

## 파이썬의 모듈 검색 경로

파이썬은 어떻게 모듈의 이름만 보고 모듈을 찾아오는 것일까?

파이썬은 임포트하려는 모듈을 찾기 위해서 특정 경로들을 살핀다.

이 경로들은 `sys` 라는 스탠다드 모듈을 통해 확인해볼 수 있다.

```python
import sys

print(sys.path)
```

sys 모듈에는 파이썬의 실행 환경과 관련된 변수들과 함수들이 저장되어 있다.

이 중에 path에는 파이썬이 모듈을 찾기 위해 검색해보는 경로들이 저장되어 있다.

파이썬은 모듈 검색 경로 리스트에 있는 경로들을 순서대로 살펴 본 후, 만약 결국 모듈을 찾지 못하면 모듈을 찾을 수 없다는 에러를 낸다.

sys.path 첫번째 경로는 항상 실행한 파일이 있는 디렉토리다.

sys.path의 마지막 경로에는 site-packages 라고 하는 디렉토리가 있다. 외부 패키지들은 일반적으로 이 폴더에 저장된다.

## 모듈 검색 경로에 새로운 경로 추가하기

### sys.path에 .append()로 경로 임시 추가

첫 번째 방법은 sys.path에 새로운 경로를 직접 추가하는 것이다. sys.path는 결국 리스트이기 때문에 `.append()` 메소드를 써서 쉽게 새로운 경로를 추가할 수 있다.

예를 들어, sys.path에 바탕화면의 경로를 추가하고 싶다면 아래와 같은 코드를 추가해 주면 된다.

```python
import sys
sys.path.append('Users/@@@/Desktop') # macOS
sys.path.append('C:\\Users\\codeit\\Desktop') # Windows
```

윈도우스의 경로 같은 경우 역슬래쉬를 2개 써준다. 프로그램잉에는 `\<char>` 패턴을 가진 특수 문자들이 있다. 예를 들어 `\t` 는 탭을 뜻하고 `\n` 은 새로운 줄을 뜻한다.

윈도우스 파일 경로는 `\` 가 들어가기 때문에 `\` 와 다음 문자가 특수 문자로 인식 될 수 있기 때문에, 윈도우스 파일 경로를 다룰 때는 `\` 를 뜻하는 특수 문자, `\\`를 사용해야 한다.

### sys.path에 영구적으로 경로 추가

sys.path에 어떤 경로를 `.append()` 해 주면 프로그램이 종료되면 그 경로는 sys.path에서 사라진다. 그 경로에 있는 모듈을 쓰고 싶으면 매번 `.append()`를 해 줘야 한다.

만약 어떤 경로를 영구적으로 sys.path에 추가하려면 자신이 쓰는 IDE(예: Pycharm)의 환경 설정에 가서 Interpreter의 파일 경로에 원하는 파일 경로를 추가해 줘야 한다.

## 스크립트 VS 모듈

### 스크립트

프로그램을 작동시키는 코드를 담은 **실행 용도**의 파일

run.py

```python
import area

x = float(input('원의 반지름을 입력해 주세요: '))
print('반지름이 {}인 원의 면적인 {}입니다.\n'.format(x, area.circle(x))

y = float(input('정사각형의 변의 길이를 입력해 주세요: '))
print('변의 길이가 {}인 정사각형의 면적은 {}입니다.'.foramt(y, area.square(y))
```

### 모듈

프로그램에 필요한 변수들이나 함수들을 정의해 놓은 파일

앞서 만들어 놓은 [area.py](http://area.py) 와 같은 파일이 해당된다.

## 모듈을 스크립트로 사용해 보기

스크립트와 모듈은 서로 용도가 다른 파일이지만, 그 안에 어떤 내용을 담을 지 정한 것 뿐, 파일 자체에는 차이가 없다.

모듈 파일도 안에 테스트 코드를 넣고 실행할 수 있다.

area.py

```python
PI = 3.14

def circle(radius):
	return PI * radius * radius

def square(length):
	reutrn length * length

print(circle(2) == 12.56) # True
print(circle(5) == 78.4) # True
print(square(2) == 4) # True
print(square(5) == 25) # True
```

이처럼 area 파일을 함수들을 테스트해 주는 스크립트로 사용할 수도 있다.

하지만 안에 테스트 코드가 포함 된 모듈을 스크립트에서 임포트해서 사용하게 되면, 모듈에 포함된 테스트 코드가 그대로 실행된다는 문제가 생긴다.

모듈을 그대로 임포트하게 되면 모듈 안에 포함된 모든 코드가 실행되기 때문이다.

이 문제를 해결하기 위해서 `__name__` 이라는 특수 변수를 사용해야 한다.

### 던더 name 특수 변수

`__name__` 은 모듈의 이름을 저장해 놓은 변수이다.

`__name__` 의 값은 파이썬이 알아서 정해 주는데,

- 파일을 직접 실행하면 `__name__` 은 `__main__` 으로 설정된다.
- 파일을 임포트하면 `__name__` 은 모듈 이름으로 설정된다.

예를 들어 area 파일에서 `__name__`을 아래처럼 출력해 보면

area.py

```python
print(__name__)
```

area 파일을 직접 실행할 경우 `__main__` 이라고 나오고,

area 파일을 임포트할 경우 area 라고 나온다.

### `if __name__ == '__main__'`

`__name__` 을 사용하면 파일일 직접 실행되냐 아니면 임포트되냐에 따라서 코드의 흐름을 제어할 수 있다.

파일이 직접 실행될 때만 실행하고 싶은 코드는 `if __name__ == '__main__'` 이라는 조건문 안에 넣어주면 된다.

area.py

```python
PI = 3.14

# 원의 면적을 구해 주는 함수
def circle(radius):
	return PI * radius * radius

# 정사각형의 면적을 구해 주는 함수
def square(length):
	return length * length

if __name__ == '__main__':
	# circle 함수 테스트
	print(circle(2) == 12.56)
	print(circle(5) == 78.4)
```

area 파일을 직접 실행시키게 되면 파일의 `__name__` 은 `__main__`이 되기 때문에 조건문 안에 있는 코드가 실행되지만 area 파일을 임포트하면 `__name__` 은 area 가 되기 때문에 조건문 안에 있는 코드가 실행되지 않는다.

이처럼 `__name__` 특수 변수를 이용하면 같은 파일을 모듈처럼 쓸 수도 있고, 스크립트처럼 쓸 수도 있다.

## `main()` 함수

파이썬에서는 모든 파일을 실행할 수 있다. 파일을 실행하면 파일에 있는 모든 코드가 처음부터 끝까지 실행된다.

하지만 Java나 C, C++ 같은 언어들은 그렇지 않다. Java나 C, C++ 같은 언어들에서는 어떤 파일을 실행하기 보다는 파일 안에 있는 `main()` 이라는 함수를 실행한다. `main` 함수는 말 그대로 '주요' 함수로서 프로그램을 작동시키는 코드를 담고 있다.

예를 들어 Java의 `Hello World!` 프로그램은 아래와 같이 생겼다.

HelloWorld.java

```java
class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

프로그램이 더 복잡해지면 `main` 함수 안에서 다른 함수들을 호출할 것이다.

파이썬에서도 이 프로그래밍 패턴을 사용할 수 있다. 파일에서 어떤 프로그램을 작동시키는 부분을 그냥 `main` 이라는 함수 안에 넣어 주면 된다.

예를 들어 area 파일과 run 파일에 `main` 함수를 추가해 주면 아래와 같이 바뀐다.

area.py

```java
PI = 3.14

# 원의 면적을 구해 주는 함수
def circle(radius):
      return PI * radius * radius

# 정사각형의 면적을 구해 주는 함수
def square(length):
      return length * length

# 함수들을 테스팅 하는 메인 함수
def main():
      # circle 함수 테스트
      print(circle(2) == 12.56)
      print(circle(5) == 78.4)

      # square 함수 테스트
      print(square(2) == 4)
      print(square(5) == 25)

if __name__ == '__main__':
    main()
```

run.py

```java
import area

# 면적 계산기 프로그램
def main():
        x = float(input('원의 지름을 입력해 주세요: '))
        print('지름이 {}인 원의 면적은 {}입니다.\n'.format(x, area.circle(x)))

        y = float(input('정사각형의 변의 길이를 입력해 주세요: '))
        print('변의 길이가 {}인 정사각형의 면적은 {}입니다.'.format(y, area.square(y)))

if __name__ == '__main__':
    main()
```

`if __name__ == '__main__'` 안에 있는 코드는 파일이 직접 실행될 때만 실행되니까 그 안에서 `main` 함수를 호출해 주면 된다.

이렇게 `main` 함수를 사용하면 파일에서 프로그램을 작동시키는 코드가 어디 있는지 쉽게 알 수 있기 때문에 코드의 가독성이 올라간다. 코드의 흐름과 의도를 더 쉽게 이해할 수 있는 것이다.

따라서 파이썬에서는 `main` 함수가 요구되지 않더라도 `if __name__ == '__main__'` 과 `main()` 을 사용하는 것이 추천된다.

</details>

<details>
  <summary>2. 패키지</summary>

# 패키지

## 패키지란?

패키지는 모듈들을 모아 놓은 디렉토리를 뜻한다.

예를 들어 평면 도형의 면적을 구해 주는 area 모듈과, 입체 도형의 부피를 구해 주는 volume 모듈을 모아서 shapes 패키지를 만들었다고 하자. shapes 패키지의 구조는 다래와 같다.

```
shapes/
    __init__.py
    area.py
    volume.py
```

shapes/area.py

```python
PI = 3.14

# 원의 면적을 구해 주는 함수
def circle(radius):
    return PI * radius * radius

# 정사각형의 면적을 구해 주는 함수
def square(length):
    return length * length
```

shapes/volume.py

```python
PI = 3.14

# 구의 부피를 구해 주는 함수
def sphere(radius):
    return (4/3) * PI * radius * radius * radius

# 정육면체의 부피를 구해 주는 함수
def cube(length):
    return length * length * length
```

패키지는 일반 디렉토리와 똑같은데 안에 `__init__.py` 라는 파일이 있다.

### 패키지 임포트

모듈과 비슷하게 패키지 안에 있는 내용을 가져올 때도 `import` 키워드를 사용한다.

### `import <package.module>`

run.py

```python
import shapes.volume

print(shapes.volume.cube(3))
```

이렇게 패키지 안에 있는 모듈을 가져올 수 있다.

패키지나 모듈 안에 있는 것은 항상 . 을 이용해서 접근한다.

### `import <package>`

run.py

```python
import shapes

print(shapes.volume.cube(3)) # 오류
```

이렇게 패키지 자체를 임포트할 수도 있는데, 그러면 **패키지 안에 있는 내용들은 임포트되지 않는다** (패키지 안에 있는 모듈도 같이 임포트하려면 패키지의 init 파일을 활용해야 한다). 그래서 위 코드는 오류가 난다.

참고로 `import ...` 방식을 써서는 모듈의 함수나 변수를 바로 가져올 수 없다.

run.py

```python
import shapes.volume.cube # 오류
```

`import ...` 방식으로는 패키지나 모듈만 임포트할 수 있다.

### `from <package> import <module(s)>`

run.py

```python
from shapes import volume
print(volume.cube(3))
```

`from ... import ...` 방식도 패키지에 쓸 수 있다. 패키지 안의 모듈을 바로 가져올 수도 있고

### `from <package.module> import <member(s)>`

모듈 안에 있는 변수나 함수를 가져올 수도 있다.

run.py

```python
from shapes.volume import cube

print(cube(3))
```

### `as` 키워드

그리고 임포트 문 뒤에 `as` 키워드를 써서 임포트하는 것의 이름을 바꿔줄 수 있다.

run.py

```python
import shapes.volume as vol

print(vol.cube(3))
```

## `__init__` 파일

### shapes 패키지의 구조

```
shapes/
    __init__.py
    area.py
    volume.py
```

shapes/area.py

```python
PI = 3.14

# 원의 면적을 구해 주는 함수
def circle(radius):
    return PI * radius * radius

# 정사각형의 면적을 구해 주는 함수
def square(length):
    return length * length
```

shapes.volume.py

```python
PI = 3.14

# 구의 부피를 구해 주는 함수
def sphere(radius):
    return (4/3) * PI * radius * radius * radius

# 정육면체의 부피를 구해 주는 함수
def cube(length):
    return length * length * length
```

### `__init__` 파일이란?

패키지 안에는 `__init__.py` 라는 파일이 있다. init 파일은 '이 폴더는 파이썬 패키지다' 라고 말해주는 파일이다.

파이썬 3.3 이전 버전에서는 init 파일이 필수였다. 디렉토리 안에 init 파일이 없으면 디렉토리가 패키지로 인식되지 않아서 패키지를 임포트할 수 없었다.

파이썬 3.3 이후 버전부터는 init 파일이 필수가 아니게 됐지만 파이썬 하위 버젼과의 호환성과 패키지의 명확성을 위해 항상 패키지 안에 init 파일을 만들어 주는 것이 권장된다.

init은 initialize 를 줄인 것인데, 이 단어는 초기화를 뜻한다. 우리가 처음으로 패키지나 패키지 안에 있는 어떤 것을 임포트하면 가장 먼저 패키지의 init 파일에 있는 코드가 실행된다.

### `__init__` 파일에서 임포트 사용하기

패키지를 임포트하면 기본적으로 패키지 안에 있는 내용은 임포트되지 않는다. 패키지를 임포트할 때 패키지 안에 있는 내용도 함께 임포트하고 싶다면 init 파일을 활용해야 한다.

init 파일에 패키지와 함께 임포트하고 싶은 것들을 써 주면 된다.

shapes/**init**.py

```python
from shapes import area, volume`
```

그러면 이제 shapes 패키지를 임포트하면 area와 volume 모듈도 임포트 된다. init 파일에서 임포트하는 것은 패키지 안으로 임포트된다고 생각하면 된다. 이렇게 임포트된 area와 volume 모듈은 아래와 같이 접근할 수 있다.

run.py

```python
import shapes

print(shapes.area.circle(2))
print(shapes.volume.sphere(2))
```

그리고 모듈 대신 모듈의 함수들을 직접 임포트할 수도 있다.

`shapes/__init__.py`

```python
from shapes.area import circle, square
```

그러면 이 함수들을 아래와 같이 접근할 수 있다.

run.py

```python
import shapes

print(shapes.circle(2))
print(shapes.square(3))
```

shapes 패키지 안에서 함수들을 직접 가져왔기 때문에 area를 건너뛸 수 있는 것이다. init 파일에서 임포트 되는 것은 항상 package. 으로 접근할 수 있다. 위 처럼 호출 방식을 바꿔주는 것은 유용하게 쓰일 때도 있다.

### `__init__ 파일에서 변수 정의하기`

상수값 PI는 area 모듈에서도 쓰이고 volume 모듈에서도 쓰인다. PI처럼 패키지에 있는 여러 모듈이 필요로 하는 것들은 각 모듈에서 정의하지 않고 패키지 안에서 한 번만 정의해 주는 게 좋다. 똑같은 걸 여러 번 정의하는 건 비효율적이고 실수로 하나를 잘못 정의하면 프로그램에 오류가 나기 때문이다.

PI를 패키지 안에서 한 번만 정의해 주려면 (즉, 패키지 레벨에서 정의해 주려면) PI를 shapes 패키지의 init 파일에서 정의해 주면 된다.

`shapes/__init__.py`

```python
PI = 3.14
```

그리고 패키지 안에 있는 모듈에서는 PI를 임포트하면 된다.

shapes/area.py

```python
from shapes import PI
...
```

shapes/volume.py

```python
from shapes import PI
...
```

PI 같은 상수뿐만이 아니라 여러 모듈에서 필요한 변수, 함수 또는 객체는 패키지의 init 파일에서 정의해 주는 게 좋다.

그리고 패키지의 init 파일에서 정의되는 것들은 패키지 밖에서도 사용할 수 있다.

run.py

```python
# 1) PI 직접 임포트
from shapes import PI
PI

# 2) 패키지 임포트 후 shapes. 으로 접근
import shapes
shapes.PI
```

## `__all__` 특수 변수

### `import *`

모듈을 임포트할 때 `from <module> import *` 를 하면 모듈의 모든 내용이 임포트 된다.

하지만 모듈 대신 패키지에 `from <package> import *` 를 하면 패키지 안에 있는 게 아무것도 임포트 되지 않는다.

### `__all__` 특수 변수

`__all__` 특수 변수는 우리가 `import *` 를 했을 때 임포트 대상에서 어떤 것들을 가져와야 하는지를 정해 주는 변수이다. 임포트 대상에서 내용 전체를 가져오라고 했을 때, '전체' 가 무엇인지 정의해 주는 것이다. `__all__`은 모듈에도 적용되고 패키지에도 적용된다.

### `__all__` 과 모듈

모듈의 `__all__` 은 모듈에 해당하는 파일에서 정의한다. 예를 들어 area.py에 아래와 같은 코드를 추가해 주면:

shapes/area.py

```python
# __all__ 정의
__all__ = ['circle', 'square']

...
```

`from shapes.area import *` 를 했을 때 area 모듈의 모든 내용이 임포트 되지 않고 circle과 square 함수만 임포트 된다.

### `__all__` 과 패키지

패키지의 `__all__`은 패키지에 해당하는 init 파일에서 정의한다. 예를 들어 shapes 패키지의 init 파일에 아래와 같은 코드를 추가해 주면:

`shapes/__init__.py`

```python
# __all__ 정의
__all__ = ['area', 'volume']
```

이제 `from shapes import *` 를 하면 area 모듈과 volume 모듈이 임포트 된다.

`__all__` 을 사용하면 패키지나 모듈에 `import *` 를 했을 때 어떤 것들이 임포트 되는지를 제어할 수 있다.

그래도 여전히 `import *` 만 봐서는 정확히 어떤 것들이 임포트 되는지를 알 수 없기 때문에 `import *` 는 프로그램에서 정의되는 이름들, 즉 네임스페이스를 완벽히 이해하고 있을 때만 사용하는 것이 추천된다.

## 서브 패키지

### 서브 패키지란?

패키지 안에는 모듈도 있을 수 있고 다른 패키지들이 있을 수도 있다.

패키지 안에 또 다른 패키지가 있을 때, 안에 있는 패키지를 **서브패키지**라고 한다.

### mymath 패키지 구조

```
mymath/
    shapes/
        __init__.py
        area.py
        volume.py
    stats/
        __init__.py
        average.py
        spread.py
```

mymath/shapes/area.py

```python
PI = 3.14

# 원의 면적을 구해 주는 함수
def circle(radius):
    return PI * radius * radius

# 정사각형의 면적을 구해 주는 함수
def square(length):
    return length * length
```

mymath/shapes/volume.py

```python
PI = 3.14

# 구의 부피를 구해 주는 함수
def sphere(radius):
    return (4/3) * PI * radius * radius * radius

# 정육면체의 부피를 구해 주는 함수
def cube(length):
    return length * length * length
```

mymath/stats/average.py

```python
# 데이터의 평균을 구해 주는 함수
def data_mean(data):
    return sum(data) / len(data)

# 데이터의 중앙값을 구해 주는 함수
def data_median(data):
    data.sort()
    n = len(data)
    if n % 2 == 0:
        # 데이터 개수가 짝수면 중앙에 위치한 두 값의 평군을 구함
        # [a, b, c, d, e, f] -> median = (c+d) / 2
        return (data[n/2] + data[(n/2)-1]) / 2
    else:
        # [a, b, c, d, e] -> median = c
        return data[(n-1)/2]
```

myath/stats/spread.py

```python
# 데이터의 범위를 구해 주는 함수
def data_range(data):
    return max(data) - min(data)
```

shapes 패키지와 stats 패키지는 서브패키지라고 할 수 있다.

서브패키지도 결국 패키지이기 때문에 지금까지 익힌 임포트 방식들을 사용하면 된다.

### 임포트 총정리

### `import ...`

run.py

```python
# 패키지 임포트
import mymath

# 서브패키지 임포트
import mymath.shapes

# 모듈 임포트
import mymath.shapes.area

# 모듈 안에 있는 변수나 함수는 이 방식으로 임포트 할 수 없음
import mymath.shapes.area.circle # 오류
```

그냥 `import` 뒤에 가져오고 싶은 모듈이나 패키지를 써 주면 된다. 하지만 모듈 안에 있는 변수나 함수는 이 방식으로 임포트할 수 없다.

그리고 (서브)패키지를 임포트할 때는 패키지와 같이 임포트하고 싶은 걸 피키지의 init 파일에 적어줘야 한다.

### `from ... import ...`

run.py

```python
# 패키지 안에 있는 패키지 임포트
from mymath import shapes

# 패키지 안에 있는 모듈 임포트
from mymath.shapes import area

# 모듈 안에 있는 함수 임포트
from mymath.shapes.aera import circle

# 임포트 뒤에는 . 을 쓸 수 없음
from mymath import shapes.area # 오류
```

`from` 뒤에는 모듈이나 패키지가 올 수 있다. `import` 뒤에는 모듈이나 패키지 안에서 가져오고 싶은 걸 써준다. `import` 뒤에는 . 을 쓸 수 없다.

### `as` 키워드

항상 임포트 문 뒤에 `as` 키워드를 써서 임포트하는 것의 이름을 바꿔 줄 수 있다.

## 상대 경로 임포트

mymath 패키지의 구조와 그 안의 (서브 패키지 안의) 모듈들의 코드는 앞서 표기된 것과 동일하다.

임포트를 하는 곳의 위치를 기준으로 임포트 하려는 것의 위치를 상대적으로 표현하는 걸 **상대 경로 임포트**라고 한다. 반대로 우리가 계속해 왔던 것처럼 임포트하려는 것의 경로를 다 풀어서 써 주는 것은 **절대 경로 임포트**라고 한다.

상대 경로 임포트는 항상 `.` 아니면 `..` 으로 시작한다. `.` 은 현재 패키지 안을 뜻하고, `..` 은 상위 패키지 안을 뜻한다.

예를 들어 shaeps 패키지의 init 파일의 기준으로는 현재 패키지가 mymath/shapes 이고 상위 패키지는 mymath 일 것이다.

### 1. shapes 패키지의 init 파일에서 패키지 안에 있는 모듈들 가져오기:

`mymath/shapes/__init__.py`

```python
# 절대 경로 임포트
from mymath.shapes import area, volume

# 상대 경로 임포트
from . import area, volume
```

상대 경로가 훨씬 더 간결하다.

임포트 문이 의미하는 것도 명확하다: 현재 패키지에서 area, volume 모듈을 임포트 하라는 뜻

### 2. stats 패키지의 init 파일에서 패키지의 모듈들 안에 있는 함수들 모두 가져오기:

`mymath/stats/__init__.py`

```python
# 절대 경로 임포트
from mymath.stats.average import *
from mymath.stats.spread import *

# 상대 경로 임포트
from .average import *
from .spread import *
```

첫 번째 예시와 비슷하게 상대 경로를 사용할 때 임포트 문이 더 간결해졌고 의미하는 것도 명확하다: 현재 패키지의 average, spread 모듈에서 모든 내용을 다 가져오라는 뜻

### 3. area 모듈에서 average 모듈에 있는 `data_mean` 함수 가져오기

프로그램을 만들다 보면 이렇게 패키지 안에서 다른 패키지에 있는 것이 필요할 때도 있다.

mymath/shapes.area.py

```python
# 절대 경로 임포트
from mymath.stats.average import data_mean

# 상대 경로 임포트
from ..stats.average import data_mean
```

이번에는 상대 경로를 봐서는 average 모듈이 정확히 어디에 있는지, 패키지 구조가 어떻게 되는지 파악하기가 힘들다.

상대 경로가 복잡해지는 경우 (주로 `..` 을 쓰는 경우)에는 그냥 절대 경로를 쓰는 것이 좋다.

</details>

<details>
  <summary>3. 외부 패키지 사용하기</summary>

# 외부 패키지 사용하기

## 외부 패키지란?

파이썬을 사용하는 개발자들이 여러 프로그래밍 분야에서 유용하게 쓰이는 기능들을 패키지로 만들어 놓은 것을 외부 패키지, 또는 외부 라이브러리라고 함

### 외부 패키지 사용법?

패키지에 어떤 함수들이 어떤 함수들이 있는지, 함수들이 어떤 일들을 하는지는

패키지의 공식 문서에 잘 정리되어 있다. 또한, 구글링을 통해서도 좋은 자료를 많이 찾을 수 있다.

### PyPI (Python Package Index)

파이썬에는 PyPI라는 공식 패키지 저장소가 있다.

여기에는 데이터 분석, 머신 러닝, 업무 자동화, 웹 개발을 포함한, 거의 모든 프로그래밍 분야의 패키지들이 있다.

PyPI을 통해서 파이썬 패키지들을 검색할 수 있고, 개별 패키지 페이지로 가면 패키지에 대한 설명을 볼 수 있다.

잘 갖춰진 공식 문서에는 Getting Strarted, User Guide, API reference와 같은 섹션이 따로 있다.

Getting Started는 입문자들을 위한 가이드로서, 패키지를 설치하는 법, 패키지의 핵심 개념들에 대한 설명 및 튜토리얼을 찾아볼 수 있다.

User Guide는 더 일반적인 가이드로서, 모든 토픽들에 대한 설명들이 있다.

API reference는 패키지의 기능과 개념을 설명해 주기 보다는, 패키지의 함수들과 객체의 인풋 파라미터, 리턴 값에 대해서 자세히 알려준다.

### API란?

외부 패키지 안에는 보통 엄청나게 많은 코드가있다. 그런데 그 코드의 대부분은 어떤 기능을 구현하기 위해서 내부적으로 사용된다. 패키지의 사용자는 패키지의 특정 함수들이나 클래스들을 이용해서 패키지의 기능을 쉽게 사용할 수 있다. 이렇게 패키지의 기능을 사용자에게 노출하는 함수들 또는 클래스들을 합쳐서 API (Application Programming Interface)라고 한다.

패키지의 init 파일에서는 패키지의 핵심 API를 쉽게 사용할 수 있도록 임포트해 주는 게 좋다.

## 스탠다드 라이브러리 vs 외부 라이브러리

### 스탠다드 라이브러리

스탠다드 라이브러리는 프로그래밍에 필요한 가장 기본적인 기능들을 제공한다. 스탠다드 라이브러리 안에는 자료형, 내장 함수, 스탠다드 모듈 등이 있다.

참고로 스탠다드 라이브러리는 패키지가 아니다. 여기서 '라이브러리'는 단순히 어떤 기능들의 모음을 뜻한다.

스탠다드 라이브러리는 파이썬을 설치하면 기본적으로 딸려오기 때문에 따로 설치하지 않아도 된다.

### 외부 라이브러리

외부 라이브러리 또는 외부 패키지는 파이썬을 사용하는 일반 개발자들이 패키지를 만들어서 PyPI에 업로드해 놓은 것이다.

외부 라이브러리는 파이썬의 일부가 아니고 직접 설치해야 한다.

## 파이썬의 가장 대표적인 패키지들

### 데이터 분석 & 시각화

**numpy**

numpy는 행렬(다차원 배열)을 다루는 패키지다. 데이터 분석이나 머신 러닝을 할 때는 데이터가 행렬 형식인 경우가 많다.

**pandas**

pandas는 데이터를 우리가 쉽게 다룰 수 있는 테이블 형식으로 만들어 준다. 결국 데이터 분석이나 머신 러닝을 하려면 데이터를 다뤄야 하기 때문에 pandas는 데이터 분석의 가장 핵심적인 패키지라고 할 수 있다. 거의 모든 데이터 사이언스 패키지들은 pandas와 연동이 된다.

**matplotlib**

matplotlib는 파이썬에서 가장 많이 쓰이는 데이터 시각화 라이브러리다. 일반적인 그래프들은 거의 다 matplotlib로 그릴 수 있다.

**seaborn**

seaborn은 matplotlib를 기반으로 한 시각화 라이브러리다. matplotlib보다 간단한 문법을 사용해서 더 예쁜 그래프들을 그릴 수 있다.

## 머신 러닝

**sklearn**

sklearn은 가장 대중적인 머신 러닝 라이브러리다. 기본적인 머신 러닝 알고리즘은 모두 지원한다. 데이터 가공, 모델 평가 기능도 제공한다.

**tensorflow, pytorch, keras**

모두 딥러닝에 최적화된 라이브러리들이다. 컴퓨터 비전에 많이 사용되는 CNN (Convolutional Neural Network(, 자연어 처리에 많이 사용되는 RNN (Recurrent Neural Network) 모델 등을 구현할 수 있다.

**nltk**

nltk는 텍스트 데이터 가공, 시각화 등을 지원하는 자연어 처리 라이브러리다.

## 웹 개발

**django**

django는 파이썬에서 많이 쓰이는 웹 프레임워크다.

일반적으로 프레임워크는 어떤 소프트웨어의 뼈대 같은 역할을 한다. 웹 프레임워크는 웹 애플리케이션을 만들기 위한 뼈대다. 사용자는 뼈대를 제외한 나머지 디테일을 채워 넣기만 하면 된다.

**flask**

flask는 파이썬에서 많이 쓰이는 또 다른 웹 프레임워크다.

django는 웹 개발에 필요한 모든 기능을 제공하지만 비교적 복잡하고, flask는 기본적인 기능만 제공하지만 비교적 간단하다.

## 기타

**beautifulsoup4**

beautifulsoup4는 html 또는 xml 문서를 파싱(원하는 데이터를 특정 패턴이나 순서로 추출해 가공하는 것)해 주는 라이브러리다. 보통 웹에서 원하는 데이터를 긁어 오는 작업인 웹 스크레이핑(web scraping)에 많이 사용된다.

**selenium**

selenium은 웹 브라우저 동작을 자동화해 주는 패키지이다. selenium을 사용하면 클릭, 로그인, 검색, 스크롤링 등을 자동화할 수 있다. 웹 애플리케이션 테스팅 자동화와 웹 스크레이핑에 많이 사용된다.

**requests**

requests는 파이썬의 간편한 http 라이브러리다. requests 라이브러리를 통해 쉽게 http 요청을 보낼 수 있다.

**opencv**

opencv는 컴퓨터 비전에 많이 사용되는 라이브러리다. 이미지 프로세싱, 얼굴 인식, 문자 인식 등 많은 기능을 제공한다.

</details>
