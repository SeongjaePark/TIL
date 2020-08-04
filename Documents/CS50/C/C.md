# 2. C 언어

[Naver BoostCourse CS50 2019](https://www.edwith.org/boostcourse-cs-050)

<details>
  <summary>1) C 기초</summary>

# C 기초

# 학습 목표

C로 "hello, world"를 출력하는 프로그램을 만들 수 있다.

## C 언어

```c
#include <stdio.h>

int main(void)
{
    printf("hello, world\n");
}
```

C는 아주 오래되고 전통적인 순수 텍스트 기반의 언어이다.

**int main(void)**는 **'시작한다'**의 의미를 가지고 있다고 보면 된다. 앞으로 우리가 작성할 코드 모두는 이 **int main(void) {}**의 중괄호 사이에 작성하게 될 것이다.

C에는 **printf**라는 함수가 있다.

**printf("hello, world\n")**는 스크래치의 "hello, world라고 말하기" 블록과 같은 역할을 한다.

- 글자나 단어, 문장을 적을 때는 **언제나 텍스트에 "" 쌍따옴표로 감싸야 한다**
- 그리고 우리가 일상에서 문장의 끝에 마침표를 붙이는 것처럼 C에서는 **세미콜론(;)**을 붙여야 한다.

**include <stdio.h>**는 "stdio.h"라는 이름의 파일을 찾아서 "printf" 함수에 접근할 수 있도록 해준다.

C로 작성한 코드는 **"파일이름.c"**로 저장해야 한다. (확장자 ".c"는 C로 작성된 코드라는 의미)

마이크로 소프트의 Word처럼 자동적으로 붙여주지 않기 때문에 C의 경우에는 직접 .c를 붙여줘야 한다.

## 컴파일러

우리가 직접 작성한 코드는 **"소스 코드"**라고 불린다. 이를 2진수로 작성된 "머신 코드"로 변환해야 컴퓨터가 이해할 수 있다. 이런 작업을 컴파일러라는 프로그램이 수행해 준다.

<img src="../imgs/compiler.png" width="400">

터미널 창의 명령어 프롬프트에서 "\$" 기호 옆에 우리가 원하는 명령어를 입력하면 된다.

clang hello.c 라는 명령어는 "clang"이라는 컴파일러로 "hello.c"라는 코드를 컴파일하라는 의미이다.

그 결과 **a.out**이라는 파일이 생성된다.

**./a.out** 이라는 명령어를 실행하면 컴퓨터가 현재 디렉토리에 있는 a.out이라는 프로그램을 실행하게 해준다.

</details>

<details>
  <summary>2) 문자열</summary>

</details>

<details>
  <summary>3) 조건문과 루프</summary>

</details>

<details>
  <summary>4) 자료형, 형식 지정자, 연산자</summary>

</details>

<details>
  <summary>5) 사용자 정의 함수, 중첩 루프</summary>

</details>

<details>
  <summary>6) 하드웨어의 한계</summary>

</details>
