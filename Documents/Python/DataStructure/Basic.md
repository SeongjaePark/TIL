# 1. 기본적인 자료구조

[코드잇 자료구조 ](https://www.codeit.kr/courses/data-structures)

<details>
  <summary>1) 컴퓨터가 데이터를 저장하는 법</summary>

  <details>
    <summary> 스토리지 Vs 메모리</summary>

# 스토리지 Vs 메모리

자료 구조

- 목적: 자료를 구조화 → 데이터를 효율적으로 사용
- 컴퓨터에 데이터가 어떻게 저장되는지 알아야 됨!

데이터 저장

- **스토리지**: 데이터가 영구적으로 저장되는 곳
  - 데이터를 저장하는 데 오래 걸림
  - 데이터를 받아오는 데 오래 걸림
- **메모리**: 데이터가 **임시**로 저장되는 곳
  - 데이터를 저장이 빠르다
  - 데이터를 받아오기가 빠르다

왜 따로 필요?

- 스토리지는 용량이 크기 때문에 스토리지에 저장해 놓고, 필요할 때 메모리에 올려놓고 사용
  - 영화를 볼 때, 파일을 실행하면 매 장면을 실시간으로 스토리지에서 받아오면 느리기 때문에 메모리에 복사해놓고 메모리로부터 받아오면 빠름. 대신 영화를 끄면 메모리에 있는 영화 데이터는 지워지고 스토리지에만 남게 됨

자료구조에서 중요한 것은 메모리.

결국 자료구조는 데이터를 메모리에서 잘 사용하도록 하는 것이 목적임

  </details>

  <details>
    <summary> RAM</summary>

# RAM: Random Access Memory

### 메모리

- 일정한 칸으로 나눠져 있음
- 각 칸에 데이터를 저장할 수 있음
- 각 칸은 자신만의 주소가 있음

### RAM: 임의 접근 메모리

- 임의 접근: 저장 위치를 알면 접근할 때 항상 일정한 시간이 걸림
  - 메모리에 저장한 데이터 접근 시간 복잡도: O(1)
- 순차 접근: 저장된 위치까지 가는 데 한 단계씩 거쳐야 됨 (예: 비디오 테이프)
- 임의 접근이 순차 접근보다 효율적!

메모리는 **임의 접근**으로 동작하고 있다는 것을 늘 기억하고 있어야 한다.

  </details>
  
  <details>
    <summary>메모리의 기본 단위:</summary>

# 메모리의 기본 단위: 바이트

메모리 한 칸이 저장할 수 있는 가장 기본적인 용량의 단위는 1**바이트(byte) = 8비트(bit)**.

바이트가 아닌 다른 크기의 용량을 담는 저장 장치들도 있지만, 대부분의 현대 컴퓨터 시스템들은 메모리 한 칸에 바이트만큼의 데이터를 저장함

1. 바이트는 컴퓨터 저장 공간 용량을 나타내는 단위
2. 메모리 한 칸에 담기는 데이터 용량은 1 바이트

  </details>

  <details>
    <summary>레퍼런스</summary>

# 레퍼런스

### 레퍼런스(reference)

- 데이터에 접근할 수 있게 해주는 값
- "주소"보다 조금 더 포괄적인 표현 (주소 자체가 항상 레퍼런스인 것은 아님)
- 자료 구조를 공부할 때는 주소와 레퍼런스를 비슷하게 생각해도 무방

### 변수를 사용할 때

```python
x = 95
print(x + 5) -> #print(95 + 5)
```

x에 정수 95가 아니라, 레퍼런스가 담겨 있음

레퍼런스에 5를 더하는 것이 아니라,  
**실제로 변수를 사용할 때는 저장된 값을 알아서 받아옴**

  </details>

  <details>
    <summary>데이터의 주소</summary>

# 데이터의 주소

### 파이썬 id() 함수

데이터가 저장되어 있는 주소를 알아내는 방법

`id()` 함수를 이용하면 저장된 데이터의 메모리 주소를 정수로 표현한 값을 알아낼 수 있다.

여러 타입의 데이터를 저장하고 `id()` 함수를 써서 메모리 주소를 출력시켜 보자.

```python
# 여러 데이터를 저장한다.
list1 = [1, 2]
int1 = 0
float1 = 3.14
set1 = set()
tuple1 = (2, 3)

# 저장된 데이터의 메모리 저장 위치를 받아온다.
print(id(list1)) # 140691582428864
print(id(int1)) # 140691591012576
print(id(float1)) # 140691582327216
print(id(set1)) # 140691580568064
print(id(tuple1)) # 140691582524544
```

데이터가 각각 다른 메모리 주소에 저장되어 있는 것을 확인할 수 있다.

### 같은 주소에 저장되어 있는 데이터

당연한 말이지만, 똑같은 주소에 저장되어 있는 데이터는 똑같은 데이터이다.

```python
# 리스트를 정의한다
list1 = [1, 2]
list3 = [1, 2, 3]

# Aliasing을 통해 list1과 list2를 같게 한다
list2 = list1

# 두 데이터의 메모리를 출력한다
print(id(list1)) # 140618457056960
print(id(list2)) # 140618457056960
print(id(list3)) # 140618457057344

```

메모리에서 만든 하나의 같은 리스트를 list1, list2라는 두 개의 다른 변수가 가리키고 있다.

이렇게 여러 변수가 같은 메모리를 가리키는 것을 **Aliasing**이라고 한다.

`id()` 함수를 써서 메모리 주소를 출력해보면, list1과 list2는 서로 같은 리스트를 가리키고 있기 때문에 똑같은 메모리 주소가 출력되고, list3는 전혀 다른 리스트를 가리키고 있기 때문에 다른 메모리 주소가 출력된다.

  </details>

</details>

<details>
  <summary>2) 배열</summary>

  <details>
    <summary>배열이란</summary>

# 배열이란

파이썬 리스트는 C 언어의 배열을 이용해 만들어졌음

### C 배열

- 크기가 고정돼 있다
- 같은 타입의 데이터만 담을 수 있다
- 값 자체를 저장
- 데이터가 메모리에 연속적으로 저장

### 파이썬 리스트

- 크기가 유동적이다
- 다양한 타입의 데이터를 담을 수 있다
- 레퍼런스를 저장

  </details>
  <details>
  <summary>배열 인덱스를 이용한 데이터 저장/접근법</summary>

# 배열 인덱스를 이용한 데이터 저장/접근법

### 정수형 값 4개를 저장하는 C 배열 정의

```c
//정수형 값 하나의 크기 = 4 바이트

int numArray[4]; //사용하고 있지 않은 **연속**적인 16칸 예약
numArray[0] = 2;
numArray[1] = 3;
numArray[2] = 5;
numArray[3] = 7;
// 배열의 요소들이 메모리에 순서대로 그리고 연속적으로 저장 됨
```

저장된 데이터를 받아오는 건 저장할 때처럼 그냥 인덱스를 사용하면 됨

인덱스 i의 주소: 시작주소 + 데이터 크기 x 인덱스

- ex) 배열의 시작주소가 1000이고, 정수형 배열인 경우의 주소: 1000 + 4 x i

### 배열 인덱스 접근과 저장의 시간복잡도

이처럼 배열의 값을 가져오려면 그 값의 주소를 알아야 함

그 주소는 그냥 간단한 계산으로 알 수 있음

따라서 임의 접근이기 때문에 배열에서 값을 받아오는 건 **O(1)**으로 할 수 있음

값을 저장하는 것도 마찬가지. 주소를 계산해서 그 주소에 O(1)으로 접근하고 거기에 값을 저장하면 되는 것임

  </details>

  <details>
    <summary>배열 탐색</summary>

# 배열 탐색

### 접근과 탐색

- 접근: 인덱스를 통해 값을 찾는 것
- 탐색: 특정 조건을 만족하는 값을 찾는 것

### 선형 탐색

- 값이 존재하는지 첫번째 인덱스부터 시작해서 찾을때까지 쭈욱 확인하는 방법
- 배열이 정렬되어 있지 않은 이상 사실상 이 방법보다 효율적으로 탐색할 수는 없음
- 시간 복잡도: O(n)

### 정리

- 배열 접근 연산: O(1)
- 배열 탐색 연산: O(n)
  </details>

  <details>
    <summary>정적 & 동적 배열</summary>

# 정적 배열

### 배열

- 정적 배열: 크기 고정 (요소 수 제한)
- 동저 배열: 크기 변함 (요소 계속 추가 가능)

보통 배열이라고 할 때에는 정적 배열을 뜻하고, 동적 배열은 '동적' 배열이라고 확실히 표현

모든 주소에 값이 있는 정적 배열에서 배열에 새로운 요소를 추가하려면 새로운 배열로 복사하고 그 뒤에 값을 추가해야 함

그렇다고 배열에 미리 너무 많은 메모리를 할당하면 메모리를 쓸데없이 낭비하게 됨

# 동적 배열 (Dynamic Array)

- 정적 배열로 만들어진 자료 구조
- 정적 배열의 크기를 상황에 맞게 조절한다.
  - ex) 기존 배열이 꽉 찼을 때 배열의 크기를 2배로 늘려주면 한 동안 늘려줄 필요가 없다
  </details>
  <details>
    <summary>파이썬 리스트의 비밀</summary>

# 파이썬 리스트(동적 배열)의 비밀

파이썬은 C를 통해 구현된 언어로, 파이썬의 리스트는 내부적으로 C 배열을 이용해서 만들어짐

`int_list = [2, 3, 5, 7, 11]`

우리 입장에서 내부적으로 얼마나 큰 배열이 있는지 몰라도, 값을 마음대로 추가할 수 있다. 동적 배열이기 때문에 상화에 맞게 배열의 크기가 조절되고 있는 것

`int_list.append(13)`

그런데 우리는 내부적으로 얼마나 큰 배열이 있는지 모른다. 아무리 저장한 데이터가 6개여도 내부적으로는 8개짜리 배열일 수도 있고, 12개짜리 배열일 수도 있고, 알 수가 없다.

만약 리스트 길이를 출력하면 뭐가 나올까?

`print(len(int_list)) # 6`

실제 사용하고 있는 메모리 공간이 더 많을지라도, 파이썬은 개수를 셀 때 값을 저장해 놓은 공간에 대해서만 알려준다. 그래서 우리는 나머지 공간에 대해서 전혀 신경을 안 써도 된다.

만약 채워지지 않은 공간에 접근하려고 하면

`print(int_list[9])`

오류가 난다. 우리가 미리 값을 저장해 놓은 공간에만 접근할 수 있도록 파이썬이 미리 처리를 해 놓은 것임

파이썬 뿐만 아니라 **동적 배열**을 자료형으로 제공한느 대부분의 언어들은 이렇게 실제 사용하는 배열의 크기와 상관 없이 **저장해 놓은 공간만 사용할 수 있게** 처리해줌

  </details>
  <details>
    <summary>동적 배열 추가 연산 시간 복잡도</summary>

# 동적 배열 추가 연산 시간 복잡도

## 추가 연산 (append operation)

### 경우 1: 정적 배열에 남는 공간 있을 때

그냥 비어있는 공간 중에 가장 앞 쪽에 있는 곳에 데이터를 저장하면 됨

시간복잡도: O(1)

### 경우 2: 정적 배열이 꽉 찼을 때

1. 값을 복사하기 위해서 현재 사용 중인 공간보다 2배로 큰 메모리 공간 예약
2. 기존 배열에서 새로운 배열로 값을 싹 다 복사: O(n)
3. 빈 칸에 새로운 값을 추가: O(1)

시간복잡도: O(n)

### 동적 배열 추가 연산 시간 복잡도

최고의 경우: O(1)

최악의 경우: O(n)

  </details>
  <details>
    <summary>분활 상환 분석 개념 & 적용</summary>

# 분활 상환 분석 개념

동적 배열 추가 연산을 할 때 최고의 경우(빈 공간O)는 자주 일어나며, 최악의 경우(빈 공간X)는 가끔 일어남

따라서 최악의 경우인 O(n)으로 시간 복잡도를 계산하는 것은 조금 비합리적인 것으로 보임

보통 시간 복잡도는 최악의 경우로 말하는데, 지금처럼 그것이 비합리적인 상황들이 종종 있음

이런 상황에 쓰이는, 시간 복잡도를 다르게 계산하는 방법들이 있음

## 분활 상환 분석 (Amortized Analysis)

- 같은 동작을 n번 했을 때 드는 시간이 X일 때: 동작을 한 번 하는 데 걸린 시간 = X / n

# 분활 상환 분석 적용

## 동적 배열 추가 연산

1. 새로운 인덱스에 데이터를 저장하는 시간
2. 기존 배열의 크기가 부족해서 더 큰 배열을 만들고, 기존 배열의 데이터들을 옮기는 시간

## 분할 상환 분석

동적 배열 추가 연산을 n번 반복한다고 가정.

총 시간을 계산하기 쉽게 두 가지로 나눠서 생각

1. 새로운 데이터를 동적 배열 맨 끝에 단순히 저장하는 데 걸리는 시간
2. 더 큰 배열을 만들고 그 배열에 기존의 데이터를 옮기는 데 걸리는 시간

### 배열 끝에 새로운 데이터를 저장하는 데 걸리는 시간

인덱스에 데이터를 저장하는 데 걸리는 시간은 1.

이걸 총 n번 하는 거니까 O(n)이 걸림

### 새로운 배열에 데이터를 옮기는 시간

내부 배열이 꽉 차서 데이터를 복사하는 데 걸리는 시간.

1칸 짜리 배열부터 시작하고, 배열이 꽉 찰 때마다 배열의 크기를 2배로 늘린다고 가정

2번째, 3번째, 5번째, 9번째 추가 때 배열의 크기를 늘려야 함. 그럴 때마다 데이터를 옮겨야 함

이때 데이터를 각각 1, 2, 4, 8개씩 복사하고 붙여넣음

→ 데이터를 복사해서 붙여 넣는 총 시간 비용은 이 시간들을 더한 8+4+2+1

**좀 더 일반화해서 생각**

추가 연산은 n번 했을 때, 가장 마지막에 데이터를 m개 옮겨서 저장했다고 가정

