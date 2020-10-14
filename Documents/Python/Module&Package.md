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
</details>

<details>
  <summary>3. 외부 패키지 사용하기</summary>
</details>
