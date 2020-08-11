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

`int main(void)`는 **시작한다**의 의미를 가지고 있다고 보면 된다. 앞으로 우리가 작성할 코드 모두는 이 `int main(void) {}`의 중괄호 사이에 작성하게 될 것이다.

C에는 **printf**라는 함수가 있다.

`printf("hello, world\n")`는 스크래치의 "hello, world라고 말하기" 블록과 같은 역할을 한다.

- 글자나 단어, 문장을 적을 때는 **언제나 텍스트에 "" 쌍따옴표로 감싸야 한다**
- 그리고 우리가 일상에서 문장의 끝에 마침표를 붙이는 것처럼 C에서는 `세미콜론(;)`을 붙여야 한다.

`include <stdio.h>`는 "stdio.h"라는 이름의 파일을 찾아서 "printf" 함수에 접근할 수 있도록 해준다.

C로 작성한 코드는 `"파일이름.c"`로 저장해야 한다. (확장자 ".c"는 C로 작성된 코드라는 의미)

마이크로 소프트의 Word처럼 자동적으로 붙여주지 않기 때문에 C의 경우에는 직접 .c를 붙여줘야 한다.

## 컴파일러

우리가 직접 작성한 코드는 **소스 코드**라고 불린다. 이를 2진수로 작성된 "머신 코드"로 변환해야 컴퓨터가 이해할 수 있다. 이런 작업을 컴파일러라는 프로그램이 수행해 준다.

<img src="../imgs/compiler.png" width="400">

터미널 창의 명령어 프롬프트에서 "\$" 기호 옆에 우리가 원하는 명령어를 입력하면 된다.

clang hello.c 라는 명령어는 "clang"이라는 컴파일러로 "hello.c"라는 코드를 컴파일하라는 의미이다.

그 결과 **a.out**이라는 파일이 생성된다.

**./a.out** 이라는 명령어를 실행하면 컴퓨터가 현재 디렉토리에 있는 a.out이라는 프로그램을 실행하게 해준다.

</details>

<details>
  <summary>2) 문자열</summary>

# 문자열

# 학습 목표

C로 문자열 형식을 가진 변수를 선언하고 출력하는 프로그램을 만들 수 있다.\

# 문자열 다루기

C 언어로 사용자의 이름을 입력으로 받고, 그 사람의 이름을 불러서 인사를 해보자.

CS50 Sandbox에서는 스크래치의 ask 함수와 가장 비슷한 것은 `get_string()` 함수이다. String은 단어나 구절, 문장을 부르는 말이다.

## 변수와 형식지정자

`string answer = get_string("What's your name?\n")`;

사용자의 이름을 받아서 저장할 **변수**를 **answer**라고 정해보자. 변수명은 마음대로 정해도 되지만, 유의해야 할 점은 C는 오래된 언어이기 때문에 변수가 저장하는 **데이터의 종류를 아주 정확하게 명시해줘야 한다**.

그래서 우리는 저장하고자 하는 값의 종류가 **문자열(string)**이라는 것을 알려줘야 한다. 이때 string을 **형식지정자**라고 한다. 컴퓨터에게 "answer"에 들어갈 것은 문자라고 알려주는 것이다.

## 할당 연산자 =

프로그래밍 언어에서 **=**는 오른쪽에 있는 것을 왼쪽으로 **지정**해준다. 이를 할당 연산자라고 한다.

여기서는 **get_string**함수가 사용자의 이름을 반환하면 그 이름을 **answer**이라는 변수에 저장하는 것이다. 이제 컴퓨터의 메모리 어딘가에 사용자의 이름이 저장되어 있는 것이다.

## 출력

`printf("hello, %s\n", answer)`;

이때 유의할 점은 `printf("hello, answer");`이 아니라는 점이다. 이 코드를 실행한다면 answer이 출력되어 hello, answer이 그대로 결과로 나온다.

우리는 answer이라는 변수에 들어있는 이름을 출력해야 하기 때문에 **%**를 사용해준다. 이 때에도 어떤 종류의 인자를 받는지 말해줘야 한다.

우리는 이름이라는 문자열을 받기 때문에 **string**에서의 **s**를 **%** 뒤에 붙여서 인자를 받아준다. 그래서 최종적으로는 `printf("hello, %s\n", answer);`이 되는 것이다