데이터를 복사해서 저장하는 데 걸린 총 시간은: m + m/2 + m/4 + ... + 1

어느 자연수 m이든 반씩 줄여서 1까지 계속 더해주면 그 결과는 절대 2m을 넘을 수 없음

결과는 _2m-1_ 이 됨

추가 연산을 연속으로 n번 하고, 가장 마지막에 옮겨 저장한 데이터 요소 수를 m이라고 할 때:

- 복사해서 저장하는 데 걸린 총 시간이 2m-1 이고
- m은 n보다 작다

다시 정리하면,

> 연속으로 추가 연산을 n번을 하면 데이터를 옮겨서 저장하는 데 걸리는 총 시간은 2n보다 작다!

## 두 경우 합치기

종합하면, 동적 배열에 n개의 데이터를 연속으로 추가하면:

1. 새로운 데이터를 저장하는 데에는 n의 시간이 들고
2. 데이터를 옮겨 저장하는 데에는 2n보다 적은 시간이 듦

이 두 시간을 합치면 총 드는 시간은 3n보다 적은 시간. 시간 복잡도로 표현하면 O(3n),

즉 O(n)임

근데 이것은 추가 연산을 한 번 하는 게 아니라 연속으로 n번 하는 데 걸리는 시간 복잡도임

따라서 뻔 하는 데는 O(n) / n, 즉 O(1)이 걸리는 것

전에는 추가 연산이 최악의 경우 O(n)이 걸린다고 했는데, 분할 상환 분석을 하면 O(1)이 걸린다고 보는 것

## 최악의 경우 분석 vs. 분할 상환 분석

분할 상환 분석을 한다고 꼭 시간 복잡도가 줄어드는 건 아님 보통은 할부 개념을 적용해도 시간 복잡도가 줄어들지 않음

하지만 만약 최악의 경우보다 분할 상환 분석을 한 시간 복잡도가 더 적다면, 분할 상환 분석을 한 시간 복잡도를 사용함

"동적 배열의 끝에 데이털르 추가할 때는 O(1)이 걸린다" 라고 표현해도 된다는 것

좀 더 정확하게 표현하자면,

> 동적 배열의 추가 연산은 최악의 경우 O(n)이 걸리지만, 분할 상환 분석을 하면 O(1)이 걸린다.

  </details>

  <details>
    <summary>동적 배열 삽입 연산</summary>

# 동적 배열 삽입 연산

추가(append) - 맨 끝에 넣을 때

삽입(insertion) - 배열의 아무 위치에나 넣을 때

## 삽입 연산(insert operation)

- 경우 1: 정적 배열에 남는 공간이 있을 때
- 경우 2: 정적 배열이 꽉 찼을 때

### 정적 배열에 여유 공간이 있을 때

넣으려고 하는 인덱스 이후의 모든 데이터를 한 칸씩 뒤로 밀어주어야 함(한 칸 뒤의 인덱스에 저장)

최악의 경우 시간 복잡도: O(n)

### 정적 배열이 꽉 찼을 때

새로운 배열에 요소들을 복사할 때 O(n) + 원하는 인덱스에 자리를 마련할 때 O(n) + 인덱스에 데이터를 저장할 때 O(1) = O(2n+1)

즉, O(n)

## 종합

가능한 두 경우 모두 시간 복잡도가 O(n)이므로,

삽입 연산의 시간 복잡도: O(n)

  </details>
  <details>
    <summary>동적 배열 삭제 연산</summary>

# 동적 배열 삭제 연산

## 삭제 연산

1. 삭제를 원하는 인덱스 뒤에 있는 데이터를 모두 한 칸씩 앞으로 밀어서 저장
2. 데이터를 삭제했으니까 동적 배열에서 접근할 수 있는 인덱스 범위도 1 감소시킴

요약하면, 삭제 연산은 그냥 삭제하고 싶은 데이터 뒤에 있는 모든 데이터 요소들을 한 칸씩 앞으로 밀어서 저장하면 됨

## 시간 복잡도

### 맨 앞의 데이터를 지울 때 (최악의 경우)

인덱스 1부터 끝까지 모든 요소들을 한 칸씩 앞으로 밀어서 저장해야 됨.

n - 1 개의 요소들을 하나씩 앞 칸으로 밀어서 저장

이 횟수가 n에 비례하기 때문에 시간 복잡도는 **O(n)**

### 맨 뒤 데이터를 지울 때

맨 뒤 데이터를 삭제할 때는 아무 요소를 안 밀고 저장해도 되고, 그냥 동적 배열의 사용 공간을 한 인덱스 줄이면 됨

이건 배열에 데이터 요소가 몇 개 있는지에 상관 없이 일정한 시간에 할 수 있음

따라서 시간 복잡도는 **O(1)**

## 정리

동적 배열의 임의의 위치에 있는 데이터를 삭제할 때는 원하는 위치 뒤에 있는 데이터를 옮겨 저장해야 하기 때문에 최악의 경우 O(n)이 걸림

하지만 가장 뒤에 있는 데이터를 삭제할 때는 다른 데이터를 옮겨 저장할 필요가 없기 때문에 O(1)이 걸림

  </details>
  <details>
    <summary>동적 배열 크기 줄이기</summary>

# 동적 배열 크기 줄이기

동적 배열은 내부적으로 정해진 크기의 정적 배열을 사용하고 있음

값을 추가하다가 내부 배열이 꽉 차면 더 큰 내부 배열을 사용하도록 자동으로 늘려 줌

반대로, 삭제를 할 때에는 내부 배열의 크기를 줄이기도 함

## 왜 내부 배열의 크기를 줄여야 될까?

만약 데이터 요소 10000개 있는 동적 배열에서 요소 9900개를 삭제하면 되면 100개만 남게 되는데, 그러면 나머지 9900개의 요소를 저장할 수 있는 낭비될 것임

동적 배열은 요소의 개수가 어느 정도 줄어들면 내부 배열의 크기도 적절히 줄여서 **공간을 좀 더 효율적으로 사용**함

## 내부 배열의 크기는 어떻게 줄어들까?

동적 배열의 요소 삭제 후 정확히 어떤 시점에 배열의 크기를 줄이면 좋을까?

크기를 늘릴 때는 내부 배열이 꽉 찼을 때였는데, 크기를 줄일 때는 내부 배열의 사용 비율이 특정 값 이하로 떨어질 때임

이 비율이 **1/3** 이라고 가정해보자. 또, 크기가 9인 배열에서 요소가 4개에서 3개로 줄어든 상황을 가정해보자.

총 사용할 수 있는 공간 중 1/3 밖에 사용을 안 하고 있는 것임. 이때:

1. 크기가 3인 새로운 내부 배열을 정의한다.
2. 기존의 3개 요소를 새로 만든 내부 배열에 옮겨서 저장한다.

전에는 6칸을 낭비하고 있었는데 이제는 낭비하고 있는 공간이 하나도 없음. 내부 배열의 크기를 요소 수에 맞게 줄이면, 낭비하는 공간을 최소한으로 할 수 있음

배열의 크기를 줄이는 사용 비율의 기준은 개발자나 프로그래밍 언어에 따라 다르다.

일단 생각의 편의를 위해 배열의 크기를 늘릴 때는 2배로 늘리고, 줄일 때에는 **요소 수가 배열 크기의 1/2가 됐을 때 줄인다고 가정**하자.

## 시간 복잡도

### 동적 배열 맨 끝 데이터 삭제 시간 복잡도

최악의 경우: 더 작은 배열로 모든 요소들을 옮겨 저장해야 될 때

- 총 n개의 데이터를 모두 새 배열에 복사해서 넣어야 함
- 맨 뒤 데이터 삭제: O(1)
- n개의 데이터를 모두 새 배열에 복사: O(n)
- 시간 복잡도: O(n)

### 맨 끝 데이터 삭제 분활 상환 분석

하지만 내부 배열의 크기가 줄어드는 건 드문 경우임. 대부분의 경우 그냥 마지막 인덱스에 있는 데이터를 지워 주기만 하면 됨

동적 배열에서 마지막 데이터를 삭제할 때는 대부분의 경우 O(1)이 걸리지만, 드물게 O(n)이 걸림

그렇기 때문에 추가 연산과 마찬가지로 분할 상환 분석을 적용할 수 있음

분할 상환 분석을 적용하면 맨 끝 데이터 삭제 연산도 O(1)이 걸린다고 이야기할 수 있음

## 정리

> 동적 배열에서 맨 끝 데이터를 삭제하는 연산은 최악의 경우 O(n)이 걸리지만, 분할 상환 분석을 적용하면 O(1)이라고 할 수 있다.

  </details>
  <details>
    <summary>배열과 동적 배열 정리/비교</summary>

# 배열과 동적 배열 정리/비교

## 연산 & 시간 복잡도

### (정적) 배열

- 접근 (access): O(1)
- 탐색 (search): O(n)
- 삽입 (insert): Not Available
- 삭제 (delete): Not Available

### 동적 배열

- 접근 (access): O(1)
- 탐색 (search): O(n)
- 삽입 (insert): O(n), 맨 뒤 O(1)
- 삭제 (delete): O(n), 맨 뒤 O(1)

## 낭비하는 공간

### (정적) 배열

크기가 고정되어 있기 때문에 낭비하는 공간이 없다!

### 동적 배열

공간을 낭비할 수도 있고 안 할 수도 있다!

최악의 경우

- 저장된 요소 수: n
- 낭비되는 공간: n - 2

최소 0 ~ 최대 n - 2

낭비하는 공간: O(n - 2) = **O(n)**

  </details>
  <details>
    <summary>정적 배열에 삽입과 삭제를 못 하는 이유</summary>

# 정적 배열에 삽입과 삭제를 못 하는 이유

## 배열에 데이터 삽입을 못 하는 이유

배열은 크기가 정해져 있음. 더 많은 데이터 요소들을 저장하고 싶으면 더 큰 배열을 정의해야 함.

사용하고 싶은 요소 수에 따라 크기를 바꿀 수 있으면 그건 배열이 아니라 동적 배열일 것임

크기가 고정되어 있는 배열에는 처음 정한 수보다 더 많은 데이터를 삽입할 수 없는 것

## 배열에 데이터 삭제를 못 하는 이유

정수 4개를 담을 수 있는 배열에 2, 3, 5, 7이 저장되어 있다고 가정하자. 여기서 인덱스 1에 있는 3을 지우고 싶으면 어떻게 하면 될까?

동적 배열 삭제 연산처럼 인덱스 1 자리에 인덱스 2의 데이터를 저장하고, 인덱스 2에 인덱스 3 데이터를 저장해서 2, 5, 7, 7 이렇게 하면 될까?

여기서 문제는 인덱스 3에 저장되어 있던 7을 메모리에서 자연스럽게 지울 수 있는 방법이 마땅히 없다는 것이다.

비었다는 것을 표시하기 위해서 파이썬에서는 None, 다른 언어들에서는 Null 이런 값을 넣는 방법을 생각할 수도 있다. 그런데 우리가 C에서 정의한 정수형 자료가 들어가는 배열에 None이나 Null은 정수형이 아니기 때문에 저장할 수 없다.

정리하자면 배열에서 인덱스 1을 지우기 위해서는 2, 3, 5, 7의 데이터를 2, 5, 7으로 만드는 게 아니라, 2, 5, 7, 7 이런 식으로 밖에 못 만든다.

지우고 싶은 요소를 "자연스럽게" 삭제할 수는 없는 것이다.

### 비교: 동적 배열에서의 삭제

많은 언어들 자체적으로 제공하는 동적 배열은 사용하는 배열의 크기와 사용하는 인덱스 범위를 따로 처리한다.

동적 배열이 내부적으로 정수 4개를 저장할 수 있는 배열에 2, 3, 5, 7을 저장하고 있다고 가정하자.

동적 배열에서 인덱스 1을 삭제하고 싶으면 인덱스 1에 5를 저장하고, 인덱스 2에 7을 저장한다. 그럼 내부적으로는 2, 5, 7, 7 이렇게 저장되어 있을텐데,

그 다음에 인덱스 3에 있는 7을 지우는 게 아니라 파이썬 내부적으로 개발자가 접근할 수 있는 인덱스 범위를 0 ~ 2로 만들어 버린다. 더 이상 인덱스 3에 접근할 수 없게 만드는 것

실제로 인덱스 3에 어떤 값이 저장되어 있든 상관 없이 개발자는 더 이상 거기 접근할 수 없다. 동적 배열에서 접근할 수 있는 데이터가 2, 5, 7 밖에 없으니까 실질적으로 삭제되었다고 할 수 있는 것.

  </details>

</details>

<details>
  <summary>3-1) 링크드 리스트</summary>

  <details>
    <summary>링크드 리스트 개념</summary>

# 링크드 리스트 개념

## 링크드 리스트 (Linked List)

- 데이터를 순서대로 저장
- 요소를 계속 추가할 수 있음

노드라는 단위의 데이터를 저장하고, 데이터가 저장된 노드들을 순서대로 연결시켜서 만든 자료 구조

각 노드는 값과, 다음 노드를 가리키는 부분으로 이루어져 있음

# 링크드 리스트 프로그래밍적으로 생각하기

## 노드(Node)

각 노드는 하나의 박스라고 생각하면 편함

각 노드는 data 뿐과 next 부분이 있음

- data: 우리가 저장하고 싶은 정보를 넣는 곳
- next: 다음 노드에 대한 레퍼런스를 넣는 곳

n_1.next = n_2

- n_1.next는 n_2에 대한 레퍼런스!

이런 노드 객체를 여러 개 만듦.

이런 노드 객체들은 서로 딱히 관계가 없음. 메모리에 연속적으로 저장된 것이 아니라, 각자 알아서 어딘가에 흩어져 있다는 뜻임

각 노드는 다음 노드에 대한 레퍼런스가 있음. 노드 객체의 next 속성을 보면 다음 노드가 어디에 있는지 알 수 있는 것.

가장 첫번째 노드 객체의 메모리 주소만 알고 있으면 next를 타고, 타고 가서 연결되어 있는 모든 노드 객체에 접근할 수 있음.

링크드 리스트의 시작점이라고 할 수 있는 이 첫번째 노드를 **head 노드**라고 함.

