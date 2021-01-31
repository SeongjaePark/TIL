참고: [파이썬 공식문서](https://docs.python.org/3/library/stdtypes.html)

<br>

은근히 까먹기 쉬운 파이썬 문자열(String) 메서드에 대해 알아보자.

---

# 문자열의 기본적인 특징

우선 파이썬에서 문자열은 변경할 수 없고(immutable), 순서가 있고(ordered), 순회 가능한(iterable) 자료형이다.

**변경할 수 없다(immutable)**

```python
a = 'hi'
a[0] = 'H'
```

`TypeError: 'str' object does not support item assignment`

기존에 문자열을 할당했던 변수에 새로운 문자열을 할당하는 것은 가능하지만,  
문자열 그 자체를 변경할 수는 없다.

**순서가 있다(ordered)**

```python
a = 'abcde'
print(a[2])
```

`c`

**순회 가능하다(iterable)**

```python
string = 'string'
for char in string:
	print(char, end=' ')
```

`s t r i n g`

<br>

# 조회 및 탐색 메서드

## `.find(x)`

> 해당 문자열에서 x가 등장하는 첫 번째 인덱스를 반환한다.  
> 만약 x가 등장하지 않으면 -1을 반환한다.

```python
string = 'abracadabra'
print(string.find('r'))
```

`2`

> 인자로 문자뿐만 아니라, 문자열을 넘겨줄 수도 있다.  
> 문자열을 인자로 넘길 경우, 그 문자열의 첫 번째 문자가 시작되는 인덱스를 반환한다.

```python
string = 'abracadabra'
print(string.find('cada'))
```

`4`

<br>

## `.index(x)`

`.find(x)` 메서드와 마찬가지로 x의 **첫 번째 위치**를 반환한다.  
`.find(x)` 메서드와 다른 점은 해당 문자가 없으면 **오류**가 발생한다는 것이다.

```python
string = 'egg'
print(string.index('a'))
```

`ValueError: substring not found`

<br>

# 값 변경 메서드

## `.replace(old, new[, count])`

바바꿀 대상 문자를 새로운 문자로 바꿔서 반환한다.  
count를 지정하면 앞에서부터 해당 갯수만큼만 바꾼다.

```python
string = 'abracadabra'
print(string.replace('a', 'A', 3))
```

`AbrAcAdabra`

<br>

## `.strip([chars])`

특정한 문자들을 지정하면 양쪽을 제거하거나 왼쪽을 제거하거나(`.lstrip()`), 오른쪽을 제거한다.(`.rstrip()`)  
인자 없이 실행하면 공백을 제거한다.

```python
print('   spacious   '.strip())

print('www.example.com'.strip('cmowz.'))

```

`spacious`
`example`

<br>

## `.split(sep=None, maxsplit=-1)`

문자열을 특정한 단위로 나누어 리스트로 반환한다.
따로 지정해주지 않을 경우 쉼표(',')를 기준으로 문자열을 나눈다.

maxsplit을 지정해 줄 경우 리스트는 최대 maxsplit + 1 개의 원소
를 갖는다.  
따로 지정해 주지 않거나 -1로 지정할 경우 최대 split 횟수의 제한이 없다.

```python
numbers = '1 2 3'
numbers.split()
```

`['1', '2', '3']`

<br>

## `'separator'.join(iterable)`

특정한 문자열로 만들어 반환한다.  
 반복가능한(iterable) 컨테이너의 요소들을 separator 문자열을 구분자로 합쳐서 하나의 문자열을 반환한다.

```python
print('~'.join(['배', '고', '파']))
```

`배~고~파`

만약 주어진 iterable에 문자열이 아닌 원소가 하나라도 있을 경우 TypeError가 발생한다.

```python
print('~'.join(['벌써', 2021, '년이야']))
```

`TypeError: sequence item 1: expected str instance, int found `

<br>

# 문자 변형 메서드

## `.capitalize()`, `.title()`, `.upper()`

`.capitalize()`: 앞글자를 대문자로 만들어 반환한다.  
`.title()`: 어퍼스트로피나 공백 이후를 대문자로 만들어 반환한다.  
`.upper()`: 모두 대문자로 만들어 반환한다.

```python
print('apple'.capitalize())
print("adam's apple".title())
print('alphabet'.upper())
```

`Apple`  
`Adam'S Apple`  
`ALPHABET`

<br>

## `.lower()`, `.swapcase()`

`.lower()`: 모두 소문자로 만들어 반환한다.  
`.swapcase()`: 대 <-> 소문자로 변경하여 반환한다.

```python
print('ALPHABET'.lower())
print('aBcDe'.swapcase())
```

`alphabet`  
`AbCdE`