## 코드

```c
#include <cs50.h>
#include <stdio.h>

string answer = get_string("What's your name?\n");
printf("hello, %s\n", answer);
```

가장 위에 포함된 cs50.h 파일 안에 string이라는 문자열 형식과 get_string 이라는 함수에 대한 코드가 포함되어 있다. 이 파일을 포함해야만 전체 코드를 컴파일 하고 실행할 수 있다.

터미널 창에 아래 명령어를 입력하여 컴파일을 할 수 있다.

`clang -o string string.c -lcs50`

여기서 -o string은 string.c를 string.out이라는 머신코드로 저장하도록 하는 명령어이다.

-lcs50은 "link"라는 의미를 지닌 -l이라는 인자에 우리가 추가로 포함한 "cs50" 파일을 합친 것이다. 이를 통해 컴파일시 cs50 파일을 연결하도록 알려줄 수 있다.

다소 복잡한 이런 과정 대신에, 아래 make 명령어를 통해 간단하게 컴파일을 수행할 수도 있다.

`make string`

이와 같이 작성한 코드를 컴파일 하고 실행하면, 사용자에게 입력값을 받고 문장 내에 포함하여 출력하는 프로그램이 된다.

# 생각해보기

"좋아하는 동물을 알려주세요"로 질문하여 동물 이름을 animal이라는 변수에 저장하고, 이를 "내가 좋아하는 동물은"으로 출력해주는 코드를 작성해 보자.

```c
#include <stdio.h>
#include <cs50.h>

int main(void) {
    string answer = get_string("좋아하는 동물을 알려주세요\n");
    printf("내가 좋아하는 동물은 %s입니다\n", answer);
}
```

</details>

<details>
  <summary>3) 조건문과 루프</summary>

# 학습 목표

조건문과 루프를 c로 작성할 수 있다.

## 정수 할당

`int counter = 0;`

여기서 int는 변수가 정수(integer)라는 것을 알려주는 것이고, counter는 변수의 이름, 0은 그 값에 0을 저장(초기화)하는 것이다.

## 변수의 값 1씩 증가

`counter = counter + 1`

counter에 1을 더한 값을 다시 counter에 저장(할당)한다는 의미가 된다.

이를 더 간단하게 아래 두 가지 방식으로 수행할 수도 있다.

`counter += 1;`

`counter ++;`

## 조건문

```c
if (x < y) {
    printf("x is less than y\n");
}
```

`if ()`의 괄호 안에는 검사하고자 하는 **조건**이 들어가고, {} 안에는 조건을 만족할 때 수행하고자 하는 작업이 들어간다. 여기에서는 조건이 true면 "x is less than y"를 출력하라는 것이다.

**else**를 이용해 처음 조건이 아닌 경우에는 다른 어떤 것을 하라고 적어줄 수 있다.

```c
if (x < y) {
    printf("x is less than y\n");
}
else {
    printf("x is not less than y\n");
}
```

이 경우에는 첫 번째 x < y 조건이 False, 즉 x가 y보다 작지 않을 경우에는, "x is not less than y"를 출력하라는 것이다.

**else if**를 통해서 아래와 같이 조건을 추가할 수도 있다.

```c
if (x < y) {
    printf("x is less than y\n");
}
else if (x > y) {
    printf("x is not less than y\n");
}
else if (x == y) {
    printf("x is equal to y\n");
}
```

**==**는 양쪽의 값이 같다를 표현하는 **일치 연산자**

**=**는 오른쪽 값을 왼쪽에 할당하는 **할당 연산자**

3개의 조건문 중 마지막의 경우 사실 물어볼 필요가 없다. x가 y보다 작지도 크지도 않다면 남은 유일한 가능성은 x와 y가 같다는 것이기 때문이다.

따라서 위의 코드를 수정하면 아래와 같다.

```c
if (x < y) {
    printf("x is less than y\n");
}
else if (x > y) {
    printf("x is not less than y\n");
}
else {
    printf("x is equal to y\n");
}
```

이렇게 좀 더 간결하게 만들 수 있다. 이렇듯 얼마나 효율적으로 코딩을 하는지, 혹은 얼마나 적은 메모리나 CPU를 사용해서 수행하는지는 정말 중요하다.

