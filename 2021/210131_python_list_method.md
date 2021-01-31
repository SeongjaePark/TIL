참고: [파이썬 공식문서](https://docs.python.org/3/library/stdtypes.html)

<br>

은근히 까먹기 쉬운 파이썬 리스트 메서드에 대해 알아보자.

---

# 리스트의 기본적인 특성

변경 가능하고(mutable), 순서가 있고(ordered), 순회 가능함(iterable)

<br>

# 값 추가 및 삭제 메서드

## `.append(x)`

리스트의 끝에 항목을 추가한다.

```python
l = [1, 2, 3]
l.append(4)
print(l)
```

`[1, 2, 3, 4]`

<br>

## `.extend(iterable)`

리스트에 iterable(list, range, tuple, string)의 모든 항목을 이어붙일 수 있다.  
문자열을 넣을 때에는 각 문자가 하나의 원소로 취급되므로 주의해야 한다.

```python
l = [1, 2, 3]
l.extend([4, 5, 6])
print(l)

a = []
a.extend('list')
print(l)
```

`[1, 2, 3, 4, 5, 6]`  
`['l', 'i', 's', 't']`

<br>

## `.insert(i, x)`

리스트의 i 번째 인덱스에 항목 x를 삽입한다. i 번째 인덱스 이후의 모든 요소는 뒤로 밀리게 된다.

```python
numbers = [1, 2, 3, 5]
numbers.insert(-1, 4)
print(numbers)
```

`[1, 2, 3, 4, 5]`

<br>

## `.remove(x)`

리스트에서 x와 값이 같은 첫 번째 항목을 삭제한다.  
만약 해당하는 항목이 없을 경우 `ValueError`를 일으킨다.

```python
numbers = [1, 2, 3]
numbers.remove(2)
print(numbers)

numbers.remove(2)
```

`[1, 3]`  
`ValueError: list.remove(x): x not in list`

<br>

## `.pop(i)`

i 번째 인덱스에 있는 항목을 리스트에서 삭제하고 반환한다.  
i가 지정되지 않으면 리스트의 마지막 항목을 삭제하고 반환한다.

```python
numbers = [1, 2, 3, 4, 5]
print(numbers.pop(2))

numbers.pop()
print(numbers)
```

`3`  
`[1, 2, 4]`

<br>

## `.clear()`

리스트의 모든 항목을 삭제한다.

```
a = ['a', 'a', 'a']
a.clear()
print(a)
```

`[]`

<br>

# 탐색 및 정렬 메서드

<br>

## `.index(x[, start[, end]])`

리스트 에서 x와 값이 같은 첫 번째 항목을 찾아 그 인덱스를 반환한다.  
만약 그 값을 가진 항목이 없으면 `ValueError`를 일으킨다.

옵셔널 파라미터인 start와 end는 슬라이싱 할 때와 마찬가지로 해석된다.  
start는 찾기 시작할 인덱스, end는 그 인덱스 바로 직전까지 찾을 인덱스를 입력한다.

```python
a = [1, 2, 1, 2, 1, 2]
print(a.index(2))
print(a.index(2, 3))
print(a.index(2, 2, 3))
```

`1`  
`3`  
`ValueError: 2 is not in list`

<br>

## `.count(x)`

리스트 안에 있는 x의 개수를 반환한다.

```python
a = [1, 2, 1, 2, 1, 2]
print(a.count(2))
```

`3`

<br>

## `.sort(*, key=None, reverse=False)`

리스트를 정렬한다.  
내장함수 `soted()`와는 달리 **원본 리스트**를 변형시키고, `None`을 반환한다.

key와 reverse는 정렬을 커스터마이징 하는 데에 쓸 수 있다.  
key에는 직접 정의한 함수를 넘겨주어 그 반환 값을 기준으로 리스트를 정렬할 수 있고,  
reverse는 False가 기본값으로, True가 주어지면 오름차순이 아니라 내림차순으로 정렬한다.

```python
a = [3, 2, 1]
print(a.sort())
print(a)
```

`None`  
`[1, 2, 3]`

<br>

key와 reverse 활용 예시

**시험성적 순으로 내림차순 정렬하고, 성적이 같다면 나이 순으로 오름차순 정렬**

```python
def my_func(x):
    return (x[1], -x[2])

scores = [('김철수', 95, 29), ('김민아', 100, 26), ('박지훈', 95, 23), ('김유미', 100, 28)]
scores.sort(key=my_func, reverse=True)
print(scores)
```

`[('김민아', 100, 26), ('김유미', 100, 28), ('박지훈', 95, 23), ('김철수', 95, 29)]`

<br>

## `.reverse()`

리스트를 **현재 상태의** 정반대로 뒤집는다.(정렬이 아니다)

```python
a = [1, 3, 5, 2, 4, 6]
print(a.reverse())
print(a)
```

`None`  
`[6, 4, 2, 5, 3, 1]`