이 head 노드만 있으면 흩어져 있는 다른 노드들을 연결지어서 순서를 저장할 수 있음

배열이나 동적 배열처럼, 정보를 원하는 순서대로 저장할 수 있는 것

주의할 점: 링크드 리스트에서 각 노드들은 실제 메모리에서는 여기저기 흩어져 있다!

  </details>
  <details>
    <summary>간단한 링크드 리스트 만들기</summary>
  
  # 노드 클래스 만들기

## 노드 클래스와 인스턴스들을 만들어 보자

```python
class Node:
  """링크드 리스트의 노드 클래스"""

  def __init__(self, data):
    self.data = data # 노드가 저장하는 데이터
    self.next = None # 다음 노드에 대한 레퍼런스

# 데이터 2, 3, 5, 7, 11을 담는 노드들 생성
head_node = Node(2)
node_1 = Node(3)
node_2 = Node(5)
node_3 = Node(7)
tail_node = Node(11)
```

# 간단한 링크드 리스트 만들기

## 아직 아무런 관계가 없는 노드들을 연결시켜보자

**iterator**: 반복문으로 리스트를 돌 때 도움을 주는 역할을 하는 값을 **이터레이터** 라고 부름

```python
class Node:
  """링크드 리스트의 노드 클래스"""

  def __init__(self, data):
    self.data = data # 노드가 저장하는 데이터
    self.next = None # 다음 노드에 대한 레퍼런스

# 데이터 2, 3, 5, 7, 11을 담는 노드들 생성
head_node = Node(2)
node_1 = Node(3)
node_2 = Node(5)
node_3 = Node(7)
tail_node = Node(11)

# 노드들을 연결
head_node.next = node_1
node_1.next = node_2
node_2.next = node_3
node_3.next = tail_node

# 노드 순서대로 출력
iterator = head_node

while iterator is not None:
  print(iterator.data)
  iterator = iterator.next

"""출력값
2
3
5
7
11
"""
```

  </details>
  <details>
  <summary>링크드 리스트 추가 연산</summary>

# 링크드 리스트 추가 연산

## 링크드 리스트를 조금 더 체계적으로 관리하기 위해서 클래스를 만들어보자

```python
class Node:
  """링크드 리스트의 노드 클래스"""

  def __init__(self, data):
    self.data = data # 노드가 저장하는 데이터
    self.next = None # 다음 노드에 대한 레퍼런스

class LinkedList:
  """링크드 리스트 클래스"""

  def __init__(self):
    self.head = None
    self.tail = None

  def append(self, data):
    """링크드 리스트 추가 연산 메소드"""
    new_node = Node(data)

    if self.head is None:
      self.head = new_node
      self.tail = new_node
    else:
      self.tail.next = new_node
      self.tail = new_node

# 새로운 링크드 리스트 생성
my_list = LinkedList()

# 링크드 리스트에 데이터 추가
my_list.append(2)
my_list.append(3)
my_list.append(5)
my_list.append(7)
my_list.append(11)

# 링크드 리스트 출력
iterator = my_list.head

while iterator is not None:
  print(iterator.data)
  iterator = iterator.next

"""출력값
2
3
5
7
11
"""
```

  </details>
  <details>
    <summary>링크드 리스트 str 메소드</summary>

# 링크드 리스트 str 메소드

## 링크드 리스트를 문자열로 표현해주는 str 메소드를 정의해보자

```python
class Node:
  """링크드 리스트의 노드 클래스"""

  def __init__(self, data):
    self.data = data # 노드가 저장하는 데이터
    self.next = None # 다음 노드에 대한 레퍼런스

class LinkedList:
  """링크드 리스트 클래스"""
  def __init__(self):
    self.head = None # 링크드 리스트의 가장 앞 노드
    self.tail = None # 링크드 리스트의 가장 뒤 노드

  def append(self, data):
    """링크드 리스트 추가 연산 메소드"""
    new_node = Node(data)

    # 링크드 리스트가 비어 있으면 새로운 노드가 링크드 리스트의 처음이자 마지막 노드다
    if self.head is None:
      self.head = new_node
      self.tail = new_node
    # 링크드 리스트가 비어 있지 않으면
    else:
      self.tail.next = new_node # 가장 마지막 노드 뒤에 새로운 노드를 추가하고
      self.tail = new_node # 마지막 노드를 추가한 노드로 바꿔준다.

  def __str__(self):
    """링크드 리스트를 문자열로 표현해서 리턴하는 메소드"""
    res_str = "|"

    # 링크드 리스트 안의 모든 노드를 돌기 위한 변수, 일단 가장 앞 노드로 정의한다.
    iterator = self.head

    # 링크드 리스트 끝까지 돈다
    while iterator is not None:
      # 각 노드의 데이터를 리턴하는 문자열에 더해준다
      res_str += f" {iterator.data} |"
      iterator = iterator.next # 다음 노드로 넘어간다

    return res_str

# 새로운 링크드 리스트 생셩
linked_list = LinkedList()

# 링크드 리스트에 데이터 추가
linked_list.append(2)
linked_list.append(3)
linked_list.append(5)
linked_list.append(7)
linked_list.append(11)

print(linked_list) # 링크드 리스트 출력
# | 2 | 3 | 5 | 7 | 11 |
```

  </details>
  <details>
    <summary>링크드 리스트 접근 & 탐색</summary>

# 링크드 리스트 접근

## 배열 접근 연산

특정 위치에 저장한 데이터를 가지고 오거나 바꿔주는 연산

## 링크드 리스트 접근 연산

특정 위치에 있는 **노드**를 리턴하는 연산!

배열은 인덱스를 이용해서 데이터가 저장된 주소를 계산할 수 있었지만,

링크드 리스트는 레퍼런스 통해 순서를 저장하기 때문에 한 번에 원하는 위치에 접근할 수 없다.

- 인덱스 **x**에 있는 노드에 접근하려면 **head**에서 다음 노드로 x번 가면 됨!

### 링크드 리스트 접근 연산 메서드(find_node_at)

```python
class Node:
  """링크드 리스트의 노드 클래스"""

  def __init__(self, data):
    self.data = data # 노드가 저장하는 데이터
    self.next = None # 다음 노드에 대한 레퍼런스

class LinkedList:
  """링크드 리스트 클래스"""
  def __init__(self):
    self.head = None # 링크드 리스트의 가장 앞 노드
    self.tail = None # 링크드 리스트의 가장 뒤 노드

  def find_node_at(self, index):
    """링크드 리스트 접근 연산 메소드. 파라미터 인덱스는 항상 있다고 가정"""
    iterator = self.head

    for _ in range(index):
      iterator = iterator.next

    return iterator


  def append(self, data):
    """링크드 리스트 추가 연산 메소드"""
    new_node = Node(data)

    # 링크드 리스트가 비어 있으면 새로운 노드가 링크드 리스트의 처음이자 마지막 노드다
    if self.head is None:
      self.head = new_node
      self.tail = new_node
    # 링크드 리스트가 비어 있지 않으면
    else:
      self.tail.next = new_node # 가장 마지막 노드 뒤에 새로운 노드를 추가하고
      self.tail = new_node # 마지막 노드를 추가한 노드로 바꿔준다.

  def __str__(self):
    """링크드 리스트를 문자열로 표현해서 리턴하는 메소드"""
    res_str = "|"

    # 링크드 리스트 안의 모든 노드를 돌기 위한 변수, 일단 가장 앞 노드로 정의한다.
    iterator = self.head

    # 링크드 리스트 끝까지 돈다
    while iterator is not None:
      # 각 노드의 데이터를 리턴하는 문자열에 더해준다
      res_str += f" {iterator.data} |"
      iterator = iterator.next # 다음 노드로 넘어간다

    return res_str

# 새로운 링크드 리스트 생셩
linked_list = LinkedList()

# 링크드 리스트에 데이터 추가
linked_list.append(2)
linked_list.append(3)
linked_list.append(5)
linked_list.append(7)
linked_list.append(11)

print(linked_list) # 링크드 리스트 출력
# | 2 | 3 | 5 | 7 | 11 |

# 링크드 리스트 노드에 접근(데이터 가져오기)
print(linked_list.find_node_at(3).data)
# 7

# 링크드 리스트 노드에 접근 (데이터 바꾸기)
linked_list.find_node_at(2).data = 13

print(linked_list) # 전체 링크드 리스트 출력
# | 2 | 3 | 13 | 7 | 11 |
```

## 링크드 리스트 접근 시간 복잡도

- 인덱스 **x**에 있는 노드에 접근하려면 **head**에서 다음 노드로 **x**번 가면 됨
- 마지막 노드에 접근하려면 **head**에서 다음 노드로 *n - 1*번 가야 됨.
- 시간 복잡도 = O(n)

# 링크드 리스트 탐색 연산

```python
class LinkedList:
	"""링크드 리스트 클래스"""
  def __init__(self):
    self.head = None # 링크드 리스트의 가장 앞 노드
    self.tail = None # 링크드 리스트의 가장 뒤 노드

  def find_node_with_data(self, data):
	  """링크드 리스트에서 탐색 연산 메소드. 단, 해당 노드가 없으면 None을 리턴한다"""
    iterator = self.head

    while iterator is not None:
      if iterator.data == data:
        return iterator

      iterator = iterator.next

    return None

# 데이터 2를 갖는 노드 탐색
node_with_2 = linked_list.find_node_with_data(2)

if not node_with_2 is None:
    print(node_with_2.data)
else:
    print("2를 갖는 노드는 없습니다")
```

  </details>
  <details>
    <summary>링크드 리스트 삽입 연산</summary>

# 링크드 리스트 삽입 연산

```python
class Node:
	"""링크드 리스트의 노드 클래스"""

  def __init__(self, data):
    self.data = data # 노드가 저장하는 데이터
    self.next = None # 다음 노드에 대한 레퍼런스

class LinkedList:
	"""링크드 리스트 클래스"""
  def __init__(self):
    self.head = None # 링크드 리스트의 가장 앞 노드
    self.tail = None # 링크드 리스트의 가장 뒤 노드

	def insert_after(self, previous_node, data):
    """링크드 리스트 주어진 노두 뒤 삽입 연산 메소드"""
    new_node = Node(data)

    # 가장 마지막 순서에 삽입할 때:
    if previous_node == self.tail:
      self.tail.next = new_node
      self.tail = new_node

    else: # 두 노드 사이에 삽입할 때:
      new_node.next = previous_node.next
      previous_node.next = new_node

  def append(self, data):
    """링크드 리스트 추가 연산 메소드"""
    new_node = Node(data)

    # 링크드 리스트가 비어 있으면 새로운 노드가 링크드 리스트의 처음이자 마지막 노드다
    if self.head is None:
      self.head = new_node
      self.tail = new_node
    # 링크드 리스트가 비어 있지 않으면
    else:
      self.tail.next = new_node # 가장 마지막 노드 뒤에 새로운 노드를 추가하고
      self.tail = new_node # 마지막 노드를 추가한 노드로 바꿔준다.

	def find_node_at(self, index):
	  """링크드 리스트 접근 연산 메소드. 파라미터 인덱스는 항상 있다고 가정"""
	  iterator = self.head

    for _ in range(index):
      iterator = iterator.next

    return iterator

  def __str__(self):
    """링크드 리스트를 문자열로 표현해서 리턴하는 메소드"""
    res_str = "|"

    # 링크드 리스트 안의 모든 노드를 돌기 위한 변수, 일단 가장 앞 노드로 정의한다.
    iterator = self.head

    # 링크드 리스트 끝까지 돈다
    while iterator is not None:
      # 각 노드의 데이터를 리턴하는 문자열에 더해준다
      res_str += f" {iterator.data} |"
      iterator = iterator.next # 다음 노드로 넘어간다

    return res_str

my_list = LinkedList()

my_list.append(2)
my_list.append(3)
my_list.append(5)
my_list.append(7)

print(my_list)
# | 2 | 3 | 5 | 7 |

node_2 = my_list.find_node_at(2) # 인덱스 2에 있는 노드 접근
my_list.insert_after(node_2, 6) # 인덱스 2 뒤에 6 삽입

print(my_list)
# | 2 | 3 | 5 | 6 | 7 |

head_node = my_list.head # 헤드 노드 접근
my_list.insert_after(head_node, 9) # 헤드 노드 뒤에 9 삽입

print(my_list)
# | 2 | 9 | 3 | 5 | 6 | 7 |

```

# prepend: 링크드 리스트 가장 앞 삽입

`insert_after()` 메소드로는 head 노드 앞에 새로운 노드를 추가할 수 없음.

이 문제를 해결해주는 새로운 메소드 `prepend()`를 정의해주자.

```python
class Node:
    """링크드 리스트의 노드 클래스"""
    def __init__(self, data):
        self.data = data  # 실제 노드가 저장하는 데이터
        self.next = None  # 다음 노드에 대한 레퍼런스

class LinkedList:
    """링크드 리스트 클래스"""
    def __init__(self):
        self.head = None  # 링크드 리스트의 가장 앞 노드
        self.tail = None  # 링크드 리스트의 가장 뒤 노드

    def prepend(self, data):
        """링크드 리스트의 가장 앞에 데이터 삽입"""
        new_node = Node(data)
        if self.head == None:
            self.head = new_node
            self.tail = new_node
        else:
            new_node.next = self.head
            self.head = new_node

    def __str__(self):
        """링크드 리스트를 문자열로 표현해서 리턴하는 메소드"""
        res_str = "|"

        # 링크드 리스트 안에 모든 노드를 돌기 위한 변수. 일단 가장 앞 노드로 정의한다.
        iterator = self.head

        # 링크드 리스트 끝까지 돈다
        while iterator is not None:
            # 각 노드의 데이터를 리턴하는 문자열에 더해준다
            res_str += f" {iterator.data} |"
            iterator = iterator.next  # 다음 노드로 넘어간다

        return res_str



# 새로운 링크드 리스트 생성
linked_list = LinkedList()

# 여러 데이터를 링크드 리스트 앞에 추가
linked_list.prepend(11)
linked_list.prepend(7)
linked_list.prepend(5)
linked_list.prepend(3)
linked_list.prepend(2)

print(linked_list)  # 링크드 리스트 출력
# | 2 | 3 | 5 | 7 | 11 |

# head, tail 노드가 제대로 설정됐는지 확인
print(linked_list.head.data)
# 2
print(linked_list.tail.data)
# 11
```

  </details>
  <details>
    <summary>링크드 리스트 삭제</summary>

