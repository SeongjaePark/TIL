참고: 모두의 네트워크 - 키즈구치 카츠야 저
위 책을 읽으며 공부한 내용을 정리한 포스트입니다.

<br>

---

## 무선 랜의 구조

### 무선 랜이란?

> **무선 랜**:
> 랜 케이블을 사용하지 않고 전파나 자외선을 이용하여 컴퓨터 통신을 가능하게 하는 네트워크 방식.

무선랜의 장점: 케이블이 지저분하게 엉키거나 걸리적거리지 않아 편하고, 랜 케이블이 닿지 않는 옆방에서도 통신할 수 있음  
무선랜의 단점: 유선보다 속도가 불안정하고 전파가 약하면 연결이 잘 안 된다. 또한 유선 랜에 비해 통신 내용이 해킹될 위험이 높기 때문에 보안에 더 신경써야 한다.

무선 랜은 **무선 액세스 포인트**(Wireless Access Point, WAP)와 **무선 클라이언트**(컴퓨터나 스마트폰 등)로 구성된다.

> **무선 액세스 포인트**:
> 무선 인터넷 사용자가 인터넷 서비스를 이용할 수 있도록 무선 인터넷 접속을 도와주는 중계 장치.

컴퓨터가 무선 액세스 포인트와 통신하려면 **무선 랜 칩**(chip)과 **무선 랜 어댑터**(adaptor)가 필요하다. 최근에 나온 컴퓨터는 대부분 무선 랜 칩을 내장하고 있어서 문제없이 통신할 수 있다.

무선 랜 어댑터에는 USB 포트에 꽂아 사용하는 **USB 메모리 방식** 어댑터와 **컴퓨터 카드 방식** 어댑터가 있다.

보통 집에서 사용하는 무선 공유기에도 무선 액세스 포인트 기능이 포함되어 있어 집에서 컴퓨터 여러 대와 스마트폰을 와이파이(Wi-Fi)로 연결할 수 있다.

기업은 층 전체에 전파가 전달되어야 하므로 무선 액세스 포인트를 여러 대 설치해야 한다.

<br>

### 인프라스트럭쳐 방식과 애드혹 방식이란?

무선 랜을 연결하는 방식에는 크게 두 가지가 있다.  
**인프라스트럭쳐(infrastructure)** 방식과 **애드혹(Ad Hoc)** 방식이다.

인프라스트럭쳐 방식은 무선 액세스 포인트를 통해 통신하는 방식이다.  
무선 공유기(무선 액세스 포인트)를 중심으로 기기들이 접속한다.

반면에 애드혹 방식은 무선 클라이언트끼리 직접 통신하는 방식이다.

주로 인프라스트럭쳐 방식을 사용한다.

<br>

### 무선 랜 규격

무선 랜은 IEEE802.11 규격을 준수하는 기기로 구성되어 있다.

**IEEE802.11**은 미국 기술 표준화 단체인 IEEE에서 승인한 무선 랜의 표준화 기술이다.

#### 무선 랜 규격

| 무선 랜 규격 | 통신 속도(최대) | 주파수 대역 |                              특징                               |
| :----------: | :-------------: | :---------: | :-------------------------------------------------------------: |
| IEEE802.11ad |     6.7Gbps     |    60GHZ    |                        초고속 통신이다.                         |
| IEEE802.11ac |     6.9Gbps     |    5GHZ     | 장애물이 많아도 고속 통신을 할 수 있고 전파 간섭을 적게 받는다. |
| IEEE802.11n  |     300Mbps     | 2.4GHZ 대역 |           장애물에 강하지만 전파 간섭을 쉽게 받는다.            |
|              |                 |  5GHZ 대역  |           장애물에 약하지만 전파 간섭을 적게 받는다.            |
| IEEE802.11a  |     54Mbps      |  5GHZ 대역  |           장애물에 약하지만 전파 간섭을 적게 받는다.            |
| IEEE802.11g  |     54Mbps      | 2.4GHZ 대역 |           장애물에 강하지만 전파 간섭을 쉽게 받는다.            |
| IEEE802.11b  |     11Mbps      | 2.4GHZ 대역 |           장애물에 강하지만 전파 간섭을 쉽게 받는다.            |

> **IEEE802.11n**:
> 무선 랜이나 와이파이(Wi-Fi)라고 부르는 랜을 위한 컴퓨터 무선 네트워크에 사용되는 표준 기술.

11b, 11g, 11a는 예전 규격이고 2018 6월 시점에서는 **11n** 또는 **11ac**를 주로 사용한다.  
무선 공유기를 살 때 안내서나 상자에 '통신 규: IEEE802.11ac/n/g/b/a'라고 쓰여 있다면 다섯 개 규격을 모두 지원한다는 뜻이다.

