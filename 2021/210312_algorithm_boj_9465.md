https://www.acmicpc.net/problem/9465
solved.ac 기준: Class 4, 실버 2

배너: [godori](https://velog.io/@godori)님이 만드신 [배너 메이커](https://velog.io/@godori/banner-maker) 활용

---

## 통과 코드

```python
import sys
read = sys.stdin.readline


def dp():
    N = int(read().rstrip())
    stickers = [list(map(int, read().split())) for _ in range(2)]
    dp = [[0] * N for _ in range(2)]
    dp[0][0] = stickers[0][0]
    dp[1][0] = stickers[1][0]
    dp[0][1] = dp[1][0] + stickers[0][1]
    dp[1][1] = dp[0][0] + stickers[1][1]
    for i in range(2, N):
        dp[0][i] = max(dp[1][i-1], dp[1][i-2]) + stickers[0][i]
        dp[1][i] = max(dp[0][i-1], dp[0][i-2]) + stickers[1][i]
    print(max(dp[0][-1], dp[1][-1]))


if __name__ == '__main__':
    T = int(read().rstrip())
    for _ in range(T):
        dp()
```

- 메모리: 38716KB, 실행시간: 816ms

- Dynamic Programming 문제라고 판단하고 먼저 아래와 같이 그림을 그려보았다.

<img src="https://images.velog.io/images/gndan4/post/d0c4f1f7-4a12-41aa-b691-88e11e926aa6/IMG_2042.jpeg" alt="Dynamic Programming를 이용한 풀이" width="50%">

- i번째 칸까지의 최고 점수는 i-2번째까지의 반대편의 최고점수와 i-1번째까지의 반대편의 최고점수 중 더 큰 것에 현재의 스티커 점수를 더한 것일 거라고 확신할 수 있었다.

### 느낀 점

- 생각하고 있는 것을 그림으로 간단하게라도 그려보니, 막연하게 풀이방법을 떠올릴 때보다 구현 방법을 더 구체적으로 생각하고 정리할 수 있었다.
