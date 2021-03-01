https://www.acmicpc.net/problem/7576  
언어: Python  
solved.ac 기준: Class 3, 실버 1

---

## 통과 코드 1 (실행시간: 2996 ms)

```python
import sys
from collections import deque
read = sys.stdin.readline

def initial_check():
    to_ripe = 0
    for r in range(N):
        for c in range(M):
            if ripe[r][c] == '1':
                q.append((r, c))
            elif ripe[r][c] == '0':
                to_ripe += 1
    return to_ripe

drc = [(-1, 0), (0, 1), (1, 0), (0, -1)]
M, N = map(int, read().split())
ripe = [read().split() for _ in range(N)]
q = deque()

to_ripe = initial_check()
ans = 0

while q and to_ripe:
    for i in range(len(q)):
        r, c = q.popleft()
        for d in range(4):
            nr, nc = r + drc[d][0], c + drc[d][1]
            if 0 <= nr < N and 0 <= nc < M and ripe[nr][nc] == '0':
                ripe[nr][nc] = 1
                to_ripe -= 1
                q.append((nr, nc))
    ans += 1
if to_ripe > 0:
    print(-1)
else:
    print(ans)
```

## 통과 코드 2 (실행시간: 1728ms)

```python
import sys
from collections import deque
read = sys.stdin.readline

def initial_check():
    to_ripe = 0
    for r in range(N):
        for c in range(M):
            if ripe[r][c] == '1':
                q.append((r, c))
            elif ripe[r][c] == '0':
                to_ripe += 1
    return to_ripe

M, N = map(int, read().split())
ripe = [read().split() for _ in range(N)]
q = deque()

to_ripe = initial_check()
ans = 0

while q and to_ripe:
    for i in range(len(q)):
        r, c = q.popleft()
        if r > 0 and ripe[r-1][c] == '0':
            ripe[r-1][c] = 1
            q.append((r-1, c))
            to_ripe -= 1
        if c > 0 and ripe[r][c-1] == '0':
            ripe[r][c-1] = 1
            q.append((r, c-1))
            to_ripe -= 1
        if r < N-1 and ripe[r+1][c] == '0':
            ripe[r+1][c] = 1
            q.append((r+1, c))
            to_ripe -= 1
        if c < M-1 and ripe[r][c+1] == '0':
            ripe[r][c+1] = 1
            q.append((r, c+1))
            to_ripe -= 1
    ans += 1
if to_ripe > 0:
    print(-1)
else:
    print(ans)
```

## 느낀 점

위 두 코드의 **차이점**은 다음과 같다.

주변에 익지 않은 토마토를 확인할 때

- 델타와 반복문을 사용하여 접근 가능한 곳인지 확인하는지,
- 각 방향에 대해서 필요한 조건만을 사용하여 확인하는지

델타와 반복문을 활용하는 방법은 코드는 간결했지만 이 경우 매번 각 방향에 대해서 불필요한 조건까지도 확인해야 하므로 실행 시간이 더 많이 걸렸고,  
각 방향에 대해서 필요한 조건만을 확인하는 경우 분기문이 방향의 개수만큼 필요하므로 코드가 깔끔하지는 않지만, 각 방향에 대해서 쓸데없는 조건을 확인하지 않기 때문에 실행 시간이 보다 빨랐다.

따라서, 앞으로 그래프를 탐색하는 코드를 작성할 때 방향의 개수를 고려하여 코드의 간결함과 실행속도 중 우선순위를 정해서 코드를 작성해야겠다.