# 링크드 리스트 삭제

```python
class Node:
	"""링크드 리스트의 노드 클래스"""

  def __init__(self, data):
    self.data = data # 노드가 저장하는 데이터
    self.next = None # 다음 노드에 대한 레퍼런스

class LinkedList:
	"""링크드 리스트 클래스"""
  def __init__(self):
    self.head = None # 링크드 리스트의 가장 앞 노드
    self.tail = None # 링크드 리스트의 가장 뒤 노드

  def append(self, data):
    """링크드 리스트 추가 연산 메소드"""
    new_node = Node(data)

    # 링크드 리스트가 비어 있으면 새로운 노드가 링크드 리스트의 처음이자 마지막 노드다
    if self.head is None:
      self.head = new_node
      self.tail = new_node
    # 링크드 리스트가 비어 있지 않으면
    else:
      self.tail.next = new_node # 가장 마지막 노드 뒤에 새로운 노드를 추가하고
      self.tail = new_node # 마지막 노드를 추가한 노드로 바꿔준다.

	def delete_after(self, previous_node):
    """링크드 리스트 삭제 연산. 주어진 노드 뒤 노드를 삭제한다"""
    # 링크드 리스트에서 노드를 삭제할 때는 지워주는 노드의 데이터를 리턴해주는 것이 관습
    data = previous_node.next.data

    # 지우려는 노드가 tail 노드일 때
    if previous_node.next is self.tail:
      previous_node.next = None
      self.tail = previous_node

    # 두 노드 사이 노드르 지울 때
    else:
      previous_node.next = previous_node.next.next

    return data

	def find_node_at(self, index):
	  """링크드 리스트 접근 연산 메소드. 파라미터 인덱스는 항상 있다고 가정"""
	  iterator = self.head

    for _ in range(index):
      iterator = iterator.next

    return iterator

  def __str__(self):
    """링크드 리스트를 문자열로 표현해서 리턴하는 메소드"""
    res_str = "|"

    # 링크드 리스트 안의 모든 노드를 돌기 위한 변수, 일단 가장 앞 노드로 정의한다.
    iterator = self.head

    # 링크드 리스트 끝까지 돈다
    while iterator is not None:
      # 각 노드의 데이터를 리턴하는 문자열에 더해준다
      res_str += f" {iterator.data} |"
      iterator = iterator.next # 다음 노드로 넘어간다

    return res_str

my_list = LinkedList()

my_list.append(2)
my_list.append(3)
my_list.append(5)
my_list.append(7)
my_list.append(11)

print(my_list)
# | 2 | 3 | 5 | 7 | 11 |

node_2 = my_list.find_node_at(2) # 인덱스 2에 있는 노드 접근
my_list.delete_after(node_2) # 인덱스 2 뒤 데이터 삭제

print(my_list)
# | 2 | 3 | 5 | 11 |

second_to_last_node = my_list.find_node_at(2)
print(my_list.delete_after(second_to_last_node)) # tail 노드 삭제
# 11

print(my_list)
# | 2 | 3 | 5 |

```

# popleft: 링크드 리스트 가장 앞 삭제

```python
class Node:
    """링크드 리스트의 노드 클래스"""
    def __init__(self, data):
        self.data = data  # 실제 노드가 저장하는 데이터
        self.next = None  # 다음 노드에 대한 레퍼런스


class LinkedList:
    """링크드 리스트 클래스"""
    def __init__(self):
        self.head = None  # 링크드 리스트의 가장 앞 노드
        self.tail = None  # 링크드 리스트의 가장 뒤 노드

    def pop_left(self):
        """링크드 리스트의 가장 앞 노드 삭제 메소드. 단, 링크드 리스트에 항상 노드가 있다고 가정한다"""
        data = self.head.data # 지우려는 노드의 데이터 미리 저장

        # 지우려는 데이터가 링크드 리스트의 마지막 남은 데이터일 때
        if self.head is self.tail:
            self.head = None
            self.tail = None

        # 지우려는 노드가 마지막 남은 노드가 아닐 때
        else:
            # 링크드 리스트의 head를 지금 head의 다음 노드로 지정해 준다
            self.head = self.head.next

        return data # 삭제된 노드의 데이털르 리턴한다

    def prepend(self, data):
        """링크드 리스트의 가장 앞에 데이터 삽입"""
        new_node = Node(data)  # 새로운 노드를 만든다

        # 링크드 리스트가 비었는지 확인
        if self.head is None:
            self.tail = new_node
        else:
            new_node.next = self.head  # 새로운 노드의 다음 노드를 head 노드로 정해주고

        self.head = new_node  # 리스트의 head_node를 새롭게 삽입한 노드로 정해준다

    def __str__(self):
        """링크드 리스트를 문자열로 표현해서 리턴하는 메소드"""
        res_str = "|"

        # 링크드 리스트 안에 모든 노드를 돌기 위한 변수. 일단 가장 앞 노드로 정의한다.
        iterator = self.head

        # 링크드 리스트 끝까지 돈다
        while iterator is not None:
            # 각 노드의 데이터를 리턴하는 문자열에 더해준다
            res_str += f" {iterator.data} |"
            iterator = iterator.next # 다음 노드로 넘어간다

        return res_str



# 새로운 링크드 리스트 생성
linked_list = LinkedList()

# 여러 데이터를 링크드 리스트 앞에 추가
linked_list.prepend(11)
linked_list.prepend(7)
linked_list.prepend(5)
linked_list.prepend(3)
linked_list.prepend(2)

# 가장 앞 노드 계속 삭제
print(linked_list.pop_left()) # 2
print(linked_list.pop_left()) # 3
print(linked_list.pop_left()) # 5
print(linked_list.pop_left()) # 7
print(linked_list.pop_left()) # 11

print(linked_list)  # 링크드 리스트 출력
# |
print(linked_list.head)
# None
print(linked_list.tail)
# None
```

  </details>
  <details>
    <summary>링크드 리스트 시간 복잡도</summary>

# 링크드 리스트 시간 복잡도

## 접근

인덱스 x에 있는 데이터에 접근하려면 링크드 리스트의 head 노드부터 x번 다음 노드를 찾아서 가야 됨

원하는 노드에 접근하는 시간은 몇 번째 인덱스인지에 비례

링크드 리스트 안에 있는 노드의 수를 n이라고 하며느 마지막 순서에 있는 노드에 접근해야 되는 최악의 경우는 head 노드에서 총 *n - 1*번 다음 노드로 가야 함

걸리는 시간은 n에 비례하기 때문에 접근 연산은 최악의 경우 **_O(n)_**의 시간 복잡도를 가짐

## 탐색

링크드 리스트의 탐색은 배열을 탐색할 때와 같은 방법. 가장 앞 노드부터 다음 노드를 하나씩 보면서 원하는 데이터를 가지는 노드를 찾음 (선형 탐색).

접근과 마찬가지로 링크드 리스트 안에 찾는 데이터가 없을 때 또는 찾는 데이터가 마지막 노드에 있는 최악의 경우, n개의 노드를 모두 다 봐야 함.

그렇기 때문에 최악의 경우 **_O(n)_**의 시간 복잡도를 가짐

## 삽입/삭제

링크드 리스트의 삽입과 삭제 연산은 배열 삽입과 조금 차이가 있음.

```python
def insert_after(self, previous_node, data):
    """파라미터 data를 데이터로 갖는 새로운 노드를 만들어서 node 파라미터 뒤에 삽입시킨"""
    new_node = Node(data) # 새로운 노드 만들기

    # tail 노드 다음에 새로운 노드를 삽입할 때
    if previous_node == self.tail:
        previous_node.next = new_node
        self.tail = new_node
    # 두 노드 사이에 새로운 노드를 삽입할 때
    else:
        new_node.next = previous_node.next
        previous_node.next = new_node

def delete_after(self, previous_node):
    """파라미터로 받은 노드 다음 노드를 삭제한다. 단, 파라미터 previous노드로 인해서 에러는 안 난다고 가정한다"""
    data = previous_node.next.data

    # 지우려는 노드가 tail 노드일 때
    if previous_node.next == self.tail:
        self.tail = previous_node
        self.tail.next = None
    # 두 노드 사이의 노드를 지울
    else:
        previous_node.next = previous_node.next.next

    return data
```

삽입, 삭제는 그냥 삽입, 삭제할 주변 노드들에 연결된 레퍼런스만 수정함

그러니까 이 연산들이 실행되는 데 걸리는 시간은 특정 값에 비례하지 않고 항상 일정

파라미터로 받는 이 노드가 어떤 순서에 있는 노드든 상관 없이 걸리는 시간은 변하지 않음

**_O(1)_**의 시간 복잡도를 갖는다고 할 수 있음

## 현실적인 삽입/삭제 시간 복잡도

하지만 조금 더 현실적으로 생각해 봐야 함.

삽입과 삭제 연산들은 특정 노드를 넘겨줘서 이 노드 다음 순서에 데이터를 삽입하거나 삭제함

그럼 이 연산들에게 넘겨주는 노드, 파라미터 previous_node를 먼저 찾아야 되는데,

head와 tail 노드는 항상 저장해주기 때문에 빨리 찾을 수 있는데, 나머지 노드들은 탐색이나 접근 연산을 통해서 가지고 와야 함.

사실상 삽입과 삭제 연산은 접근 또는 탐색의 시간 복잡도인 **_O(n)_**을 공유한다고 볼 수 있음

- 접근: O(n)
- 탐색: O(n)
- 원하는 노드에 접근 또는 탐색 + 삽입: **_O(n+1)_**
- 원하는 노드에 접근 또는 탐색 + 삭제: **_O(n+1)_**

## 삽입 삭제 연산 특수 경우 시간 복잡도

아까 언급했듯, head와 tail 노드는 항상 한 번에 찾을 수 있음. 접근하는데 O(1), 연산을 하는 데 O(1)이 걸림.

따라서 이 두 노드와 관련이 있는 삽입이나 삭제 연산들은 O(1)로 할 수 있음

`append`, `prepend`, `pop_left` 메소드를 살펴보면 head노드와 tail 노드를 한 번에 가지고 와서 레퍼런스를 바꿔줌

```python
def pop_left(self):
    """링크드 리스트의 가장 앞 노드를 삭제해주는 메소드, 단 링크드 리스트에 항상 노드가 있다고 가정한다"""
    data = self.head.data  # 삭제할 노드를 미리 저장해놓는다

    # 지우려는 데이터가 링크드 리스트의 마지막 남 데이터일 때
    if self.head is self.tail:
        self.head = None
        self.tail = None
    else:
        self.head = self.head.next

    return data  # 삭제된 노드의 데이터를 리턴한다

def prepend(self, data):
    """링크드 리스트의 가장 앞에 데이터 삽입"""
    new_node = Node(data)  # 새로운 노드를 만든다

    # 링크드 리스트가 비었는지 확인
    if self.head is None:
        self.tail = new_node
    else:
        new_node.next = self.head   # 새로운 노드의 다음 노드를 head 노드로 정해주고

    self.head = new_node   # 리스트의 head_node를 새롭게 삽입한 노드로 정해준다

def append(self, data):
    """파라미터로 받은 데이터를 갖는 노드를 생성한다"""
    new_node = Node(data)

    # 링크드 리스트가 비어 있으면 새로운 노드가 링크드 리스트의 처음이자 마지막 노드다
    if self.head == None:
        self.head = new_node
        self.tail = new_node
    # 링크드 리스트가 비어 있지 않으면
    else:
        self.tail.next = new_node  # 가장 마지막 노드 뒤에 새로운 노드를 추가하고
        self.tail = new_node  # 마지막 노드를 추가한 노드로 바꿔준다
```

링크드 리스트 안에 몇 개의 노드가 있든 상관없이, 항상 한 번에 받아와서 레퍼런스를 바꿔줌

- 가장 앞에 접근 + 삽입: **_O(1+1)_**
- 가장 앞에 접근 + 삭제: **_O(1+1)_**
- 가장 뒤에 접근 + 삽입: **_O(1+1)_**

양 끝에서 하는 삽입/삭제 연산들 중 유일하게 tail 노드를 삭제하는 경우는 빠졌음

tail 노드를 삭제하기 위해서는 바로 전 node가 필요한데, 이 노드를 찾으려면 head 노드에서 *n - 2*번 다음 노드로 가야 됨.

접근하는 데에 **_O(n-2)_**, 그러니까 **_O(n)_**의 시간 복잡도가 걸림. 접근한 노드에서 다음 노드를 삭제하는 건 **_O(1)_**이 걸림

그러니까 tail 노드 전 노드에 접근해서 tail 노드를 삭제하는 건 O(n+1), 결국 O(n)임

- 뒤에서 두 번째 노드(tail 노드 전 노드) 접근 + 삭제: **_O(n+1)_**

링크드 리스트 가장 뒤 노드 삭제 연산은 나머지 세 연산만큼 효율적으로 할 수 없음

  </details>

</details>

<details>
  <summary>3-2) 더블리 링크드 리스트</summary>

  <details>
    <summary>더블리 링크드 리스트 & 겹치는 메소드</summary>
  
# 더블리 링크드 리스트

## 싱글리 링크드 리스트

각 노드가 다음 노드의 레퍼런스만 저장

## 더블리 링크드 리스트

각 노드가 앞 노드와 뒤 노드의 레퍼런스를 모두 가짐

- 전 노드에 대한 레퍼런스 prev

### 더블리 링크드 리스트의 노드 클래스 생성

```python
class Node:
  """더블리 링크드 리스트 노드"""
  def __init__(self, data):
    self.data = data
    self.next = None
    self.prev = None
```

### 더블리 링크드 리스트 클래스 생성

```python
# 싱글리 링크드 리스트 클래스와 동일
class LinkedList:
  """더블리 링크드 리스트"""
  def __init__(self):
    self.head = None
    self.tail = None
```