추가로 if, else, else if 뒤에는 세미콜론(;)이 붙지 않은 것을 볼 수 있다. 보통 조건과 같은 것들의 끝에는 세미콜론을 붙이지 않는다.

## 루프

```c
while (true)
{
    printf("hello, world\n");
}
```

먼저 while의 경우 위의 코드와 같이 while () 괄호 안에 조건을 넣고 {} 안에 수행할 작업을 포함시키면 된다. 즉, C에서 루프를 구현하고 싶다면 성립 조건을 정해줘야 한다. 답이 네, 참, 혹은 1로 나올 수 있는 질문을 던져줘야 하는 것이다.

답이 참이 나오게 하는 방법은 여러가지가 있을 수 있지만, 가장 간단한 방법은 그냥 **true**를 적는 것이다.

위의 코드에서는 true라는 항상 참이 되는 조건을 통해 while 루프가 영원히 수행되도로 한다. 따라서 위의 코드는 "hello, world"를 무한정 출력하게 될 것이다.

만약 특정 횟수만큼 작업을 수행하고 싶으면 어떻게 해야할까?

```c
int i = 0;
while (i < 50)
{
    printf("hello, world\n");
    i = i + 1
}
```

counter라는 변수는 너무 긴 단어이다. 그래서 프로그래머들은 무언가를 셀 때 간단하게 정수를 나타내는 **i**를 사용한다. 물론 변수명은 맘대로 적어도 문제는 없다.

따로 변수를 선언해도 되지만 아래와 같이 **for**문을 사용하면 for () 안에 각각 (변수 초기화; 변수 조건; 변수 증가)에 해당하는 코드를 넣어서 간단하게 표현할 수 있다.

즉, 가장 먼저 정수 값을 가지는 i라는 변수를 0으로 초기화하고, i가 50인지 매번 검사를 하고, 이를 만족하면 {} 안의 내용을 수행한 후에, i를 1씩 증가시킨다는 의미이다.

```c
for (int i = 0; i < 50; i = i + 1) {
    printf("hello, world\n");

}
```

while문과 비교하여 코드가 엄청 간단해진 것을 확인할 수 있다.

# 생각해보기

학습한 다양한 방법을 이용하여 "개발공부는 재미있다!"를 10번 출력하는 코드를 작성해보자.

```c
#include <stdio.h>

int main(void) {
    int i = 0;
    while (i < 10) {
        printf("개발공부는 재미있다!\n");
        i++;
    }
}
```

또는

```c
#include <stdio.h>

int main(void) {
    for (int i = 0; i < 10; i++) {
        printf("개발공부는 재미있다!\n");
    }
}
```

## 부울 연산자

부울 연산자는 참과 거짓을 판단하는 **부울 연산식**을 만드는 데 사용된다.

`bool a = d < 5;` true

`bool b = 2 >= 8;` false

`bool c = a && b;` false

`bool d = a || b;` true

`bool e = ~d;` false

## 조건문을 표현하는 다른 방법

## Switch문

조건식의 결과값에 따라 매칭되는 case의 코드를 실행시킨다.

```c
switch (x)
{
    case 1:
        printf("A\n");
        break;
    case 2:
        printf("B\n");
        break;
    default:
        printf("C\n");

}
```

### 3항 연산자

식 하나를 받아서, 식이 참이면 : 기호 왼편의 값으로 계산되고, 거짓이면 오른편의 값으로 계산된다.

```c
int y = (x > 3) ? 2 : 1;
```

위의 식에서 만약 x > 3가 참이면 y는 2가되고, 그렇지 않으면 1이 된다.

</details>

<details>
  <summary>4) 자료형, 형식 지정자, 연산자</summary>

