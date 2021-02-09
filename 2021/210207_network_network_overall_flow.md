참고: 모두의 네트워크 - 키즈구치 카츠야 저
위 책을 읽으며 공부한 내용을 정리한 포스트입니다.

---

## 랜 카드에서의 데이터 전달과 처리

### 네트워크의 구성

#### OSI 모델

- 응용 계층(세션 계층과 표현 계층을 포함): 어플리케이션 등에서 사용하는 데이터를 송수신하는 데 필요
- 전송 계층: 목적지에 데이터를 정확하게 전달하는 데 필요
- 네트워크 계층: 다른 네트워크에 있는 목적지에 데이터를 전달하는 데 필요
- 데이터 링크 계층: 랜에서 데이터를 송수신하는 데 필요
- 물리 계층: 데이터를 전기 신호로 변환하는 데 필요

#### 네트워크의 구성

아래 그림과 같이 컴퓨터, 스위치, 라우터, 웹 서버로 구성된 네트워크가 있다. 이 구성은 몇 개의 네트워크로 나누어져 있을까?

<img src="https://images.velog.io/images/gndan4/post/067c5d14-a66f-46c1-9491-9cf6122b7539/IMG_0433.jpg" width="70%">

<br>
<br>

정답은 192.168.1.0/24, 172.16.0.0/16, 192.168.10.0/24로 총 3개다.

위의 그림을 OSI 모델로 나타내면 아래와 같이 구성된다.

<img src="https://images.velog.io/images/gndan4/post/a5f3a7fb-b98d-49d6-acfe-76c29c5f911b/IMG_0434.jpg" width="70%">

<br>

<br>

### 컴퓨터의 데이터가 전기 신호로 변환되는 과정

OSI 모델의 전체적인 관점으로 데이터가 전달되고 처리되는 과정을 알아보자.

구체적으로 컴퓨터의 웹 브라우저에 URL을 입력할 때부터 웹 서버에 도착할 때까지 이루어지는 OSI 모델의 **캡슐화**와 **역캡슐화**를 살펴보자.

<br>

#### 클라이언트의 컴퓨터에서 데이터의 흐름 (캡슐화)

<img src="https://images.velog.io/images/gndan4/post/9dd55fe0-3be7-4dd6-a218-8368468d27d3/IMG_0435.jpg" width="80%">

<br>

#### 응용 계층

먼저 웹 사이트에 접속해야 하므로 **응용 계층**에서 시작한다. 그림과 같이 웹 브라우저에서 URL을 입력하고 `Enter` 키를 누르면 캡슐화가 시작된다. 단, **3-way 핸드셰이크**는 이미 완료되어 **연결이 확립**되어 있다고 가정한다.

컴퓨터에서 웹 브라우저를 이용하여 웹 서버의 웹 사이트에 접속하기 위한 요청을 보낼 때 사용하는 것이 HTTP 프로토콜이었다. 응용 계층에서는 웹 서버에 있는 html 데이터를 얻어야 하므로 그림처럼 `GET/index.html HTTP/1.1 ~`와 같은 **HTTP 메시지**를 보낸다.

#### 전송 계층

계속해서 이 데이터가 전송 계층에 전달된다. 전송 계층에서는 **출발지 포트 번호**와 **목적지 포트 번호**가 포함된 **TCP 헤더**를 데이터에 붙인다.

출발지 포트 번호(웹 브라우저)는 **잘 알려진 포트**가 아닌 포트(1025번 이상인 포트) 중에서 무작위로 선택된다. 여기서는 3500번 포트를 사용했다고 가정한다. 목적지 포트 번호는 HTTP이므로 80번이 된다.

이와 같이 TCP 헤더가 붙은 데이터를 **세그먼트**라고 한다.

#### 네트워크 계층

그 다음에는 데이터가 네트워크 계층에 전달된다. 네트워크 계층에서는 전달받은 세그먼트에 **IP 헤더**를 붙인다. IP 헤더에는 **출발지 IP 주소**와 **목적지 IP 주소**가 포함되어 있으며, IP 헤더가 붙은 데이터를 **IP 패킷**이라 한다.

#### 데이터 링크 계층

그 다음에는 데이터 링크 계층으로 전달된다. 데이터 링크 계층에서는 **도착지 MAC 주소**와 **출발지 MAC 주소**가 포함되어 있는 **이더넷 헤더**가 붙는다. 이더넷 헤더가 붙은 데이터를 **이더넷 프레임**이라고 한다.

#### 물리 계층

