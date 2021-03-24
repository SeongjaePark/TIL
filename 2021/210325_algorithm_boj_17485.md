https://www.acmicpc.net/problem/17485  
solved.ac 기준: 골드 5

---

## 통과 코드

```python
import sys
read = sys.stdin.readline


def solve():
    n, m = map(int, read().split())

    # 해당 위치에 올 때까지 최소 연료량을 dp에 저장
    # 다만, 각 위치 당 3개의 값을 리스트 안에 저장하며, 각 리스트에서의 인덱스는 직전 위치 방향을 뜻함
    # 0-> 좌상, 1-> 상, 2-> 우상
    # tabulation
    dp = [[100001] * 3] + [[i] * 3 for i in list(map(int, read().split()))] + [[100001] * 3]
    for r in range(n-1):
        # 좌우를 101로 패딩한 우주 정보 입력 (각 공간에서 소모되는 연료)
        next = [100001] + list(map(int, read().split())) + [100001]
        # 다음 dp를 기록할 임시 변수
        temp_dp = [[100001] * 3] + [[0] * 3 for _ in range(m)] + [[100001] * 3]
        # 각 위치에서 방향이 연속하지 않도록 최솟값 저장
        for c in range(1, m+1):
            # 좌상에서 온 경우
            temp_dp[c][0] = min(dp[c-1][1], dp[c-1][2]) + next[c]
            # 상에서 온 경우
            temp_dp[c][1] = min(dp[c][0], dp[c][2]) + next[c]
            # 우상에서 온 경우
            temp_dp[c][2] = min(dp[c+1][0], dp[c+1][1]) + next[c]
        # 최신 dp 반영
        dp = temp_dp
    # 마지막 달까지 도달 시 각 위치의 최솟값들의 최솟값 출력
    print(min([min(dp[i]) for i in range(1, m+1)]))


solve()
```

- 실행시간: 1580ms
- 해결 방안: 각 위치에 각 위치까지의 최솟값을 직전 위치별로(좌상, 상, 우상) 리스트에 저장 후 이후에 활용하여 이동 방향이 연속하지 않도록 최솟값들을 각 인덱스에 저장
  - 예: 인덱스 0 - 직전 위치가 좌상, 인덱스 1 - 직전 위치가 상, 인덱스 2 - 직전 위치가 우상
- tabulation을 적용하되, 메모리를 아끼기 위해 다음 줄로 넘어갈 때마다 dp를 최신으로 갱신함으로써 dp의 크기를 늘리지 않았음

### 오늘의 교훈

최솟값이 확실하지 않을 땐, 각 조건에 대한 최솟값을 모두 기록해서 다음 단계에 활용하는 방법도 있다.