# 더블리 링크드 리스트 겹치는 메소드

## 더블리 링크드 리스트 겹치는 연산들

더블리 링크드 리스트는 `init` 메소드 말고도 싱글리 리스트에서 안 바꿔도 되는 메소드들이 좀 있음

`find_node_at`(접근 연산), `find_node_with_data`(탐색 연산), 그리고 `str` 메소드가 겹침

### 접근

```python
def find_node_at(self, index):
    """링크드 리스트 접근 연산 메소드. 파라미터 인덱스는 항상 있다고 가정한다"""

    iterator = self.head  # 링크드 리스트를 돌기 위해 필요한 노드 변수

    # index 번째 있는 노드로 간다
    for _ in range(index):
        iterator = iterator.next

    return iterator
```

### 탐색

```python
def find_node_with_data(self, data):
    """링크드 리스트에서 주어진 데이터를 갖고있는 노드를 리턴한다. 단, 해당 노드가 없으면 None을 리턴한다"""
    iterator = self.head  # 링크드 리스트를 돌기 위해 필요한 노드 변수

    while iterator is not None:
        if iterator.data == data:
            return iterator

        iterator = iterator.next

    return None
```

### `str` 메소드

```python
def __str__(self):
    """링크드 리스트를 문자열로 표현해서 리턴하는 메소드"""
    res_str = "|"

    # 링크드 리스트 안에 모든 노드를 돌기 위한 변수. 일단 가장 앞 노드로 정의한다.
    iterator = self.head

    # 링크드 리스트 끝까지 돈다
    while iterator is not None:
        # 각 노드의 데이터를 리턴하는 문자열에 더해준다
        res_str += f" {iterator.data} |"
        iterator = iterator.next  # 다음 노드로 넘어간다

    return res_str
```

  </details>

  <details>
    <summary>더블리 링크드 리스트 추가 연산</summary>

# 더블리 링크드 리스트 추가 연산

## 추가 연산 메소드 정의 (append)

```python
class Node:
  """더블리 링크드 리스트 노드"""
  def __init__(self, data):
    self.data = data
    self.next = None
    self.prev = None

class LinkedList:
  """더블리 링크드 리스트 클래스"""
  def __init__(self):
    self.head = None
    self.tail = None

  def append(self, data):
    """링크드 리스트 추가 연산 메소드"""
    new_node = Node(data) # 새로운 데이터를 저장하는 노드

    # 링크드 리스트가 비어 있는 경우
    if self.head is None:
      self.head = new_node
      self.tail = new_node

    else: # 링크드 리스트에 데이터가 이미 있는 경우
      self.tail.next = new_node
      new_node.prev = self.tail
      sefl.tail = new_node

  def fine_node_at(self, index):
    """링크드 리스트 접근 연산 메소드. 파라미터 인덱스는 항상 있다고 가정"""
    iterator = self.head # 연결 리스트를 돌기 위해 필요한 노드 변수

    # index 번째 있는 노드로 간다
    for _ in range(index):
      iterator = iterator.next

    return iterator

  def find_node_with_data(self, data):
    """링크드 리스트에서 주어진 데이터를 갖고 있는 노드를 리턴한다. 단, 해당 노드가 없으면 None을 리턴한다"""
    iterator = self.head # 링크드 리스트를 돌기 위해 필요한 노드 변수

    while iterator is not None:
      if iterator.data == data:
        return iterator

      iterator = iterator.next

    return None

  def __str__(self):
    """링크드 리스트를 문자열로 표현해서 리턴하는 메소드"""
    res_str = "|"

    # 링크드 리스트 안에 모든 노드를 돌기 위한 변수. 일단 가장 앞 노드로 정의한다.
    iterator = self.head

    # 링크드 리스트 끝까지 돈다
    while iterator is not None:
      # 각 노드의 데이터를 리턴하는 문자열에 더해준다.
      res_str += f" {iterator.data} |"
      iterator = iterator.next # 다음 노드로 넘어간다

    return res_str
```

## 메소드 동작 확인

```python
# 빈 링크드 리스트 정의
my_list = LinkedList()

# 링크드 리스트에 데이터 추가
my_list.append(2)
my_list.append(3)
my_list.append(5)
my_list.append(7)

print(my_list)
# | 2 | 3 | 5 | 7 |
```

  </details>
  <details>
    <summary>더블리 링크드 리스트 삽입 연산</summary>

# 더블리 링크드 리스트 삽입 연산 개념

```python
def insert_after(self, previous_node, data):
	"""더블리 링크드 리스트 삽입 연산"""
	new_node = Node(data)

	#1) tail 노드 뒤에 삽입 하는 경우
		self.tail 노드의 next에 new_node 지정
		self.tail 노드에 new_node 할당
	#2) 두 노드 사이에 삽입하는 경우
		new_node.prev에 previous_node 할당
		new_node.next에 previous_node.next 할당

		previous 노드의 다음 노드의 prev에 new_node 할당
		previous 노드의 next에 new_node 할당

```

# 더블리 링크드 리스트 삽입 연산 구현

## `insert_after()` 메소드 구현

```python
class Node:
    """링크드 리스트의 노드 클래스"""
    def __init__(self, data):
        self.data = data  # 실제 노드가 저장하는 데이터
        self.next = None  # 다음 노드에 대한 레퍼런스
        self.prev = None  # 전 노드에 대한 레퍼런스


class LinkedList:
    """링크드 리스트 클래스"""
    def __init__(self):
        self.head = None  # 링크드 리스트의 가장 앞 노드
        self.tail = None  # 링크드 리스트의 가장 뒤 노드

    def insert_after(self, previous_node, data):
        """링크드 리스트 추가 연산 메소드"""
        new_node = Node(data)

        # tail 노드 뒤에 삽입하는 경우
        if previous_node is self.tail:
            self.tail.next = new_node
            self.tail = new_node

        # 두 노드 사이에 삽입하는 경우
        else:
            new_node.prev = previous_node
            new_node.next = previous_node.next

            previous_node.next.prev = new_node
            previous_node.next = new_node

    def find_node_at(self, index):
        """링크드 리스트 접근 연산 메소드. 파라미터 인덱스는 항상 있다고 가정한다"""

        iterator = self.head # 링크드 리스트를 돌기 위해 필요한 노드 변수

        # index 번째 있는 노드로 간다
        for _ in range(index):
            iterator = iterator.next

        return iterator

    def append(self, data):
        """링크드 리스트 추가 연산 메소드"""
        new_node = Node(data)  # 새로운 노드 생성

        # 빈 링크드 리스트라면 head와 tail을 새로 만든 노드로 지정
        if self.head is None:
            self.head = new_node
            self.tail = new_node
        # 이미 노드가 있으면
        else:
            self.tail.next = new_node  # 마지막 노드의 다음 노드로 추가
            new_node.prev = self.tail
            self.tail = new_node  # 마지막 노드 업데이

    def __str__(self):
        """링크드 리스트를 문자열로 표현해서 리턴하는 메소드"""
        res_str = "|"

        # 링크드 리스트 안에 모든 노드를 돌기 위한 변수. 일단 가장 앞 노드로 정의한다.
        iterator = self.head

        # 링크드 리스트 끝까지 돈다
        while iterator is not None:
            # 각 노드의 데이터를 리턴하는 문자열에 더해준다
            res_str += " {} |".format(iterator.data)
            iterator = iterator.next  # 다음 노드로 넘어간다

        return res_str
```

## 메소드 동작 확인

```python
# 새로운 링크드 리스트 생성
my_list = LinkedList()

# 새로운 노드 5개 추가
my_list.append(2)
my_list.append(3)
my_list.append(5)
my_list.append(7)
my_list.append(11)

print(my_list)
# | 2 | 3 | 5 | 7 | 11 |

# tail 노드 뒤에 노드 삽입
tail_node = my_list.tail  # 4 번째(마지막)노드를 찾는다
my_list.insert_after(tail_node, 5)  # 4 번째(마지막)노드 뒤에 노드 추가
print(my_list)
# | 2 | 3 | 5 | 7 | 11 | 5 |
print(my_list.tail.data)  # 새로운 tail 노드 데이터 출력
# 5

# 링크드 리스트 중간에 데이터 삽입
node_at_index_3 = my_list.find_node_at(3)  # 노드 접근
my_list.insert_after(node_at_index_3, 3)
print(my_list)
# | 2 | 3 | 5 | 7 | 3 | 11 | 5 |

# 링크드 리스트 중간에 데이터 삽입
node_at_index_2 = my_list.find_node_at(2)  # 노드 접근
my_list.insert_after(node_at_index_2, 2)
print(my_list)
# | 2 | 3 | 5 | 2 | 7 | 3 | 11 | 5 |
```

# 더블리 링크드 리스트 prepend 메소드

## `prepend()` 메소드 구현

```python
class Node:
    """링크드 리스트의 노드 클래스"""
    def __init__(self, data):
        self.data = data  # 실제 노드가 저장하는 데이터
        self.next = None  # 다음 노드에 대한 레퍼런스
        self.prev = None  # 전 노드에 대한 레퍼런스


class LinkedList:
    """링크드 리스트 클래스"""
    def __init__(self):
            self.head = None  # 링크드 리스트 가장 앞 노드
            self.tail = None  # 링크드 리스 가장 뒤 노드

    def prepend(self, data):
        """링크드 리스트 가장 앞에 데이터를 추가시켜주는 메소드"""
        new_node = Node(data)

				# 링크드 리스트가 비어 있는 경우
        if self.head is None:
            self.head = new_node
            self.tail = new_node

				# 이미 head 노드가 존재하는 경우(링크드 리스트가 비어있지 않은 경우)
        else:
            new_node.next = self.head
            self.head.prev = new_node
            self.head = new_node


    def __str__(self):
        """링크드 리스트를 문자열로 표현해서 리턴하는 메소드"""
        res_str = "|"

        # 링크드 리스트 안에 모든 노드를 돌기 위한 변수. 일단 가장 앞 노드로 정의한다.
        iterator = self.head

        # 링크드 리스트 끝까지 돈다
        while iterator is not None:
            # 각 노드의 데이터를 리턴하는 문자열에 더해준다
            res_str += " {} |".format(iterator.data)
            iterator = iterator.next  # 다음 노드로 넘어간다

        return res_str
```

## 메소드 동작 확인

```python
# 새로운 링크드 리스트 생성
my_list = LinkedList()

# 여러 데이터를 링크드 리스트 앞에 추가
my_list.prepend(11)
my_list.prepend(7)
my_list.prepend(5)
my_list.prepend(3)
my_list.prepend(2)

print(my_list) # 링크드 리스트 출력
# | 2 | 3 | 5 | 7 | 11 |

# head, tail 노드가 제대로 설정됐는지 확인
print(my_list.head.data)
# 2
print(my_list.tail.data)
# 11
```

  </details>
  <details>
    <summary>더블리 링크드 리스트 삭제 연산</summary>

# 더블리 링크드 리스트 삭제 연산 개념

더블리 링크드 리스트의 노드는 전 노드와 다음 노드에 대한 레퍼런스를 모두 가지고 있음

따라서 지우려는 노드 하나만 있으면 전 노드와 다음 노드에 모두 접근할 수 있음

따라서 더블리 링크드 리스트의 삭제 메소드에는 지우려는 노드의 전 노드가 아니라, 지우려는 노드 하나만 넘겨주면 됨

```python
def delete(self, node_to_delete):
  """더블리 링크드 리스트 삭제 연산"""

  # 1) 지우려는 노드가 링크드 리스트의 마지막 남은 노드일 때
  head 노드와 tail 노드에 None 할당

  # 2) head 노드를 지우려는 경우(마지막 남은 노드가 아님)
  head 노드에 head 노드의 다음 노드 할당
  바뀐 head 노드의 prev에 None 할당

  # 3) tail 노드를 지우려는 경우(마지막 남은 노드가 아님)
  tail 노드에 tail 노드의 전 노드 할당
  바뀐 tail 노드의 next에 None 할당

  # 4) 두 노드 사이에 있는 노드를 지우려는 경우 (가장 일반적)
  지울 노드의 전 노드의 next가 지울 노드의 다음 노드를 가리키게 함
  지울 노드의 다음 노드의 prev가 지울 노드의 전 노드를 가리키게 함
```

4가지 경우 모두, 지우려는 노드만 있으면 어떤 노드인지 상관없이 딱 2개의 레퍼런스만 바꾸면 됨.

시간복잡도: **_O(1)_**

# 더블리 링크드 리스트 삭제 연산 구현

## `delete()` 메소드 구현

```python
class Node:
    """링크드 리스트의 노드 클래스"""
    def __init__(self, data):
        self.data = data  # 실제 노드가 저장하는 데이터
        self.next = None  # 다음 노드에 대한 레퍼런스
        self.prev = None  # 전 노드에 대한 레퍼런스

class LinkedList:
    """링크드 리스트 클래스"""
    def __init__(self):
        self.head = None  # 링크드 리스트의 가장 앞 노드
        self.tail = None  # 링크드 리스트의 가장 뒤 노드

    def delete(self, node_to_delete):
        """더블리 링크드 리스트 삭제 연산 메소드"""
        data = node_to_delete.data # 지울 노드의 데이터 저장

        # 1) 지우려는 노드가 링크드 리스트의 마지막 남은 노드일 때
        if node_to_delete is self.head and node_to_delete is self.tail:
            self.head = None
            self.tail = None

        # 2) head 노드를 지우려는 경우(마지막 남은 노드가 아님)
        elif node_to_delete is self.head:
            self.head = self.head.next
            self.head.prev = None

        # 3) tail 노드를 지우려는 경우(마지막 남은 노드가 아님)
        elif node_to_delete is self.tail:
            self.tail = self.tail.prev
            self.tail.next = None

        # 4) 두 노드 사이에 있는 노드를 지우려는 경우 (가장 일반적)
        else:
            node_to_delete.prev.next = node_to_delete.next
            node_to_delete.next.prev = node_to_delete.prev

        return data # 지워진 노드의 데이터 리턴



    def find_node_at(self, index):
        """링크드 리스트 접근 연산 메소드. 파라미터 인덱스는 항상 있다고 가정한다"""

        iterator = self.head # 링크드 리스트를 돌기 위해 필요한 노드 변수

        # index 번째 있는 노드로 간다
        for _ in range(index):
            iterator = iterator.next

        return iterator

    def append(self, data):
        """링크드 리스트 추가 연산 메소드"""
        new_node = Node(data)  # 새로운 노드 생성

        # 빈 링크드 리스트라면 head와 tail을 새로 만든 노드로 지정
        if self.head is None:
            self.head = new_node
            self.tail = new_node
        # 이미 노드가 있으면
        else:
            self.tail.next = new_node  # 마지막 노드의 다음 노드로 추가
            new_node.prev = self.tail
            self.tail = new_node  # 마지막 노드 업데이

    def __str__(self):
        """링크드 리스트를 문자열로 표현해서 리턴하는 메소드"""
        res_str = "|"

        # 링크드 리스트 안에 모든 노드를 돌기 위한 변수. 일단 가장 앞 노드로 정의한다.
        iterator = self.head

        # 링크드 리스트 끝까지 돈다
        while iterator is not None:
            # 각 노드의 데이터를 리턴하는 문자열에 더해준다
            res_str += " {} |".format(iterator.data)
            iterator = iterator.next  # 다음 노드로 넘어간다

        return res_str
```