[C 표준 라이브러리 - 위키백과](https://ko.wikipedia.org/wiki/C_표준_라이브러리)

[CS50 라이브러리 문서](https://cs50.readthedocs.io/libraries/cs50/c/)

[입력과 출력2 - c언어 기초](https://opentutorials.org/module/3921/23575)

# 학습 목표

- 다양한 데이터 타입과 형식 지정자를 나타내는 방법을 학습한다.
- 다양한 연산자를 이용하여 조건문을 표현하는 방법을 학습한다.

# 데이터 타입

아래 목록은 변수의 데이터 타입으로 사용할 수 있는 것들이다.

- bool: 불리언 표현, (예) True, False, 1, 0, yes, no
- char: 문자 하나 (예) 'a', 'Z', '?'
- string: 문자열
- int: 특정 크기 또는 특정 비트까지의 정수 (예) 5, 28, -3, 0
- long: 더 큰 크기의 정수
- float: 부동소수점을 갖는 실수 (예) 3.14, 0.0, -28.56
- double: 부동소수점을 포함한 더 큰 실수

* int는 대략 40억까지 셀 수 있기 때문에 40억 개 이상의 데이터를 가진 일부 거대 기업과 같은 상황이 아니면 일반 사용자들은 대부분 정수에 int를 사용한다.

# CS50 라이브러리 내의 get 함수

CS50 라이브러리는 위와 같은 데이터 타입을 입력값으로 받을 수 있는 아래와 같은 함수들을 포함한다.

- get_char
- get_double
- get_float
- get_int
- get_long
- get_string

# 형식 지정자

printf 함수에서는 각 데이터 타입을 위한 형식 지정자를 사용할 수 있다.

- **%c**: char
- **%f**: float, double
- **%i**: int
- **%li**: long
- **%s**: string

# 기타 연산자 및 주석

그 외에도 아래 목록과 같이 다양한 수학 연산자, 논리 연산자, 주석 등이 기호로 정의되어 있다.

- +: 더하기
- -: 빼기
- \*: 곱하기
- /: 나누기
- %: 나머지
- &&: 그리고
- ||: 또는
- //: 주석

# 정수와 실수를 받아서 출력해보기

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int age = get_int("What's your age?\n");
		days = age * 365;
    printf("You are at least %i days old.\n", days);
}
```

`get_int`라는 정수 값을 받아오는 CS50 라이브러리에 있는 함수를 사용한다.

사용자의 나이는 오른쪽에서 왼쪽으로 복사되어 age라는 변수에 저장된다.

그 변수의 종류는 int 정수이다.

days라는 정수 변수에 age에 365를 곱한 수를 저장해준다.

그리고 printf 함수에 이번에는 문자가 아닌 정수이기 때문에 %i로 days의 인자를 받아주고 출력해준다.

더 간단한 코드를 작성해보면,

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int age = get_int("What's your age?\n");
    printf("You are at least %i days old.\n", age * 365);
}
```

이전에 days에 age에 365를 곱한 값을 저장했다.

하지만 엄밀히 말하면 이 행은 필요가 없다.

days 대신 age \* 365를 넣으면 되기 때문이다.

좀 더 극단적으로 줄여보면,

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    printf("You are at least %i days old.\n", get_int(What's your age?\n") * 365);
}
```

age라는 변수를 없애버리고 age \* 365 대신에 get_int 함수를 넣어 365를 곱할 수 있다.

그렇다면 극단적으로 줄여버린 코드가 옳은 것일까?

마지막 코드는 좌우로 너무 길어서 가독서이 떨어진다.

디자인 측면에서는 시선이 왼쪽에서 오른쪽으로 가는 것보다 위에서 아래로 가는 것이 좋다.

무론 이 것은 사람마다 생각이 다르기 때문에 정답은 없다.

하지만 **읽기 편하고 이해하기 쉬운 코드**가 더 선호되는 것 또한 사실이다.

이번에는 실수(float)을 사용해보자.

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    float price = get_float("What's the price?\n");
    printf("Your total is %f. \n", price * 1.0625);
}
```

`get_float` 함수를 사용하여 물건의 가격을 물어보고 가격을 받아 price에 저장해준다.

그런 다음 **세금을 포함한 값을 계산**해서 출력해보자.

총액은 **실수(float)**이므로 %f를 사용해준다.

가격을 100으로 넣어보면 결과값으로 106.250000이 나온다.

하지만 소수점이 6번째 자리까지 나와 보기에 안 좋다.

그럼 이것을 일부분만 나오게 하자. (소수점 2번째 자리까지)

`printf("Your totla is %.2f\n", price * 1.0625);`

이때는 %f 앞에 **'.원하는 자리수'**를 넣어 **%.2f**로 소수점 2번쨰 자리까지 나오게 할 수 있다.

출력을 해보면 106.25로 총액이 좀 더 보기 좋게된 것을 확인할 수 있다.

# 짝수인지 홀수인지 알려주는 코드짜기

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int n = get_int("n: ");

    if (n % 2 == 0)
    {
        printf("even\n");
    }
    else
    {
        printf("odd\n")
    }
}
```

우선 get_int로 사용자들에게 정수인 숫자를 받아서 n에 저장한다.

받은 정수인 숫자가 짝수인지 홀수인지 알아보는 방법은 **2로 나누어 나머지가 0이냐 1이냐**를 보는 것이다.

# 주석

C에서는 //로 주석을 달 수 있다.

```c
//주석이다
```

주석은 이 코드가 무슨 일을 하는지 설명하는 것이다. 주석은 꼭 타인이 아닌 자기 자신에게도 도움이 되는 것으로, 주석으로 잘 설명하는 습관이 중요하다.

# 생각해보기

짝수인지 홀수인지 알려주는 코드짜기에 자신의 스타일 대로 주석을 달아보고 다른 수강생은 어떤 주석을 달았는지 비교해보자.

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int n = get_int("n: "); //정수인 숫자를 입력으로 받아 변수 n에 저장

    if (n % 2 == 0) // 짝수인지 판별
    {
        printf("even\n");
    }
    else // 짝수가 아닌 경우 (홀수인 경우)
    {
        printf("odd\n")
    }
}
```

# [c언어 기초 입력과 출력 2](https://opentutorials.org/module/3921/23575)

## scanf()

scanf() 함수는 입력 상황에서 사용자 키보드를 검사함으로써 키보드로부터 입력된 데이터를 읽어들이는 함수이다. 읽어들인 데이터는 변수에 저장하게 된다.

또한 scanf()도 printf()와 마찬가지로 함수의 이름과 내용(의미, 형식)이 사전에 정의되어 있는 라이브러리 함수이므로 함수가 선언되어 저장된 헤더 파일이 필요하다.

```c
#include <stdio.h>
int main (void)
{
    int a =0;
    scanf("%d", &a);
    printf("%d", a);
}
```

실행 결과

```
385
385

```

- 5행에서 385라는 값을 입력하고 Enter 키를 누르면 6행의 printf() 함수에 의해 값 385가 출력된다.
- scanf()에서 사용가능한 **형식 지정자**는 printf()와 같으며, 입력 받을 값의 **자료형**에 해당하는 형식 지정자를 큰 따옴표("") 안에 포함시키면 된다. 단, **출력은 하지 않으므로** printf() 처럼 출력 데이터를 첨가하거나, 특수 문자를 사용할 수 없다.
- scanf()를 사용할 때 가장 주의할 점은 값이 입력될 변수의 이름 앞에 **참조 연산자'&'**를 붙여야 한다는 것이다. '&' 연산자는 **변수의 메모리 주소를 알려주는 표현**으로, 만일 '&' 없이 변수 이름만 작성하면 오류가 발생한다.

## scanf() 함수의 활용

scanf() 함수를 이용하여 실수, 문자, 그리고 문자열 등 다양한 데이터를 직접 입력받을 수 있다.

```c
#include <stdio.h>

int main (void)
{
    float a;
    char b;
    char c[10];
    scanf("%f %c %s", &a, &b, c);
    printf("%f %c %s", a, b, c);
}
```

실행결과

위 프로그램을 실행하고 원하는 값을 입력할 때 큰 따옴표("") 안에 있는 형식과 동일하게 입력해야 한다.

```
3.14 A 365
3.14 A 365

```

- 4~6행에서 한 개의 실수를 저장하기 위한 변수 a, 한 개의 문자를 저장하기 위한 b, 여러 개의 문자(문자열)를 한 번에 저장하기 위한 배열 변수 c[]를 선언했다.
- 7행에서 scanf() 함수를 통해 각 변수에 저장할 값을 입력한다. 이때 **변수의 성격에 따라 서로 다른 형식 지정자**를 사용한다는 점에 주의하자.
- 8행에서 printf()함수를 통해 결과값을 출력한다.

</details>

<details>
  <summary>5) 사용자 정의 함수, 중첩 루프</summary>

</details>

<details>
  <summary>6) 하드웨어의 한계</summary>

</details>
