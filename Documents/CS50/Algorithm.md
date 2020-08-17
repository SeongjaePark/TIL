# 4. 알고리즘

[Naver BoostCourse CS50 2019](https://www.edwith.org/boostcourse-cs-050)

<details>
  <summary>1) 검색 알고리즘</summary>

# 학습 목표

주어진 배열 속에서 특정 값을 찾는 방법을 설명할 수 있다.

# 검색 알고리즘

**배열**은 한 자료형의 여러 값들이 메모리 상에 모여 있는 구조이다.

컴퓨터는 이 값들에 접근할 때 배열의 인덱스 하나하나를 접근한다.

만약 어떤 값이 배열 안에 속해 있는지를 찾아 보기 위해서는 배열이 정렬되어 있는지 여부에 따라 아래와 같은 방법을 사용할 수 있다.

# 선형 검색

배열의 인덱스를 처음부터 끝까지 하나씩 증가시키면서 방문하여 그 값이 속하는지를 검사한다.

아래 의사코드와 같이 나타낼 수 있다.

```
For i from 0 to n–1

    If i'th element is 50

        Return true

Return false
```

# 이진 검색

만약 배열이 정렬되어 있다면, 배열 중간 인덱스부터 시작하여 찾고자 하는 값과 비교하며 그보다 작은(작은 값이 저장되어 있는) 인덱스 또는 큰(큰 값이 저장되어 있는) 인덱스로 이동을 반복하면 된다.

아래 의사코드와 같이 나타낼 수 있다.

```
If no items

    Return false

If middle item is 50

    Return true

Else if 50 < middle item

    Search left half

Else if 50 > middle item

    Search right half
```

# 생각해보기

만약 정렬되지 않은 배열이 있다면, 선형 검색이 빠를까 이진 검색이 빠를까?

- 정답을 찾는 속도는 선형 검색이 더 빠를 것이다. 선형 검색은 데이터를 차례대로 계속해서 찾기만 하지만, 이진 검색의 경우 해당 인덱스의 데이터와 찾고자 하는 값을 비교하는 과정을 반복하기 때문이다.
- 또한, 정렬되지 않은 상태에서 이진 검색으로 찾게 되면 데이터가 배열 안에 존재하는 데에도 불구하고 그 데이터가 없는 것으로 잘못 결론을 내릴 수도 있다.
- 하지만 배열이 정렬되어 있는 경우라면 이진 검색이 올바른 결과를 도출하면서도 그 속도가 평균적으로 훨씬 빠를 것이다.

</details>

<details>
  <summary>2) 알고리즘 표기법</summary>

</details>

<details>
  <summary>3) 선형 검색</summary>

</details>

<details>
  <summary>4) 버블 정렬</summary>

</details>

<details>
  <summary>5) 선택 정렬</summary>

</details>

<details>
  <summary>6) 정렬 알고리즘의 실행시간</summary>

</details>

<details>
  <summary>7) 재귀</summary>

</details>

<details>
  <summary>8) 병합 정렬</summary>

</details>
