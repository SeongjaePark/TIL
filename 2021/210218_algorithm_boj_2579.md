https://www.acmicpc.net/problem/2579
solved.ac 기준: Class 3, 실버 3

---

## 통과 코드

```python
import sys
read = sys.stdin.readline

N = int(read().rstrip())
stairs = [0] +[int(read().rstrip()) for _ in range(N)] # 0 번째 시작점은 인덱싱 편의를 위한 더미
stairs.append(0) # 마지막 계단은 IndexError를 방지하기 위한 더미

# 모두 다 기록하지 않고 필요한 만큼만 갱신하면서 가져가는 tabulation 방식

# (누적 점수, 연속으로 1칸 오른 수)의 튜플이 각 집합의 원소로 들어갈 것임
current = {(stairs[1], 1)} # 1층
next = [(stairs[2], 1), (0, 2)] # 2층
next_next = [(0, 1), (0, 2)]
for i in range(1, N): # 1부터 마지막 바로 전(N-1) 계단까지 방문하면서
    for record in current:
        # 연속 두 개 계단을 밟지 않은 상태라면
        if record[1] == 1:
            # 다음 기록에 한 칸 이동 추가
            next_record = (record[0] + stairs[i+1], 2)
            # 다음 칸 기록의 값 보다 클 경우에만 갱신 (연속 스텝 수 같은 기록만)
            if next_record[0] > next[1][0]:
                next[1] = next_record
        # 다음 다음 기록에 두 칸 이동 추가
        next_record = (record[0] + stairs[i+2], 1)
        # 다음 다음 칸 기록의 값 보다 클 경우에만 갱신 (연속 스텝 수 같은 기록만)
        if next_record[0] > next_next[0][0]:
            next_next[0] = next_record

    # record 담은 리스트들 갱신
    current = next
    next = next_next
    next_next = [(0, 1), (0, 2)]

# for문이 끝나면 마지막 계단의 기록들이 current에 담겨있을 것임
ans = 0
for record in current:
    if record[0] > ans:
        ans = record[0]

print(ans)
```

## 정리

- 마지막 계단까지 얻을 수 있는 '최대' 점수를 구해야 하며, '연속으로 3개의 계단을 밟을 수 없다'는 제약이 있어서 문제 풀이를 생각해 내는 데에 애를 먹었다.

  - 연속으로 밟은 계단의 수를 기록하여 조건문에 활용
  - 마지막 이전까지의 계단들을 부분 문제로 간주하여 DP 사용

- 처음에는 n 번째 계단까지 밟았을 때의 '누적 점수'와 '연속으로 밟은 계단 수'를 기록할 때 각 층에 해당하는 리스트에 모두 저장을 하여 사용했다.
  - **메모리 초과**
- 전 칸과 전 전 칸의 정보만 남겨둬도 무방하다는 것을 떠올려 필요한 만큼만 남기고 정보를 갱신해가는 방식으로 코드를 수정하였다

  - **메모리 초과**

- 메모리 초과의 주된 원인은 각 층에서 '최대 누적 점수' 가 아닌 정보들까지도 리스트에 저장해 왔던 것이라고 판단해, 각 층에서 '최대 누적 점수'일 경우에만 정보가 갱신되게 하였으며, 이는 '연속으로 밟은 계단 수'가 1인 경우와 2인 경우에 나뉘어 2개씩만 저장되었다.
  - 드디어 메모리 초과를 벗어나고 통과하였다.

### 느낀 점

- 쓸데없이 모든 정보를 다 기록하지 말고, 처음 코드를 짤 때부터 필요한 정보만큼만 기록하도록 하자. 그래야 메모리 초과를 막을 수 있다.

---

### 메모리 초과 코드 1

```python
import sys
read = sys.stdin.readline

N = int(read().rstrip())
stairs = [0] +[int(read().rstrip()) for _ in range(N)] # 0 번째 시작점은 인덱싱 편의를 위한 더미
stairs.append(0) # 마지막 계단은 인덱싱 편의를 위한 더미

# (누적 점수, 연속으로 1칸 오른 수)의 튜플이 각 리스트의 원소로 들어갈 것임
records = [[] for _ in range(N+2)] # 마지막 리스트는 IndexError 방지를 위한 더미
records[0] = [(0, 0)]
for i in range(N):
    for record in records[i]:
        # 연속 두개 계단을 밟지 않은 상태라면
        if record[1] < 2:
            # 다음 기록에 한 칸 이동 추가
            next_record = (record[0] + stairs[i+1], record[1] + 1)
            records[i+1].append(next_record)
        # 다음 다음 기록에 두 칸 이동 추가
        next_record = (record[0] + stairs[i+2], 1)
        records[i+2].append(next_record)

ans = 0
for record in records[N]:
    if record[0] > ans:
        ans = record[0]

print(ans)
```

### 메모리 초과 코드 2

```python
import sys
read = sys.stdin.readline

N = int(read().rstrip())
stairs = [0] +[int(read().rstrip()) for _ in range(N)] # 0 번째 시작점은 인덱싱 편의를 위한 더미
stairs.append(0) # 마지막 계단은 더미

# 모두 다 기록하지 않고 필요한 만큼만 가져가는 tabulation

# (누적 점수, 연속으로 1칸 오른 수)의 튜플이 각 리스트의 원소로 들어갈 것임
current = [(0, 0)]
next = []
next_next = []
for i in range(N): # 0부터 마지막 바로 전(N-1) 계단까지 방문하면서
    for record in current:
        # 연속 두개 계단을 밟지 않은 상태라면
        if record[1] < 2:
            # 다음 기록에 한 칸 이동 추가
            next_record = (record[0] + stairs[i+1], record[1] + 1)
            next.append(next_record)
        # 다음 다음 기록에 두 칸 이동 추가
        next_record = (record[0] + stairs[i+2], 1)
        next_next.append(next_record)

    # record 담은 리스트들 갱신
    current = next
    next = next_next
    next_next = []

# for문이 끝나면 마지막 계단의 기록들이 current에 담겨있을 것임
ans = 0
for record in current:
    if record[0] > ans:
        ans = record[0]
```