그 다음으로 물리 계층에서 데이터가 **전기 신호**로 변환되어 네트워크로 전송된다. 물리 계층에서 데이터를 전기 신호로 변환할 때 **랜 카드**라는 장비가 사용된다.

<br>

---

## 스위치와 라우터에서의 데이터 전달과 처리

### 스위치에서의 데이터 전달과 처리

#### 물리 계층 -> 데이터 링크 계층 -> 물리 계층으로 전달 (스위치 A)

아래 그림과 같이, 스위치 A는 데이터를 **전기 신호**로 변환하여 라우터 A로 전송한다.

<img src="https://images.velog.io/images/gndan4/post/a86bbd34-8862-4912-9637-3382ef2d6928/IMG_0436.jpg" width="80%">

<br>

<br>

### 라우터에서의 데이터 전달과 처리

계속해서 데이터는 스위치 A에서 라우터 A로 전기 신호로 전달된다. 라우터 A에서의 캡슐화와 역캡슐화에 대해 살펴보자.

#### 물리 계층 -> 데이터 링크 계층 -> 네트워크 계층으로 전달 (라우터 A - 역캡슐화)

<img src="https://images.velog.io/images/gndan4/post/eb62ccd5-c493-40ea-a679-1e680e7cbb19/IMG_0437.jpg" width="80%">

<br>

위 그림과 같이 스위치 A에서 데이터가 **전기 신호**로 변환되어 케이블을 통해 흘러가 라우터 A에 도착하면 라우터 A는 **데이터 링크 계층**에서 이더넷 프레임의 **목적지 MAC 주소**와 자신의 MAC 주소를 비교한다. 이때 주소가 같으면 이더넷 헤더와 트레일러를 분리하는 **역캡슐화를** 수행한다. 다음으로 **네트워크 계층**에 전달하고 자신의 **라우팅 테이블**과 **목적지 IP 주소**를 비교한다.

<br>

#### 네트워크 계층 -> 데이터 링크 계층 -> 물리 계층 (라우터 A - 캡슐화)

<img src="https://images.velog.io/images/gndan4/post/f37f4853-abbf-4912-8bff-9a17c5ace6a6/IMG_0438.jpg" width="80%">

라우터 A의 라우팅 테이블에서 목적지 IP 주소의 경로를 알 수 있으므로 **라우팅**을 할 수 있다. 그래서 위 그림과 같이 현재 출발지 IP 주소 192.168.1.10을 라우터의 외부 IP 주소(실제로는 WAN 측)인 172.16.0.1로 변경한다.

그런 다음 **데이터 링크 계층**으로 전달하여 라우터 B로 보내지도록 이더넷 헤더와 트레일러를 붙인 후에 **물리 계층**에서 데이터를 전기 신호로 변환하여 네트워크로 전달한다.

<br>

#### 물리 계층 -> 데이터 링크 계층 -> 네트워크 계층으로 전달(라우터 B - 역캡슐화)

<img src="https://images.velog.io/images/gndan4/post/a1678dd9-6784-4eff-befa-db2a4debbc04/IMG_0439.jpg" width="80%">

데이터가 전기 신호로 변환되어 케이블을 통해 라우터 A에서 라우터 B에 도착하면 라우터 B는 이더넷 프레임의 목적지 MAC 주소와 자신의 MAC 주소를 비교한다. 주소가 같으면 이더넷 헤더와 트레일러를 분리하는 **역캡슐화**를 수행한다. 그 다음 **네트워크 계층**으로 전달되면 자신의 라우팅 테이블과 목적지 IP 주소를 비교한다. 라우터 A와 마찬가지로 라우터 B도 목적지의 네트워크를 알아야 하기 때문이다.

<br>

#### 네트워크 계층 -> 데이터 링크 계층 -> 물리 계층으로 전달(라우터 B - 캡슐화)

<img src="https://images.velog.io/images/gndan4/post/57c0ebcb-b7ec-4db4-8b4e-6ac6c02b6513/IMG_0442.jpg" width="80%">

라우터 B의 라우팅 테이블을 확인해 보면 목적지 IP 주소의 경로를 알 수 있으므로 라우팅을 할 수 있다. 그리고 위의 그림과 같이 현재의 출발지 IP 주소 172.16.0.1을 라우터 B의 내부 IP주소(실제는 LAN 측)인 192.168.10.1로 변경한다. 그런 다음 **데이터 링크 계층**에 전달하여 스위치에 전달되도록 이더넷 헤더와 트레일러(FCS)를 붙인 후 물리 계층에서 데이터를 전기 신호로 변환하여 네트워크로 전달한다.