## 메소드 동작 확인

```python
# 새로운 링크드 리스트 생성
my_list = LinkedList()

# 새로운 노드 4개 추가
my_list.append(2)
my_list.append(3)
my_list.append(5)
my_list.append(7)

print(my_list)
# | 2 | 3 | 5 | 7 |

# 두 노드 사이에 있는 노드 삭제
node_at_index_2 = my_list.find_node_at(2)
my_list.delete(node_at_index_2)
print(my_list)
# | 2 | 3 | 7 |

# 가장 앞 노드 삭제
head_node = my_list.head
print(my_list.delete(head_node))
# 2
print(my_list)
# | 3 | 7 |

# 가장 뒤 노드 삭제
tail_node = my_list.tail
my_list.delete(tail_node)
print(my_list)
# | 3 |

# 마지막 노드 삭제
last_node  = my_list.head
my_list.delete(last_node)
print(my_list)
# |
```

  </details>
  <details>
    <summary>더블리 링크드 리스트 시간 복잡도</summary>

# 더블리 링크드 리스트 시간 복잡도

- 접근: **_O(n)_**
- 탐색: **_O(n)_**
- 삽입: **_O(1)_**
- 삭제: **_O(1)_**

## 접근 & 탐색 연산

더블리 링크드 리스트의 접근과 탐색 연산은 싱글리 링크드 리스트와 똑같이 함.

head 노드부터 하나씩 다음 노드로 가면서 원하는 위치에 있거나 데이터를 갖고 있는 노드를 찾았음

링크드 리스트의 길이가 n이라고 할 때, 최악의 경우 걸리는 시간은 이 n에 비례하니까 접근과 탐색은 **_O(n)_**이 걸림

## 삽입 & 삭제 연산

삽입 연산은 특정 노드가 주어졌을 때 그 다음 위치에 새로운 노드를 더함. 그냥 앞과 뒤 노드의 레퍼런스 몇 개만 바꿔주면 됨.

링크드 리스트의 길이와 상관 없이 항상 일정함. **_O(1)_**

삭제 연산은 파라미터로 지우려는 노드를 받아서 그 노드를 링크드 리스트에서 지웠음. 이 때는 경우가 4개로 좀 많긴 했지만, 모든 경우 다 그냥 레퍼런스 두 개만 바꿔주면 노드를 지울 수 있음

삽입과 마찬가지로 항상 일정한 시간, **_O(1)_**이 걸림

## 현실적인 시간 복잡도

싱글리 링크드 리스트와 마찬가지로 더블리 링크드 리스트의 삽입과 삭제 연산을 하기 위해서는 특정 노드가 필요함. 그 특정 노드를 접근 또는 탐색한 후에야 삽입과 삭제도 할 수 있음

그래서 현실적으로 더블리 링크드 리스트 연산들은 다음과 같은 시간이 걸림

- 접근: **_O(n)_**
- 탐색: **_O(n)_**
- 원하는 노드에 접근 또는 탐색 + 삽입: **_O(n)_**
- 원하는 노드에 접근 또는 탐색 + 삭제: **_O(n)_**

## 삽입 & 삭제 특수한 경우

링크드 리스트는 head와 tail 노드를 변수로 갖고 있어서 바로 접근할 수 있음. 이 특성을 이용하면 링크드 리스트의 가장 앞과 뒤에 삽입이나 삭제 연산을 할 때 좀 더 효율적으로 할 수 있음

`append`와 `prepend` 메소드를 떠올려 보면, 파라미터를 안 받고 그냥 바로 tail 노드나 head 노드에 접근해서 양 끝에 새로운 데이터를 삽입할 수 있었음

마찬가지로 더블리 링크드 리스트의 `delete` 메소드에 파라미터로 head나 tail 노드를 가지고 와서 넘겨주면 양 끝 데이터를 한 번에 **_O(1)_** 로 삭제할 수 있음

- 가장 앞에 접근 + 삽입: **_O(1)_**
- 가장 앞에 접근 + 삭제: **_O(1)_**
- 가장 뒤에 접근 + 삽입: **_O(1)_**
- 가장 뒤에 접근 + 삭제: **_O(1)_**

## 싱글리 vs 더블리 링크드 리스트 tail 노드 삭제

### 가장 뒤에 접근 + 삭제

- 싱글리 링크드 리스트: **_O(n+1)_**
- 더브리 링크드 리스트: **_O(1+1)_**

싱글리 링크드 리스트의 삭제 연산은 지우려는 노드의 바로 전 위치의 노드를 파라미터로 받음. 그렇기 때문에 tail 노드를 지우기 위해서는 tail 노드 전 노드에 접근해서 이걸 파라미터로 넘겨줘야 함.

맨 뒤 노드 바로 이전 노드에 접근하는 데에 **_O(n)_**이 걸리기 때문에 효율적으로 할 수 없음

더블리 링크드 리스트는 삭제 연산을 할 때 지우려는 노드 자체를 파라미터로 받음. tail 노드는 링크드 리스트의 속성으로 저장하고 있기 때문에 바로 가지고 와서 삭제 연산의 파라미터로 넘겨주면 효율적으로 tail 노드를 삭제할 수 있음. head 노드도 마찬가지로 한 번에 삭제할 수 있음

링크드 리스트를 사용해야 되는 상황에서 **tail 노드를 많이 삭제해야 된다면** 싱글리 링크드 리스트보다 **더블리 링크드 리스트를 사용하는 게 더 효율적**

  </details>
  <details>
    <summary>싱글리 vs 더블리 링크드 리스트</summary>

# 싱글리 vs 더블리 링크드 리스트

## 노드가 갖는 레퍼런스

싱글리 링크드 리스트 노드

- 다음 노드에 대한 레퍼런스만 저장

더블리 링크드 리스트 노드

- 전 노드와 다음 노드에 대한 레퍼런스 둘 다 저장

## 노드에 대한 접근

싱글리 링크드 리스트

- 특정 노드에서 앞에 있는 노드들에 접근할 수 없다!

더블리 링크드 리스트

- 어떤 노드든지 링크드 리스트 안 모든 노드에 접근할 수 있다!

## 추가적 공간 (실제 저장 데이터를 제외한 다른 정보가 저장된 공간)

링크드 리스트에서는 레퍼런스를 저장하는 공간이 추가적 공간

싱글리 링크드 리스트: **_O(n)_**

- 링크드 리스트 안의 레퍼런스 개수: _n - 1_

더블리 링크드 리스트: **_O(n)_**

- 링크드 리스트 안의 레퍼런스 개수: _2n - 2_

두 자료의 추가적 공간에 대한 공간 복잡도는 동일하긴 하지만, 실질적으로는 두 배 정도 차이가 남

평소에는 큰 차이 없이 사용해도 되지만, 조금이라도 공간을 효율적으로 사용하고 싶을 때에는 더블리 링크드 리스트보다 싱글리 링크드 리스트를 사용하는 편이 조금이나마 유리

  </details>

</details>

<details>
  <summary>4) 해시 테이블</summary>

  <details>
    <summary>key - value 데이터 & Direct Access Table</summary>

# key - value 데이터

모든 데이터에 순서 관계가 있는 것은 아님. ex) 호수와 입주민의 관계

이처럼 이미 알고 있는 정보를 이용해서 저장한 정보를 검색할 수 있는 데이터 유형을 **key - value** 라고 함.

- 하나의 **key**와 그 key에 해당하는 **value**를 합쳐서: **key - value** 쌍
- 하나의 **key**에는 하나의 **value**만 있어야 한다!

# Direct Access Table

key를 배열 인덱스로 사용해서 데이터를 저장하고 가져오는 방식 = Direct Access Table

- 효율적으로 key - value 쌍을 저장하고 가져올 수 있다. O(1)
- but, 낭비하는 공간이 많다.
  </details>
  <details>
    <summary>해시 테이블 & 해시 함수</summary>

# 해시 테이블 (Hash Table) 개념

## 해시 함수

특정 값을 원하는 범위의 자연수로 바꿔주는 함수

- key가 아무리 커도 원하는 범위 사이의 자연수로 바꿀 수 있음

## 해시 테이블

해시 함수와 배열을 같이 사용하는 자료구조

key를 바로 인덱스로 사용하지 않고, 해시 함수에 넣어서 리턴된 값을 인덱스로 사용

### 저장

1. 원하는 크기의 배열을 만든다
2. key를 해시 함수에 넣어서, 리턴된 값에 해당하는 배열의 인덱스에 key와 value를 모두 저장

Direct Access Table에서는 key 자체가 인덱스였기 때문에 인덱스에 value만 저장했는데, 해시 테이블에서는 한 인덱스에 key와 value를 모두 저장해 줌

이렇게 하면 배열의 크기가 무한대로 크지 않아도, 그 어떤 key - value 쌍도 배열에 저장할 수 있게 됨

### 접근

저장된 값을 가져올 때에도 마찬가지.

1. key를 해시 함수에 넣어서, 리턴된 값데 해당하는 배열의 인덱스에 있는 value를 가져옴

### 해시 테이블 정리

1. 고정된 크기의 배열을 만든다
2. 해시 함수를 이용해서 key를 원하는 범위의 자연수로 바꾼다
3. 해시 함수 결과 값 인덱스에 key - value 쌍을 저장한다.

# 해시 함수 구현

## 해시 함수의 조건

1. 한 해시 테이블의 해시 함수는 결정론적이어야 된다.
   1. 그 말은 똑같은 key를 넣었을 때는 항상 똑같은 결과가 나와야 한다는 것. 942를 해시 함수를 넣을 때 어쩔 때는 5가 나오고 어쩔 때는 10이 나오면 안 됨. 942를 넣으면 항상 똑같은 결과가 나와야 함
2. 결과 해시값이 치우치지 않고 고르게 나온다.
   1. 그러니까 해시 함수에 101, 204, 302, 711, 942나 아무 숫자를 넣었을 때 항상 40만 나오면 안 된다. 원하는 범위가 0부터 100까지의 자연수면, 이 사이에 아무 두 숫자가 나올 확률이 최대한 비슷해야 됨
3. 빨리 계산할 수 있어야 된다
   1. 해시 테이블은 모든 연산을 할 때마다 해시 함수르 써야 되는데, 해시 함수가 비효율적이면 해시 테이블도 비효율적일 수 밖에 없음

### 해시 함수 만드는 법: 나누기 방식

가장 직관적이면서 쉬운 방법

자연수 key를 해시 테이블의 크기로 나눈 나머지를 리턴하는 함수

```python
def hash_function_remainder(key, array_size):
    """해시 테이블의 key를 나누기 방법으로 0 ~ array_size - 1 범위의 자연수로 바꿔주는 함수"""
    return key % array_size

print(hash_function_remainder(40, 200)) # 40
print(hash_function_remainder(120, 200)) # 120
print(hash_function_remainder(788, 200)) # 188
print(hash_function_remainder(2307, 200)) # 107
```

어떤 키가 들어와도 0 ~ 원하는 정수 범위의 자연수로 바꾸어 줌

### 해시 함수 만드는 법: 곱셈 방식

예시: key가 200, 배열의 크기가 30

1. 먼저 0 < a < 1 인 아무 값 a를 정한다. 일단 임의로 0.6666
2. 그 다음에 이 a에 key를 곱한다. `0.666 x 200 = 133.32`. 이때 정수 부분은 버리고 소수 부분만 남긴다. 0.32가 남는다.
3. 마지막으로 남은 소수 부분에 배열의 크기를 곱해준다. `0.32 * 30 = 9.6`. 이번엔 소수점 부분을 버리고 9만 남긴다.

### 이 방법이 자연수를 리턴하는 이유

a와 key를 곱한 값의 정수 부분을 버리면 그 결과 값은 0과 1 사이의 소수가 나옴. 0과 1 사이의 소수에 테이블의 크기를 곱해 버리면, 다시 0과 테이블 크기 사이의 수가 나옴.

그러니까 항상 0보다 크거나 같고 테이블 크기보다는 작은 숫자가 나옴. 그리고 여기서 소수점 뒷자리를 버리니까 원하는 범위의 자연수를 구할 수 있음

```python
def hash_function_multiplication(key, array_size, a):
    """해시 테이블의 key를 곱셈 방법으로 0 ~ array_size - 1 범위의 자연수로 바꿔주는 함수"""
    temp = a * key # a와 key를 곱한다
    temp = temp - int(temp) # a와 key를 곱한 값의 소숫점 오른쪽 부분만 저장한다

    return int(array_size * temp) # temp와 배열 크기를 곱한 수의 자연수 부분만 리턴한다


print(hash_function_multiplication(40, 200, 0.61426212)) # 114
print(hash_function_multiplication(120, 200, 0.61426212)) # 142
print(hash_function_multiplication(788, 200, 0.61426212)) # 7
print(hash_function_multiplication(2307, 200, 0.61426212)) # 20
```

## 정리

나누기 방법과 곱셈 방법은 해시 함수로 사용할 수 있는 가장 간단한 두 예시.

