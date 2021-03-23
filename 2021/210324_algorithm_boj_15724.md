https://www.acmicpc.net/problem/15724
solved.ac 기준: 골드 5  
유형: 다이나믹 프로그래밍, 누적 합

---

## 통과 코드

```python
import sys
read = sys.stdin.readline


def solve():
    N, M = map(int, read().split())
    # 영토 정보 map (왼쪽, 위는 0으로 패딩)
    dp = [[0] * (M+1)] + [[0] + list(map(int, read().split())) for _ in range(N)]
    # dp로 (1,1) 부터 해당 위치까지 인구 수의 합 저장이 목적
    # 우선 각 행에서 현재 열까지의 인구 수 합 저장
    for r in range(1, N+1):
        for c in range(2, M+1):
            dp[r][c] += dp[r][c-1]
    # 각 행에서 (1,1)에서 현재 위치까지의 인구 수 합산 값 저장 (이전 행의 정보 반영)
    for r in range(2, N+1):
        for c in range(1, M+1):
            dp[r][c] += dp[r-1][c]

    K = int(read().rstrip())
    for _ in range(K):
        r1, c1, r2, c2 = map(int, read().split())
        # 해당되지 않는 부분 빼주고, 중복으로 감산되는 부분 다시 더해주기
        print(dp[r2][c2] - dp[r1-1][c2] - dp[r2][c1-1] + dp[r1-1][c1-1])


solve()
```

- 실행시간: 772ms
- 해결 방안: 좌상단 시작 지점부터 해당 위치까지의 총합을 해당 위치에 기록해두면, 그 이후부터는 간단 연산만으로도 특정 좌표부터 특정 좌표까지를 포함하는 직사각형 내의 총합을 구할 수 있다.
