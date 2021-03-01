패스트캠퍼스 컴퓨터 공학자 따라잡기 온라인 완주반  
운영체제([이준희 님](https://www.fun-coding.org/)) 파트를 수강하며 공부한 내용을 정리한 자료입니다.

---

## 운영체제의 역할

1. 응용 프로그램을 관리한다.
2. 시스템 자원(System Resource)를 관리한다.
3. 사용자와 컴퓨터 간의 커뮤니케이션을 지원

### 운영체제의 역할 1: 시스템 자원(System Resource) 관리자

시스템 자원(System Resource) = 컴퓨터 하드웨어

- CPU(중앙처리장치), Memory
- I/O Devices(입출력 장치)
  - 모니터, 마우스, 키보드, 네트워크
- 저장매체: SSD, HDD(하드 디스크)

컴퓨터 하드웨어는 스스로를 관리할 수 없기에 이를 관리해주는 운영체제가 필요하다.

1. CPU: 각 프로그램이 얼마나 CPU를 사용할 지를 결정할 수 없다.
2. Memory: 각 프로그램이 어느 주소에 저장되어야 하는지, 어느 정도의 메모리 공간을 확보해줘야 하는지 결정할 수 없다.
3. 저장매체(SSD, HDD): 어디에 어떻게 저장할 지 결정할 수 없다.
4. 키보드/마우스: 스스로 표시할 수 없다.

### 운영체제의 역할 2: 사용자와 컴퓨터 간의 커뮤니케이션 지원

운영체제는 사용자와 컴퓨터가 원활한 커뮤니케이션을 할 수 있도록 돕는 중개자 역할을 한다.  
운영체제 없이는 사용자가 컴퓨터에게 명령을 내릴 수가 없다.

### 운영체제의 역할 3: 컴퓨터 하드웨어와 응용 프로그램을 제어

운영체제는 컴퓨터 하드웨어 뿐만 아니라, 응용 프로그램을 제어한다.  
운영체제는 여러 기술을 활용해서 컴퓨터 하드웨어와 응용 프로그램을 제어하여 효율적으로 사용할 수 있도록 해준다.

---

## 운영체제와 응용 프로그램

### 응용 프로그램이란?

- 프로그램 = 소프트웨어
- 소프트웨어 = 응용 프로그램(사람들이 자주 사용하는 엑셀, 파워포인트 등 포함). 운영 체제 또한 소프트웨어의 일종이다.

### 운영체제와 응용 프로그램 간의 관계

응용 프로그램은 누구나 만들 수 있다.
하지만 응용 프로그램을 잘못 작성해서 프로그램이 다운되거나, 모든 파일을 삭제하게될 수도 있고, CPU를 과도하게 많이 사용하게될 수도 있다. 따라서 운영체제는 응용 프로그램을 관리할 필요가 있다.

운영체제가 응용 프로그램을 관리하는 방식

- 응용 프로그램을 실행시킨다.
- 응용 프로그램의 **권한**을 관리해준다. (관리자 권한으로 실행)
- 응용 프로그램을 사용하는 **사용자**도 관리한다. (로그인)

우리가 사용하는 응용 프로그램은 모두 운영체제 위에서 실행이 된다.

운영체제(Operating System)의 목표: 사용자가 사용하는 **응용 프로그램이 효율적으로, 적절하게 동작하도록 지원**하는 것

운영체제는 응용 프로그램이 요청하는 **시스템 리소스를 효율적으로 분배**하고 지원하는 소프트웨어라고 할 수 있다.

참고로 운영체제는 저장매체(SSD/HDD)에 저장(설치)되며, 컴퓨터를 키면 운영체제가 Memory에 올라가게 된다.