사실 key를 받아서 원하는 범위의 자연수를 리턴하면서

1. 결정론적 (같은 key를 넣으면 항상 같은 값 리턴)
2. 원하는 범위의 자연수 하나하나가 리턴될 확률이 최대한 비슷해야 함
3. 빨리 계산을 할 수 있어야 함

이 세 조건을 만족하는 아무 함수나 만들면 해시 함수로 이용할 수 있음

# 파이썬 hash 함수

파이썬 언어도 내부적으로 `hash`라는 함수를 제공함. 방금 논한 해시 함수랑은 조금 다름. 파이썬 해시 함수는 파라미터로 받은 값을 그냥 아무 정수로만 바꿔주는 함수임

특정 범위 안에 있는 정수가 아니라, **아무** 정수로 바꿔줌

정수형, 소수형, 문자열 타입에 `hash` 함수를 호출했을 때 나오는 결과를 살펴보자

```python
# 정수 값
print(hash(12345))  # 12345
print(hash(12345))  # 12345

# 다른 정수 값
print(hash(12346))  # 12346
```

```python
# 소수 값
print(hash(15.1234))  # 284541027336970255
print(hash(15.1234))  # 284541027336970255

# 다른 소수 값
print(hash(81.1234))  # 284541027336978513
```

```python
# 문자열
print(hash("파이썬"))  # -8002119629611903017
print(hash("파이썬"))  # -8002119629611903017

# 다른 문자열
print(hash("자바"))  # -8553573703343279427
```

이런 식으로 같은 값을 넣으면 항상 같은 정수를 리턴해주는 함수이다. 이때 중요한 점은 `hash` 함수에 서로 다른 두 값을 파라미터로 넣었을 때 같은 정수가 리턴될 수 없다는 것이다.

데이터를 **자신만의 고유한 정수 값**으로 바꿔주는 함수임

지금까지는 해시 함수의 key를 정수형으로만 생각했음. 다른 타입의 데이터들을 자신만의 고유한 정수 값으로 바꿀 수 있으면 이제 정수 뿐만 아니라 다른 자료형들도 key로 사용할 수 있음.

## `hash` 함수의 한계

파이썬 `hash`함수는 언어 자체적으로는 불변 타입 자료형에만 사용할 수 있음

파이썬의 대표적인 불변 타입 자료형:

- 불린형
- 정수형
- 소수형
- 튜플
- 문자열
  </details>
  <details>
    <summary>해시 테이블 충돌과 Chaining 개념 & Chaining에서 사용하는 링크드 리스트</summary>

# 해시 테이블 충돌과 Chaining 개념

## 해시 테이블 충돌

배열과 해시 함수만으로 해시 테이블을 사용할 수 있으면 좋겠지만, 큰 문제점이 있음.

서로 다른 두 key에 대한 해시 함수가 같을 때, 즉 이미 사용하고 있는 인덱스에 새로운 key - value 쌍을 또 저장해야 되는 경우에 **충돌(Collision)**이 일어났다고 표현함.

## Chaining

직역을 하면 충돌이 일어나면 그 데이터를 쇠사슬처럼 엮겠다는 뜻

- 배열 인덱스에 링크드 리스트 저장해서 충돌 해결!
- Chaining을 할 때엔, 링크드 리스트 노드에 data 대신 key와 value를 저장해 줌.
  - 즉, 각 노드에 key, value, 그리고 next(다음 노드에 대한 레퍼런스) 변수가 저장됨
- 아무리 충돌이 일어나도 링크드 리스트에 새 노드를 추가해주기만 하면, 원하는 key - value 쌍을 모두 저장할 수 있음

# Chaining에서 사용하는 링크드 리스트

더블리 링크드 리스트를 이용해서 해시 테이블을 직접 구현해보자.

노드에 변수 `data` 대신 `key`와 `value`를 저장한다.

## Node 클래스

```python
class Node:
  """링크드 리스트의 노드 클래스"""
  def __init__(self, key, value):
		self.key = key
    self.value = value
    self.next = None # 다음 노드에 대한 레퍼런스
    self.prev = None # 전 노드에 대한 레퍼런스
```

## LinkedList 클래스

링크드 리스트 클래스에서는 필요한 메소드만 가지고 와서 쓰면 됨. 노드 클래스와 마찬가지로 조금씩 고쳐 써야한다.

init 메소드는 바꾸지 않고 쓸 수 있다.

```python
class LinkedList:
  """링크드 리스트 클래스"""
  def __init__(self):
    self.head = None # 링크드 리스트 가장 앞 노드
    self.tail = None # 링크드 리스트 가장 뒤 노드
```

### 탐색 메소드

```python
	def find_node_with_key(self, key):
	  """링크드 리스트에서 주어진 key를 갖고 있는 노드를 리턴한다. 단, 해당 노드가 없으면 None을 리턴한다"""
	  iterator = self.head # 링크드 리스트를 돌기 위해 필요한 노드 변수

	  while iterator is not None:
	    if iterator.key == key:
	      return iterator

	    iterator = iterator.next

	  return None
```

탐색 메소드는 이제 더 이상 특정 data를 갖는 노드를 찾는 게 아니라 특정 key를 갖는 노드를 찾는다. 이에 맞게 링크드 리스트를 처음부터 끝까지 돌면서 원하는 key를 갖는 노드를 리턴해주도록 수정해준다.

### 추가(맨 뒤 삽입) 메소드

```python
	def append(self, key, value):
    """링크드 리스트 추가 연산 메소드"""
    new_node = Node(key, value)

    # 빈 링크드 리스트라면 head와 tail을 새로 만든 노드로 지정
    if self.head is None:
      self.head = new_node
      self.tail = new_node

    # 이미 노드가 있다면
    else:
      self.tail.next = new_node # tail의 다음 노드로 추가
      new_node.prev = self.tail
      self.tail = new_node # tail 업데이트
```

추가 메소드 `append`는 이제 파라미터로 data 변수 대신 key와 value를 받는다. 링크드 리스트에 데이터를 더해줄 때는 항상 새로운 노드를 만들어 줘야 되는데, 파라미터로 받은 정보를 key와 value를 갖는 새로운 노드를 만들어 준다. 새 노드를 링크드 리스트에 연결해주는 부분 코드는 똑같다.

### 삭제 메소드

```python
	def delete(self, node_to_delete):
    """더블리 링크드 리스트 삭제 연산 메소드"""

    # 링크드 리스트에서 마지막 남은 데이터를 삭제할 때
    if node_to_delete is self.head and node_to_delete is self.tail:
      self.head = None
      self.tail = None

    # 링크드 리스트 가장 앞 데이터 삭제할 때
    elif node_to_delete is self.head:
      self.head = self.head.next
      self.prev = None

    # 링크드 리스트 가장 뒤 데이터 삭제할 때
    elif node_to_delete is self.tail:
      self.tail = self.tail.prev
      self.tail.next = None

    # 두 노드 사이에 있는 데이터 삭제할 때
    else:
      node_to_delete.prev.next = node_to_delete.next
      node_to_delete.next.prev = node_to_delete.prev
```

원래 링크드 리스트 삭제 메소드에서는 노드를 삭제할 때 삭제하는 노드의 데이터를 리턴해줬는데, 이 부분을 빼줬다.

나머지 부분은 바꿀 필요가 없다. 더블리 링크드 리스트 삭제 메소드는 어차피 노드가 주어졌을 때 그 노드를 링크드 리스트에서 삭제해주기 때문에, 기존 data 변수나 key, value 변수와 전혀 관계가 없는 메소드이기 때문에 나머지 코드를 바꿔줄 필요가 없다.

### 문자열 메소드

문자열 메소드는 출력 형식을 조금 바꿔준다.

```python
def __str__(self):
    """링크드 리스트를 문자열로 표현해서 리턴하는 메소드"""
    res_str = ""

    # 링크드 리스트 안에 모든 노드를 돌기 위한 변수, 일단 가장 앞 노드로 정의한다.
    iterator = self.head

    # 링크드 리스트 끝까지 돈다.
    while iterator is not None:
      # 각 노드의 데이터를 리턴하는 문자열에 더해준다.
      res_str += f"{iterator.key}: {iterator.value}\n"
      iterator = iterator.next # 다음 노드로 넘어간다

    return res_str
```

원래는 링크드 리스트에 2, 3, 5, 7, 11이 들어있으면 이런 식으로 링크드 리스트의 모든 data 변수를 한 줄에 출력했음

```python
# | 2 | 3 | 5 | 7 | 11 |
```

이제는 key - value 쌍을 저장하니까 출력 형식을 바꿔준다.

링크드 리스트에 101: "최지웅", 204: "강영훈", 305: "성태호" 가 들어있다고 하면, 아래와 같이 이 링크드 리스트를 출력했을 때 한 줄에 key - value 쌍 하나씩 나오도록 바꿔준 것이다.

```python
# 101: 최지웅
# 204: 강영훈
# 305: 성태호
```

  </details>
  <details>
    <summary>Chaining을 쓰는 해시 테이블 탐색, 삽입, 삭제 연산 & 평균 시간 복잡도</summary>

# Chaining을 쓰는 해시 테이블 탐색 연산

## 해시 테이블 탐색

해시 테이블에는 배열과 링크드 리스트처럼 데이터의 순서 관계를 저장하지 않기 때문에, 접근 연산이 없다. 대신 탐색 연산을 사용

배열과 링크드 리스트 탐색 연산은 원하는 조건에 해당하는 (원하는 data를 가지고 있는) 데이터를 찾아내는 데에 사용되는데, 해시 테이블의 탐색 연산은 주어진 **key에 해당하는 value**를 찾는다

## 해시 테이블 탐색 연산 과정과 시간 복잡도

1. 해시 함수 계산: **_O(1)_**
2. 배열 인덱스 접근: **_O(1)_**
3. 링크드 리스트 탐색: 최악의 경우(모든 데이터가 이 링크드 리스트에 들어가 있을 때) **_O(n)_**

### 해시 테이블 탐색 연산의 시간 복잡도: **_O(n)_**

# Chaining을 쓰는 해시 테이블 삽입 연산

## 해시 테이블 삽입

> 하나의 key에는 하나의 value만!

- key - value 데이터 쌍을 저장, 또는 수정

## 삽입 연산 시간 복잡도

1. 해시 함수 계산: **_O(1)_**
2. 배열 인덱스 접근: **_O(1)_**
3. 링크드 리스트 노드 탐색: **_O(n)_**
4. 링크드 리스트 저장 / 노드 수정: **_O(1)_**

### 해시 테이블 삽입 연산의 시간 복잡도: _O(n)_

# Chaining을 쓰는 해시 테이블 삭제 연산

## 해시 테이블 삭제

- 주어진 key에 대한 key - value 데이터 쌍 삭제

## 삭제 연산 시간 복잡도

1. 해시 함수 계산: **_O(1)_**
2. 배열 인덱스 접근: **_O(1)_**
3. 링크드 리스트 노드 탐색: **_O(n)_**
4. 링크드 리스트 노드 삭제: **_O(1)_**

### 해시 테이블 삭제 연산의 시간 복잡도: _O(n)_

# Chaining을 쓰는 해시 테이블 평균 시간 복잡도

해시 테이블의 탐색, 저장, 삭제 연산은 **_O(n)_**의 시간 복잡도를 가진다. 세 연산 모두 key를 이용해서 저장된 링크드 리스트 노드를 탐색하는 과정을 포함하는데, 링크드 리스트 탐색 연산은 링크드 리스트의 길이에 비례한다.

해시 테이블이 사용하는 링크드 리스트의 길이가 가장 긴 경우는, 저장하는 모든 key - value 쌍이 하나의 링크드 리스트에 저장되는 경우이다. 해시 테이블에 저장된 key - value 쌍의 수가 *n*이라고 하면 길이가 *n*인 링크드 리스트를 탐색하는 데 걸리는 시간은 **_O(n)_**이다. 세 연산 모두 링크드 리스트를 탐색하는 단계를 포함하기 때문에, 세 연산은 최악의 경우 **_O(n)_**이 걸린다.

근데 해시 테이블의 모든 key - value 쌍이 모두 같은 링크드 리스트에 저장되는 건 거의 일어나지 않는 일일텐데, 이걸 이용해서 해시 테이블의 연산들의 시간 복잡도를 평가하는 건 불공평하다.

동적 배열 추가 동작은 분할 상환 분석을 이용해서 조금 더 합리적으로 시간 복잡도를 구했다. 이번에는 최악의 경우만으로 연산의 효율성을 평가하는 게 불공평할 때 사용하는 방법 중 하나인 **평균 시간 복잡도**를 이용해서 해시 테이블 연산들을 분석해 보자.

## 해시 테이블 연산 분해 분석

각 연산의 단계들을 나눠서 보면, 링크드 리스트를 탐색하는 데 **_O(n)_**이 걸리고 나머지 부분들은 다 **_O(1)_**이 걸린다. 그리고 링크드 리스트 탐색이 *n*에 비례하는 이유는 모든 데이터가 하나의 링크드 리스트에 저장된 경우 때문임

배열에 저장된 각 링크드 리스트의 길이가 평균적으로는 *n*이 아니라 다른 값, 예를 들어 *average_length*라는 값이라면 어떨까? 나머지 부분 연산들의 시간 복잡도가 O(1) 밖에 걸리지 않기 때문에 세 연산 모두 링크드 리스트 탐색에 걸리는 시간, **_O(average_length)_**가 걸린다고 할 수 있다.

해시 테이블 연산의 시간 복잡도는 평균적으로 이 *average_length*에 비례하는 것이다.

## 배열에 저장되어 있는 링크드 리스트들의 평균 길이

각 인덱스에 저장된 **링크드 리스트의 평균 길이 = 총 들어 있는 'key - value' 쌍 수 / 배열 인덱스 수**

1. 해시 테이블에 총 들어가 있는 key - value 쌍의 수: _n_
2. 해시 테이블이 사용하는 배열의 크기: _m_

라고 하면, 링크드 리스트들의 평균 길이는 _n/m_ 이라고 할 수 있다.

링크드 리스트들의 평균 길이가 _n/m_ 이면 각 연산들은 "평균적으로 **_O(n/m)_**이 걸린다"라고 표현할 수 있다.