<br>

#### 데이터 링크 계층 -> 물리 계층 (스위치 B)

<img src="https://images.velog.io/images/gndan4/post/0963699f-4b8f-452e-833f-2203c929e764/IMG_0444.jpg" width="80%">

이번에는 전기 신호 형태의 데이터가 라우터 B에서 스위치 B로 전달된다. 스위치 B는 위의 그림과 같이 전기 신호를 데이터 링크 계층에서 처리하고 웹 서버에 데이터를 전기 신호로 전달한다.

<br>

---

## 웹 서버에서의 데이터 전달과 처리

### 웹 서버에서의 데이터 전달 및 처리

웹 서버에서 이루어지는 OSI 모델의 역캡슐화를 살펴보자.

#### 웹 서버에서 데이터의 흐름(역캡슐화)

<img src="https://images.velog.io/images/gndan4/post/777a5938-e4e8-48d7-a5ee-a4c949e4a2e9/IMG_0446.jpg" width="80%">

#### 물리 계층 -> 데이터 링크 계층

위 그림과 같이 데이터가 전기 신호로 웹 서버에 도착하면 웹 서버는 **데이터 링크 계층**에서 이더넷 프레임의 목적지 MAC 주소와 자신의 MAC 주소를 비교한다. 주소가 같으면 이더넷 헤더와 트레일러를 분리하고 네트워크 계층에 전달한다.

#### 네트워크 계층

다음으로 **네트워크 계층**에서는 목적지 IP 주소와 웹 서버의 IP 주소가 같은지 확인한다. 주소가 같으면 IP 헤더를 분리하고 전송 계층에 전달한다.

#### 전송 계층 -> 응용 계층

다음으로 **전송 계층**에서는 목적지 포트 번호를 확인하여 어떤 어플리케이션으로 전달해야 되는지 판단하고 TCP 헤더를 분리하여 응용 계층에 전달한다.

드디어 html 데이터를 보내달라는 클라이언트의 요청이 웹 서버의 **응용 계층**에 도착한 것이다.

사용자의 컴퓨터에서 웹 서버까지 데이터가 도달하려면 이처럼 많은 네트워크 단계를 거쳐야 한다.  
지금까지 이 포스트에서 전체적으로 살펴 본 내용은 요청 한 번에 대한 것이다. 이 다음에는 컴퓨터로 응답을 보내야 한다. 우리가 웹 사이트를 볼 때 컴퓨터와 웹 서버 사이에는 몇 번이고 요청과 응답의 교환이 이루어지고 있는 것이다.

<br>

---

## 정적 라우팅과 동적 라우팅

라우팅은 패킷을 목적지 컴퓨터까지 보낼 때 최적의 경로를 선택하여 전송하는 것을 뜻한다. 라우팅은 크게 정적 라우팅과 동적 라우팅이라는 두 가지 방법으로 나뉜다.

### 정적 라우팅

정적 라우팅은 관리자가 테이블에 경로를 수동으로 추가하는 방법이다. 목적지까지의 경로를 고정하거나 목적지까지의 경로가 하나로 한정되는 경우에 사용한다.

정적 라우팅에서는 네트워크에 존재하는 모든 목적지 네트워크의 정보를 라우터에 알려줘야 한다. 그것을 관리자가 수동으로 설정해야 하므로 소규모 네트워크에서 사용된다.

라우팅 정보가 교환되지 않아 대역폭에 대한 부담이 적다는 장점이 있다. 라우팅 정보가 네트워크로 전달되지 않으므로 보안을 유지하는 데도 좋다.

단점은, 동적으로 반영되지 않으므로 어떤 경로에 장애가 발생해도 다른 경로로 우회할 수 없다는 것이다. 이럴 때는 관리자가 설정을 하나하나 변경해야 해서 번거롭다.

### 동적 라우팅

동적 라우팅은 네트워크 변경을 자동으로 감지하여 라우팅 테이블을 업데이트하거나 네트워크 장애가 발생했을 때 라우터끼리 정보를 교환하여 최적의 경로로 전환하는 기능을 한다. 관리자는 정적 라우팅처럼 라우팅 테이블에 경로를 수동으로 추가할 필요가 없다.

대규모 네트워크에서는 라우터에 많은 경로가 등록되기 때문에 정적 라우팅을 지원하지 않고 동적 라우팅을 사용하여 경로를 자동으로 업데이트 한다.