다만 무선 클라이언트(컴퓨터 등)도 이러한 규격을 지원해야 하는데 그렇지 않은 경우도 있으니 주의해야 한다.  
무선 공유기가 IEEE802.11ac를 지원하더라도 무선 클라이언트가 그 규격을 지원하지 않으면 사용할 수 없다.

무선 랜을 구성하는 장비 중에서 무선 액세스 포인트를 **무선 공유기** 또는 **무선 AP**라고 부르기도 한다.

<br>

---

## SSID의 구조

### SSID란?

> **SSID(서비스 세트 식별자)**:
> 무선 랜을 통해 전송되는 패킷의 각 헤더에 붙는 고유 식별자로 하나의 무선 랜을 다른 무선 랜과 구분하는 역할을 한다.

무선 랜은 **무선 액세스 포인트**와 **무선 클라이언트**가 서로 통신한다.

무선 액세스 포인트와 무선 클라이언트를 연결하려면 혼선을 피하기 위해 **SSID**(Service Set IDentifier)라는 **액세스 포인트의 고유 이름**을 사용한다. 그리고 **네트워크 이름, 인증, 암호화, 암호화 키**를 설정해야 한다.

이런 설정을 해 둬야 무선 클라이언트가 자동으로 무선 액세스 포인트를 찾아서 통신할 수 있다.

#### 무선 액세스 포인트와 무선 클라이언트의 연결

<img src="https://images.velog.io/images/gndan4/post/4cf61b11-8e76-4384-af6b-890f22c2e189/IMG_0447.jpg" width="70%">

<br>

<br>

무선 액세스 포인트는 **비컨**(beacon)이라고 하는 자기를 알리는 신호를 네트워크에 있는 모든 기기에 주기적으로 전송하는데, 무선 클라이언트는 이 신호를 잡아서 연결하는 것이다.

신호를 받은 무선 클라이언트는 자신의 **SSID**와 같은지 무선 액세스 포인트에 문의한다.

그러면 같은 SSID의 무선 액세스 포인트가 응답을 하고 서로의 존재를 알게 된다.

그 다음으로 설정된 **인증** 방식이 올바른지 확인되면 무선 클라이언트는 무선 액세스 포인트에 **연결을 요청**하고, 무선 액세스 포인트로부터 승인을 받으면 연결하여 통신할 수 있다.

<br>

### 채널이란?

무선 액세스 포인트와 무선 클라이언트 사이의 거리가 멀수록 전파가 약해져서 접속이 잘 ㅇ나 되거나 통신 속도가 느려질 수 있다.

이러한 이유로 무선 액세스 포인트를 여러 대 설치해야 한다. 여기서 **채널**이라는 용어가 나온다.

> **채널**(channel):
> 무선 통신에서 하나의 통화 신호나 기타 정보가 전송되는 분리된 전송로를 뜻한다. 통신 채널이라고도 한다.

무선 랜은 여러 기기를 동시에 연결할 수 있도록 **주파수 대역**을 분할하는데, 그 주파수 대역을 **채널**이라고 부른다.

만약 무선 공유기 A가 컴퓨터 1과 컴퓨터 2와 연결하여 통신할 때, 이 무선 공유기 A와 컴퓨터는 모두 같은 채널을 각각 설정해야 한다. 같은 주파수 대역을 사용한다는 의미다.

여러 무선 공유기가 있을 경우 서로 다른 채널을 설정해야 한다. 다른 채널은 주파수가 서로 다르기 때문에 전파가 겹치더라도 서로 간섭이 일어나지 않아 통신 속도도 떨어지지 않는다.

만약 전파가 겹치는 무선 공유기들이 같은 채널로 설정되어 있으면 주파수가 서로 겹치면서 **전파 간섭**이 생기고 통신 속도가 느려진다. 그래서 같은 채널을 사용하되 전파를 겹치지 않게 하려면 거리를 떨어뜨려 설치해야 한다.

> **전파 간섭**(interference):
> 같은 주파수의 파동이 합성되거나 상쇄될 때 나타나는 현상이다. 무선 랜과 무선 랜 또는 무선 랜과 다른 기기 사이의 전파 간섭 때문에 통신 속도가 떨어질 수 있다.

IEEE802.11b와 IEEE802.11g는 서로 다른 채널인 **1ch**와 **2ch**라도 일부에서 같은 주파수를 사용하기 때문에 간섭이 생길 수 있으므로 주의해야 한다.

IEEE802.11a는 각 채널 간에 서로 다른 주파수 대역을 사용하므로 전파가 겹쳐도 문제없다.

무선 액세스 포인트는 기본적으로 자동으로 설정되니 알아서 최적의 채널을 찾아준다. 연결이 불안정하거나 통신 속도가 느려질 때는 이런 것이 원인일 수 있으므로 채널을 수동으로 변경해 보는 것도 좋은 해결 방법이다. 참고로 무선 공유기의 설정은 웹 브라우저로 확인할 수 있다.
