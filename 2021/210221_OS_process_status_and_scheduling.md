패스트캠퍼스 컴퓨터 공학자 따라잡기 온라인 완주반
운영체제([이준희 님](https://www.fun-coding.org/)) 파트를 수강하며 공부한 내용을 정리한 자료입니다.

---

## 프로세스 상태와 스케쥴링

### 프로세스 상태와 멀티 프로그래밍

멀티 프로그래밍: 단위 시간 당 CPU 활용도를 극대화 하는 스케쥴링 알고리즘

wait: 간단히 저장매체로부터 파일 읽기를 기다리는 시간으로 가정

아래 그림과 같이 프로세스 상태를 고려한 멀티 프로그래밍을 활용하면 CPU 활용도를 극대화하고 프로세스 실행 시간을 줄일 수 있다.

#### 그림1. 프로세스 상태를 고려한 멀티 프로그래밍 예시

<img src="https://images.velog.io/images/gndan4/post/a81d5e2a-34da-4d57-9286-bfb88e220bc8/image.png" alt="프로세스 상태를 고려한 멀티 프로그래밍 예시" width="70%">

### 프로세스 상태

프로세스 스케쥴러는 스케쥴링을 할 때 프로세스의 상태 정보를 필요로 한다.
어느 시점에 어떤 프로세스를 CPU에 넣어줄 지를 결정하는 데에 있어서 프로세스 상태가 주요한 요소가 된다.

#### 그림2. 프로세스 상태

<img src="https://images.velog.io/images/gndan4/post/62b70dea-b3ba-4feb-86ee-128c40fd6acc/image.png" alt="프로세스 상태" width="70%">

기본적인 프로세스 스케쥴링 알고리즘에서는 프로세스 상태 정보를 위와 같이 5개로 정의해 놓았다.

이 중 스케쥴러에서 가장 필요로 하는 주요 상태 정보는 다음의 3가지 상태다.

1. ready state: CPU에서 실행 가능 상태(실행 대기 상태)
2. blocked state: 특정 이벤트 발생 대기 상태(예: 파일 읽기가 완료되었다)
3. running state: 현재 CPU에서 실행 중인 상태

<br>

- 프로세스가 생성 중인 상태 (ready state로 아직 가지 못한 상태)
- 프로세스가 종료 중인 상태
  - 프로세스가 완료된 후 쥐고 있는 시스템 리소스를 아직 다 풀어주지 못한 상태!

### 프로세스 상태 간 관계

#### 그림3. 프로세스 상태 간 관계

<img src="https://images.velog.io/images/gndan4/post/cf297264-9c98-4a5d-85c4-53631344272e/process_state.png">

그림 출처: https://medium.com/@sohailk1999/five-state-process-model-6e83d7428c8c

- running -> block

  - 프로세스가 running 상태에 있다가 파일 읽기를 요청한 경우 block(waiting) 상태에 들어가게 된다.

- block -> running

  - block 상태에서 특정한 이벤트를 받으면 스케쥴러에게 running 상태로 바꿔도 좋다라고 알려주기 위해서 우선은 ready 상태로 상태가 변경된다.

- running -> ready

  - 프로세스가 타이머 등의 이유로 현재 실행중인 프로세스를 중단시키게 되면 그 프로세스는 ready 상태로 들어가게 된다.

- ready -> running
  - 현재 실행 중인 프로세스가 완료되거나 중단된 경우 ready 상태에 있는 프로세스가 running 상태로 들어가서 실행된다.

#### 그림4. 프로세스 상태와 큐를 기반으로 한 기본적인 알고리즘 예시

<img src="https://images.velog.io/images/gndan4/post/31b2c0a5-cbba-4a19-ad5e-1390ba88f54a/image.png" alt="프로세스 상태와 큐를 기반으로 한 기본적인 알고리즘 예시" width="70%">
