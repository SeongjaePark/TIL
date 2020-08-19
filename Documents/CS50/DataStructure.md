# 5. 자료구조

[Naver BoostCourse CS50 2019](https://www.edwith.org/boostcourse-cs-050)

<details>
  <summary>1) malloc과 포인터 복습</summary>

# 학습 목표

포인터의 개념과 malloc 함수의 용법을 잘 이해할 수 있다.

# malloc과 포인터 복습

아래와 같은 main 함수 코드가 있다. 여기서 문제가 될 만한 지점을 발견해 보자

```c
#include <stdlib.h>

int main(void)
{
    int *x;
    int *y;

    x = malloc(sizeof(int));

    *x = 42;
    *y = 13;
}
```

main 함수 안의 첫 두 줄에서는 **포인터 x와 y**를 선언한다.

그리고 x에는 **malloc** 함수를 이용해서 int 자료형 크기에 해당하는 메모리를 할당한다.

그 다음에는 x와 y 포인터가 가리키는 지점에 각각 42와 13을 저장한다.

여기서 문제가 될 만한 부분은 \*y = 13이다. y는 포인터로만 선언되었을 뿐이지, 어디를 가리킬 지에 대해서는 아직 정의가 되지 않았다.

따라서 **초기화 되지 않은 \*y**는 프로그램 어딘가를 임의로 가리키고 있을 수도 있다.

따라서 그 곳에 13이라는 값을 저장하는 것이 오류를 발생시킬 수도 있는 것이다.

아래 코드와 같이 `y = x;`라는 코드를 더해주면, y는 x가 가리키는 곳과 동일한 곳을 가리키게 된다.

따라서 `*y = 13;`으로 저장하면 x가 가리키는 곳에도 동일하게 13으로 저장될 것이다.

```c
y = x;

*y = 13;
```

# 생각해보기

포인터를 초기화시키지 않고 값을 저장하면 어떤 오류가 발생할 수 있을까?

- 초기화되지 않는 포인터는 프로그램 어딘가를 임의로 가리키고 있을 수 있는데, 거기에는 쓰레기 값이 있다고 가정해야 된다. 이처럼 없거나 잘못된 주소에 접근하여 값을 저장하려 하면 메모리 문제가 일어날 수 있다.

</details>

<details>
  <summary>2) 배열의 크기 조정하기</summary>

</details>

<details>
  <summary>3) 연결 리스트: 도입</summary>

</details>

<details>
  <summary>4) 연결 리스트: 코딩</summary>

</details>

<details>
  <summary>5) 연결 리스트: 시연</summary>

</details>

<details>
  <summary>6) 연결 리스트: 트리</summary>

</details>

<details>
  <summary>7) 해시 테이블</summary>

</details>

<details>
  <summary>8) 트라이</summary>

</details>

<details>
  <summary>9) 스택, 큐, 딕셔너리</summary>

</details>