여기에서 중요한 한 가정을 한다. 해시 테이블을 만들 때 항상 충분히 여유롭게 총 저장하는 key - value 쌍 수가 해시테이블이 사용하는 배열의 크기와 비슷하거나 보다 작다고 가정한다.

그러니까 해시 테이블을 사용할 때에는 항상 어느 정도까지는 _n=m_ 과 같이 유지시켜준다는 약속을 하는 것. 이 약속만 지켜주면, 해시 테이블 연산들이 **_O(n/m)_**이 걸리니까 *n=m*을 적용하면 다시 **_O(1)_**이라고 표현할 수 있다.

## 해시 테이블 평균 시간 복잡도 종합

실제로 해시 테이블을 사용할 때는 대부분의 경우 세 연산들이 그냥 O(1)이 걸린다고 가정하고 사용한다.

분할 상환 분석할 때와 마찬가지로 이 연산들의 최악의 경우 시간 복잡도가 O(n)인 것ㅇ느 변하지 않는다. 생각해보면 모든 key - value 쌍이 하나의 인덱스에 저장되는 일이 일어나기 쉽지는 않지만 실제 일어날 수도 있는 일이기는 하다.

이런 혼란을 줄이기 위해서 조금 더 정확하게

**"해시 테이블 삽입, 삭제, 탐색 연산은 최악의 경우 *O(n)*이 걸리지만, 평균적으로는 *O(1)*이 걸린다"**

라고 표현한다.

  </details>
  <details>
    <summary>Chaining을 쓰는 해시 테이블 구현</summary>

# Chaining을 쓰는 해시 테이블 구현

### [HDLL.py](http://hdll.py) (더블리 링크드 리스트가 정의된 파일)

```python
class Node:
    """링크드 리스트의 노드 클래스"""
    def __init__(self, key, value):
        self.key = key
        self.value = value
        self.next = None  # 다음 노드에 대한 레퍼런스
        self.prev = None  # 전 노드에 대한 레퍼런스

class LinkedList:
    """링크드 리스트 클래스"""
    def __init__(self):
        self.head = None  # 링크드 리스트의 가장 앞 노드
        self.tail = None  # 링크드 리스트의 가장 뒤 노드


    def find_node_with_key(self, key):
        """링크드 리스트에서 주어진 데이터를 갖고있는 노드를 리턴한다. 단, 해당 노드가 없으면 None을 리턴한다"""
        iterator = self.head   # 링크드 리스트를 돌기 위해 필요한 노드 변수

        while iterator is not None:
            if iterator.key == key:
                return iterator

            iterator = iterator.next

        return None

    def append(self, key, value):
        """링크드 리스트 추가 연산 메소드"""
        new_node = Node(key, value)

        # 빈 링크드 리스트라면 head와 tail을 새로 만든 노드로 지정
        if self.head is None:
            self.head = new_node
            self.tail = new_node
        # 이미 노드가 있으면
        else:
            self.tail.next = new_node  # 마지막 노드의 다음 노드로 추가
            new_node.prev = self.tail
            self.tail = new_node  # 마지막 노드 업데이

    def delete(self, node_to_delete):
        """더블리 링크드 리스트 삭제 연산 메소드"""

        # 링크드 리스트에서 마지막 남은 데이터를 삭제할 때
        if node_to_delete is self.head and node_to_delete is self.tail:
            self.tail = None
            self.head = None

        # 링크드 리스트 가장 앞 데이터 삭제할 때
        elif node_to_delete is self.head:
            self.head = self.head.next
            self.head.prev = None

        # 링크드 리스트 가장 뒤 데이터 삭제할 떄
        elif node_to_delete is self.tail:
            self.tail = self.tail.prev
            self.tail.next = None

        # 두 노드 사이에 있는 데이터 삭제할 때
        else:
            node_to_delete.prev.next = node_to_delete.next
            node_to_delete.next.prev = node_to_delete.prev

        return node_to_delete.value

    def __str__(self):
        """링크드 리스트를 문자열로 표현해서 리턴하는 메소드"""
        res_str = ""

        # 링크드 리스트 안에 모든 노드를 돌기 위한 변수. 일단 가장 앞 노드로 정의한다.
        iterator = self.head

        # 링크드 리스트 끝까지 돈다
        while iterator is not None:
            # 각 노드의 데이터를 리턴하는 문자열에 더해준다
            res_str += "{}: {}\n".format(iterator.key, iterator.value)
            iterator = iterator.next # 다음 노드로 넘어간다

        return res_str
```

### main.py

```python
from HDLL import LinkedList  # 해시 테이블에서 사용할 링크드 리스트 임포트

class HashTable:
    def __init__(self, capacity):
        self._capacity = capacity  # 파이썬 리스트 수용 크기 저장
        self._table = [LinkedList() for _ in range(self._capacity)]  # 파이썬 리스트 인덱스에 반 링크드 리스트 저장

    def _hash_function(self, key):
        """
        주어진 key에 나누기 방법을 사용해서 해시된 값을 리턴하는 메소드
        주의: key는 파이썬 불변 타입이여야 한다.
        """
        return hash(key) % self._capacity

    def _get_linked_list_for_key(self, key):
        """주어진 key에 대응하는 인덱스에 저장된 링크드 리스트를 리턴하는 메소드"""
        hashed_index = self._hash_function(key)

        return self._table[hashed_index]

    def _look_up_node(self, key):
        """파라미터로 받은 key를 갖고 있는 노드를 리턴하는 메소드"""
        linked_list = self._get_linked_list_for_key(key)

        return linked_list.find_node_with_key(key)

    def look_up_value(self, key):
        """
        주어진 key에 해당하는 데이터를 리턴하는 메소드
        """
        existing_node = self._look_up_node(key)
        if existing_node is not None:
            return self._look_up_node(key).value
        else:
            return None

    def insert(self, key, value):
        """
        새로운 key - value 쌍을 삽입시켜주는 메소드
        이미 해당 key에 저장된 데이터가 있으면 해당 key에 해당하는 데이터를 바꿔준다
        """
        existing_node = self._look_up_node(key)  # 이미 저장된 key인지 확인한다

        if existing_node is not None:
            existing_node.value = value  # 이미 저장된 key면 value만 바꿔주고
        else:
            # 없는 key면 링크드 리스트에 새롭게 삽입시켜준다
            linked_list = self._get_linked_list_for_key(key)
            linked_list.append(key, value)

    def delete_by_key(self, key):
        """주어진 key에 해당하는 key - value 쌍을 삭제하는 메소드"""

        linked_list = self._get_linked_list_for_key(key)
        existing_node = self._look_up_node(key)

        if existing_node is not None:
            linked_list.delete(existing_node)
        else:
            print(f"There is no student named {key}")
						return None


    def __str__(self):
        """해시 테이블 문자열 메소드"""
        res_str = ""

        for linked_list in self._table:
            res_str += str(linked_list)

        return res_str[:-1]



test_scores = HashTable(50) # 시험 점수를 담을 해시 테이블 인스턴스 생성

# 여러 학생들 이름과 시험 점수 삽입
test_scores.insert("현승", 85)
test_scores.insert("영훈", 90)
test_scores.insert("동욱", 87)
test_scores.insert("지웅", 99)
test_scores.insert("신의", 88)
test_scores.insert("규식", 97)
test_scores.insert("태호", 90)

print(test_scores)
# 영훈: 90
# 태호: 90
	# 동욱: 87
# 신의: 88
# 규식: 97
# 현승: 85

# 학생들 시험 점수 삭제
test_scores.delete_by_key("태호")
test_scores.delete_by_key("지웅")
test_scores.delete_by_key("신의")
test_scores.delete_by_key("현승")
test_scores.delete_by_key("규식")

print(test_scores)
# 영훈: 90
# 동욱: 87
```

  </details>
  <details>
    <summary>Open Addressing을 이용한 충돌 해결 & 탐사 방법</summary>

# Open Addressing을 이용한 충돌 해결 & 탐사 방법

## Open Addressing

충돌이 일어났을 때, 다른 비어있는 인덱스를 찾아서 거기에 데이터를 저장하는 방법

비어있는 인덱스를 어떻게 찾을까?

### 선형 탐사 (Linear Probing)

충돌이 일어났을 때 빈 인덱스를 하나씩 순서대로 선형적으로 찾는 방법

- 충돌이 일어났을 때, 해당 인덱스 다음 인덱스부터 한 칸씩 다음 인덱스가 비었는지 확인

### 제곱 탐사 (Quadratic Probing)

해쉬 함수에 key를 넣어서 나온 해당 인덱스에 이미 데이터가 있을 경우, 그 인덱스에 1의 제곱 뒤에 있는 인덱스를 확인하고, 그 인덱스도 비어 있지 않다면 또 2의 제곱 뒤에 있는 인덱스를 확인하는 식으로 빈 인덱스를 탐사하는 방법

ex) 해당 인덱스 = 10

- 10 + 1^(2) = 11 인덱스 확인 → 데이터 있음
- 11 + 2^(2) = 15 인덱스 확인 → 데이터 있음
- 15 + 3^(2) = 24 인덱스 확인 → 비어 있음 → 새로운 key - value 쌍 저장

> 이처럼, 제곱 탐사는 선형적으로 바로 다음 인덱스들을 하나씩 확인하지 않고, 제곱을 한 값들을 이용해서 인덱스를 찾는다.

  </details>
  <details>
    <summary>Open Addressing을 쓰는 해시 테이블 시간 복잡도 & 평균 시간 복잡도</summary>

# Open Addressing을 쓰는 해시 테이블 시간 복잡도

## 연산 세부 단계

- 해시 함수 계산: O(1)
- 배열 인덱스 접근: O(1)
- 원하는 인덱스에 key - value 쌍 저장: O(1)

Open Addressing을 하게 되면 탐색, 삽입, 삭제 연산 모두 인덱스를 찾는 **탐사**를 해야 함.

정확히 말하면, 삽입 연산은 탐사를 통해서 빈 인덱스를 찾고, 탐색과 삭제 연산은 원하는 key를 가진 데이터를 찾는다.

## 탐사 최악의 경우

어떤 경우에 가장 오래 걸릴까?

해당 key에 대해 해시 함수가 리턴한 값보다 1 작은 인덱스를 제외하고 모든 인덱스에 이미 데이터가 있는 경우 혹은 딱 그 자리에 원하는 key를 가진 데이터가 있는 경우, 배열의 모든 인덱스를 하나씩 다 확인해야 한다.

해시 테이블 안에 저장된 key - value 쌍의 개수가 *n*일 때, *n*에 비례하는 시간이 걸리는 것

탐사를 제외한 세 연산의 다른 모든 단계들은 **_O(1)_**이 걸렸는데, 탐사는 최악의 경우 **_O(n)_**이 걸린다.

### Open Addressing 연산 시간 복잡도

- 삽입: **_O(n)_**
- 탐색: **_O(n)_**
- 삭제: **_O(n)_**

# Open Addressing을 쓰는 해시 테이블 평균 시간 복잡도

Open Addressing을 쓰는 해시 테이블 연산에서 최악의 경우는 해시 테이블이 사용하는 배열이 거의 꽉 찼을 경우임. 그런데 해시 테이블이 거의 꽉 차 있는 경우는 잘 일어나지 않고, 대부분의 경우 여유 공간이 넉넉하게 있을 것임

Chaining을 이용하는 해시 테이블과 마찬가지로 최악의 경우로만 분석하면 불공평함

Open Addressing을 사용하는 해시 테이블의 연산들도 **평균 시간 복잡도**로 표현해 보자

## load factor

해시 테이블 연산들을 분석할 때는 load factor라는 것을 사용함. load factor **_α_**는 해시 테이블이 사용하는 배열의 크기를 _m_, 해시 테이블 안에 들어 있는 데이터 쌍의 수를 *n*이라고 할 때: **_α = n/m_**

α는 해시 테이블이 얼마나 차 있는지를 나타내는 변수임

Open Addressing을 쓰는 해시 테이블의 연산들을 분석할 때 이 load factor는 굉장히 중요한 역할을 한다. 해시 테이블 안에 배열의 크기보다 많은 key - value 쌍을 저장할 수 없기 때문에 load factor **_α_**는 항상 1보다 작다고 가정한다.

## 정리

결론적으로 Open Addressing을 사용하는 해시 테이블에서 평균적으로 탐사를 해야 되는 횟수 (기댓값)는 1 / (1 - α) 보다 작다

기댓값이 1 / (1 - α)라는 건 무슨 의미일까? 배열이 총 100칸이라고 하고 90개의 key - value 쌍을 저장하고 있다고 가정하자. 그럼 α = 0.9이다.

기댓값에 α를 대입하면 10이 나온다. 빈 인덱스를 찾기 위해서 평균적으로 인덱스 10개 보다 적은 인덱스를 확인해도 된다는 뜻. 사실 load factor가 0.9도 굉장히 큰 값이고, 만약에 α = 0.5, 즉 햇 ㅣ테이블이 반 정도 차있다고 하면 기댓값은 2보다 작다.

해시 테이블이 반이나 차 있어도 평균적으로 두 개의 인덱스만 확인해봐도 빈칸을 찾을 수 있다는 뜻. 모든 α에 대해서 계산을 하면 성공적으로 원하는 인덱스를 찾는데 확인해야 하는 인덱스 수는 평균적으로 **_O(1)_**이다. 탐사가 _평균적으로_ **_O(1)_**이 걸리는 것이다.

Open Addressing을 사용한 해시 테이블 연산들의 시간복잡도가 O(n)인 이유는 다른 단계들은 **_O(1)_**로 할 수 있는데 탐사가 최악의 경우 **_O(n)_**이 걸리기 때문이었다. 하지만 탐사는 최악의 경우 **_O(n)_**이 걸리지만 평균적으로는 **_O(1)_**의 시간이 걸린다.

따라서 Open Addressing을 사용하든 Chaining을 사용하든 **해시 테이블의 모든 연산들을 평균적으로 _O(1)_**로 할 수 있다. 굉장히 효율적인 것이다.

  </details>

</details>

<details>
  <summary>5) 추상 자료형</summary>

</details>
