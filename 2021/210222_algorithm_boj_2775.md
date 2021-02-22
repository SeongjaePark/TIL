https://www.acmicpc.net/problem/2775  
언어: Python  
solved.ac 기준: Class 2, 브론즈 2

---

## 통과코드

```python
import sys
read = sys.stdin.readline


def num_of_residents(k, n, memo):
    # base case
    if memo[k-1][n-1]:
        return memo[k-1][n-1]
    elif k == 1:
        return n * (n+1) // 2
    elif n == 1:
        return 1

    # recursive case
    answer = num_of_residents(k, n-1, memo) + num_of_residents(k-1, n, memo)
    memo[k-1][n-1] = answer
    return answer


T = int(read().rstrip())
for t in range(T):
    K = int(read().rstrip())
    N = int(read().rstrip())
    # 거주자 수 기록 memo
    memo = [[0] * N for _ in range(K)]

    print(num_of_residents(K, N, memo))

```

## 정리

- 문제 분류가 수학이라는 것에 너무 집착한 나머지 k층 n호의 거주자 수를 간단한 수식으로 나타낼 수 있다고 믿고 고민하다가 포기했다. 방향을 잘못 잡은 것이다.

- 이후 실행 시간에 대한 별 고민없이 재귀로 코드를 짜서 시간 초과가 났다.

### 시간 초과 코드 1

```python
T = int(input())

def family_n(a, b):
    # base case
    if a == 0:
        return b

    # recursive case
    ans = 0
    for i in range(1, b+1):
        ans += family_n(a-1, i)
    return ans

for _ in range(T):
    a = int(input())
    b = int(input())
    print(family_n(a, b))
```

- 문제에서 요구하는 것이 결국 다음과 같다는 것을 알게 되었다

  - k층 n호의 거주자 수 = (k층 n-1호의 거주자 수) + (k-1층 n호의 거주자 수)
  - 1층 n호의 거주자 수 = n\*(n+1) / 2
  - k층 1호의 거주자 수 = 1

- 이 문제는 부분 문제의 해답을 활용해 문제의 해답을 구하는 Dynamic Programming 방식으로 풀 수 있는 것이다.

- 하지만 또 다시 시간에 대한 별 고민 없이 재귀 코드를 짰고, 이는 DP가 아닌 그냥 재귀였다. 시간 초과가 났다.

### 시간 초과 코드 2

```python
import sys
read = sys.stdin.readline


def num_of_residents(k, n):
    # base case
    if k == 1:
        return n * (n+1) // 2
    elif n == 1:
        return 1

    # recursive case
    return num_of_residents(k, n-1) + num_of_residents(k-1, n)


T = int(read().rstrip())
for t in range(T):
    K = int(read().rstrip())
    N = int(read().rstrip())
    print(num_of_residents(K, N))
```

- DP 방식 중 memoization을 통해 코드를 짰다. (통과 코드)
- 하지만 보다 빠른 정답 코드들을 확인해보니,
  - 다른 사람들은 각 호의 거주자 수를 기록하고
  - 새로운 층에서 각 호의 거주자 수를 다시 갱신하는 방식으로 부분적인 tabulation 방식을 사용하고 있었다.

### 더 빠른 코드

- 코드 제출자: alcks12

```python
import sys
input = sys.stdin.readline

for _ in range(int(input())):
    k = int(input())
    n = int(input())

    people = [i for i in range(n + 1)]

    for i in range(k):
        for j in range(1, n + 1):
            people[j] = people[j] + people[j - 1]

    print(people[-1])
```
