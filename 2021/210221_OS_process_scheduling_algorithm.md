패스트캠퍼스 컴퓨터 공학자 따라잡기 온라인 완주반
운영체제([이준희 님](https://www.fun-coding.org/)) 파트를 수강하며 공부한 내용을 정리한 자료입니다.

---

## 프로세스란?

프로세스: 메모리에 올려져서 실행 중인 프로그램  
코드 이미지(바이너리): 실행 파일

> 프로세스라는 용어는 작업, task, job이라는 용어와 혼용

응용 프로그램 != 프로세스

- 응용 프로그램은 여러 개의 프로세스로 이루어질 수 있음
- 하나의 응용 프로그램은 여러 개의 프로세스(프로그램)가 상호작용을 하면서 실행될 수도 있음

간단한 프로그램을 만든다면 -> 하나의 프로세스  
여러 프로그램을 만들어서 서로 통신하면서 프로그램을 작성할 수도 있음 (IPC 기법)

## 스케쥴링 알고리즘

스케쥴러는 프로세스를 관리하는 주체다.

시스템의 목표에 따라서 스케쥴링 알고리즘이 달라진다.

- 시분할 시스템: 프로세스 응답 시간을 가능한 한 짧게
- 멀티 프로그래밍: 단위 시간 당 CPU 활용도를 최대로 높혀서, 프로세스를 빨리 실행

### FIFO 스케쥴러

> 프로세스가 저장매체를 읽는다든지 프린팅을 한다든지 하는 작업 없이, CPU를 처음부터 끝까지 쭉 사용한다고 가정하고 이 알고리즘을 살펴보자.

> **FIFO 스케쥴러** (First In First Out):  
> 프로세스 실행 요청이 들어와 준비 큐에 등록된 순서대로 프로세서(CPU)에 넘겨주어 순차적으로 실행을 완료한다.

- 가장 간단한 스케쥴러(배치 처리 시스템과 유사)
- FCFS(First Come First Served)라고도 부름
- 큐 자료구조를 통해 구현된다.

#### 그림1. FIFO 스케쥴러

<img src="https://images.velog.io/images/gndan4/post/4e8a686f-b309-40ef-85cd-df7148fd0a02/image.png" alt="FIFO 스케쥴러" width="70%">

### 최단 작업 우선(SJF) 스케쥴러

> **SJF 스케쥴러** (Shortest Job First):
> 가장 프로세스 실행시간이 짧은 프로세스부터 먼저 실행시키는 알고리즘

#### 그림1. FIFO 스케쥴러와 SJF 스케쥴러 비교

<img src="https://images.velog.io/images/gndan4/post/2c2f306a-08f0-4957-b72a-4f27d327ccd3/image.png" alt="FIFO 스케쥴러와 SJF 스케쥴러 비교" width="70%">

#### RTOS와 GPOS

- Real Time OS(RTOS): 응용 프로그램 실시간 성능 보장을 목표로 하는 OS
  - 정확하게 프로그램 시작, 완료 시간을 보장
  - Hardware RTOS, Software RTOS
- General Purpose OS(GPOS): 프로세스 실행시간에 민감하지 않고, 일반적인 목적으로 사용되는 OS
- Windows, Linux 등

### 우선순위 기반 스케쥴러

> **Priority-Based 스케쥴러**
> : 프로세스에 우선순위를 매겨 놓고, 우선 순위가 높은 순서대로 프로세스를 실행하는 방식

- 정적 우선순위: 프로세스마다 우선순위를 미리 지정
  - 하지만 모든 프로세스에 직접 우선 순위를 준다는 것이 현실적으로 번잡스럽다.
- 동적 우선순위: 상황에 따라 스케쥴러가 우선순위를 동적으로 변경
  - 목적에 따라 스케쥴러가 우선순위를 할당하는 알고리즘이 다를 것이다.

#### 그림2. FIFO, SJF, 우선순위 기반 스케쥴러 비교

<img src="https://images.velog.io/images/gndan4/post/8e4fabaa-21ee-47ca-b8b1-91fdc2b0c69f/image.png" alt="FIFO, SJF, 우선순위 기반 스케쥴러 비교" width="70%">

### Round-Robin 스케쥴러

#### 그림3. Round-Robin 스케쥴러

<img src="https://images.velog.io/images/gndan4/post/280f1eb1-3ed6-4ffb-9c9b-0edd89039149/image.png" alt="Robin-Round 스케쥴러" width="70%">

- 기본적으로는 FIFO 스케쥴러와 동작 방식이 비슷하다.
- 시분할 시스템을 가정하고 있다.
- 특정 시간이 지날 때마다 아직 프로세스가 완료되지 않았더라도 중단하고 다음 프로세스를 실행한다.
  - 중단된 프로세스는 다시 준비 큐의 맨 뒤에 추가된다.

#### 그림4. Round-Robin 스케쥴러 작동 예시

<img src="https://images.velog.io/images/gndan4/post/c6bb2840-1cfb-43bc-bdcd-9fbccbd16d58/image.png" alt="Round-Robin 스케쥴러 작동 예시" width="70%">

## 정리

- FIFO (FCFS) - 배치 처리 시스템과 유사 (요청된 순서대로 실행)
- 최단 작업 우선(SJF) - 실행 시간이 짧은 프로세스를 먼저 실행
- 우선순위 기반 스케쥴링 알고리즘 - 할당된 우선순위가 높은 프로세스를 먼저 실행
  - 정적 우선순위, 동적 우선순위
- Round-Robin - 정해진 시간마다 실행 중인 프로세스를 중단하고 준비 큐에 다시 추가. 다음 프로세스를 이어서 실행
  - 시분할 시스템 기반
