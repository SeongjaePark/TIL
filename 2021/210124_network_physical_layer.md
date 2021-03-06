참고: 모두의 네트워크 - 키즈구치 카츠야 저
위 책을 읽으며 공부한 내용을 정리한 포스트입니다.

아날로그 신호 & 디지털 신호: [zum 학습백과](http://study.zum.com/book/13707)

다이렉트 케이블 & 크로스 케이블 그림: [Guru99](https://www.guru99.com/difference-between-straight-through-crossover-cables.html)

---

<br><br>

# 물리 계층의 역할과 랜 카드의 구조

## 전기 신호란?

<br>

데이터는 전기 신호로 변환되어 네트워크를 통해 전송된다.

<br>

> **전기 신호**(electric signal):
>
> 전기 신호는 전압이 일정 패턴으로 변하여 생기는 일련의 흐름으로 전압의 변화가 모여서 만들어진 신호다.
> 이런 전기 신호들을 주고받음으로써 네트워크에서 사진이나 문서 등을 주고받을 수 있다.

<br>

0과 1만으로 이루어진 비트열을 전기 신호로 변환하려면 OSI 모델의 맨 아래 계층은 **물리 계층**의 기술이 필요하다.

<br>

> **물리 계층**(physical layer):
>
> OSI 모델의 최하위 계층으로, 데이터를 전송하기 위해 시스템 간의 물리적인 연결을 하고 전기 신호의 변환 및 제어하는 역할을 담당한다.
>
> 또한 전송 매체를 통해 데이터를 통신할 수 있는 전기적인 신호로 바꾸어 전송하는 일을 한다.

<br>

전기 신호의 종류에는 아날로그 신호와 디지털 신호가 있다.

<br>

> **아날로그 신호**:
> 물결 모양의 신호로, 빛, 소리 등과 같이 연속적으로 변하는 신호.
> 전화 회선이나 라디오 방송에서 사용된다.

<br>

![](https://images.velog.io/images/gndan4/post/19715725-079f-4c6e-b84a-fb8c564efd66/image.png)

<br>

> **디지털 신호**:
>
> 막대 모양의 신호로, 특정한 값을 단위로 불연속적으로 변하는 신호.
> 컴퓨터나 휴대 전화와 같은 현대 문명에서 사용되는 대부분의 신호.
>
> 아날로그 신호와 대비되는 신호 형태로 아날로그 신호를 전류의 유무나 극성, 위상의 동일이나 반대 등 물리적 현상을 이용하여 컴퓨터가 인식하는 0 또는 1의 2진수에 대응시켜 나타내는 신호를 말한다.

<br>

![](https://images.velog.io/images/gndan4/post/65742e5d-2951-46aa-8bb2-75a26486fa59/image.png)

<br>

데이터 송신 측 컴퓨터가 전송하는 0과 1의 비트열 데이터는 전기 신호로 변환되어 네트워크를 통해 수신 측 컴퓨터에 도착한다.
수신 측 컴퓨터에서는 전기 신호를 0과 1의 비트열 데이터로 복원한다.

<br>

## 랜 카드란?

<br>

> **랜 카드**(LAN card): 컴퓨터의 네트워크 연결 및 데이터 전송을 담당하며, '네트워크 카드' 또는 '네트워크 인터페이스 컨트롤러(NIC)'라고도 불린다.

<br>

컴퓨터는 네트워크를 통해 데이터를 송수신할 수 있도록 **랜 카드**가 메인 보드에 포함되어 있는 내장형 랜 카드나 별도의 랜 카드를 가지고 있다.

0과 1의 정보가 컴퓨터 내부에 있는 랜 카드로 전송되고 랜 카드는 0과 1을 전기 신호로 변환한다.

이처럼 물리 계층은 컴퓨터와 네트워크 장비를 연결하고, 컴퓨터와 네트워크 장비 간에 전송되는 데이터를 전기 신호로 변환하는 계층이다.

<br><br>

# 케이블의 종류와 구조

<br>

## 트위스트 페어 케이블이란?

<br>

네트워크의 **전송 매체**는 **데이터가 흐르는 물리적인 선로**로 크게 **유선**과 **무선**으로 나뉜다.  
유선에는 트위스트 페어 케이블, 광케이블 등이 있고,  
무선에는 라디오파, 마이크로파, 적외선 등이 있다.

<br>

이 중 **트위스트 페어 케이블**(twisted pair cable)이 가장 많이 사용되며, 그 종류에는 UTP 케이블과 STP 케이블이 있다.

<br>

> **UTP** 케이블:
> Unshielded Twist Pair의 약자로, '비차폐 연선'이라고도 한다.

<br>

UTP 케이블은 구리 선 여덟 개를 두 개씩 꼬아 만든 네 쌍의 전선으로, **실드**(shield)로 보호되어 있지 않은 케이블이다.

실드는 **금속 호일이나 금속의 매듭과 같은 것**으로, 외부에서 발생하는 노이즈(noise)를 막는 역할을 한다.

UTP 케이블은 실드로 보호되어 있지 않아서 **노이즈**의 영향을 받기 쉽지만 저렴하기 때문에 일반적으로 많이 사용되는 케이블이다.

<br>

> **노이즈**(noise, 잡음):
> 케이블에 전기 신호가 흐를 때 발생하며,  
> 데이터의 왜곡이나 분해로 인해 전송 매체에서 생기는 전자 신호다.

<br>

![노이즈로 인한 아날로그 신호와 디지털 신호의 변화](https://images.velog.io/images/gndan4/post/b5754c18-4469-46a1-b414-a97507d83fab/image.png)

<br>

노이즈의 영향을 적게 받도록 구리 선 두 개를 비틀어 꼬아서 케이블을 만드는 것이다.

<br>

> **STP** 케이블:
> Shielded Twist Pair의 약자로, '차폐 연선'이라고도 한다.

<br>

STP와는 달리 UTP는 노이즈의 영향을 쉽게 받지만 저렴하기 때문에 일반적으로는 UTP 케이블을 사용한다.

<br>

UTP 케이블은 데이터 전송 품질에 따라 다음과 같이 분류된다.

<br>

### UTP 케이블의 분류

<br>

| 분류  |    규격     |   속도   |
| :---: | :---------: | :------: |
| Cat3  |  10BASE-T   |  10Mbps  |
| Cat5  | 100BASE-TX  | 100Mbps  |
| Cat5e | 1000BASE-T  | 1000Mbps |
| Cat6  | 1000BASE-TX | 1000Mbps |
| Cat6a |  10GBASE-T  | 10GMbps  |
| Cat7  |  10GBASE-T  | 10GMbps  |

<br>

트위스트 페어 케이블(UTP, STP)은 일반적으로 **랜 케이블**(LAN cable, 랜 선)이라고 한다. 보통은 랜 케이블이라는 용어를 더 많이 사용한다.

랜 케이블의 양쪽 끝에는 **RJ-45**라고 부르는 커넥터가 붙어 있다.  
이 커넥터를 컴퓨터의 랜 포트나 네트워크 기기에 연결하는 것이다.

<br>

## 다이렉트 케이블과 크로스 케이블이란?

<br>

랜 케이블의 종류에는 다이렉트 케이블과 크로스 케이블이 있다.

**다이렉트 케이블**은 아래와 같이 구리 선 8개를 **같은 순서**로 커넥터에 연결한 케이블이다.

<br>

![Direct Cable](https://images.velog.io/images/gndan4/post/2b16011f-6c2d-4c36-8034-b23f5831d467/image.png)

<br>

**크로스 케이블**은 아래와 같이 구리 선 8개 중 한쪽 커넥터의 **1번**과 **2번**에 연결되는 구리 선을 다른 쪽 커넥터의 **3번**과 **6번**에 연결한 케이블이다.

<br>

![Cross Cable](https://images.velog.io/images/gndan4/post/bcf3f0d3-d632-4750-ba4a-2cda77760577/image.png)

<br>

다이렉트 케이블이나 크로스 케이블 모두 실제로는 1번, 2번, 3번 ,6번 구리 선을 사용하고 있다.  
나머지 선 4개는 사용하지 않는다.

다이렉트 케이블은 **컴퓨터와 스위치**를 연결할 때 사용하고,  
크로스 케이블은 **컴퓨터 간에 직접 랜 케이블로 연결할 때** 사용한다.

컴퓨터 간에 직접 데이터를 보낼 때는 양쪽 컴퓨터 모두 1번과 2번 선을 사용한다.

다이렉트의 구조는 양쪽 컴퓨터에서 1번과 2번으로 데이터를 전송하면 데이터가 충돌한다.

그래서 크로스 케이블은 일부러 중간에 전선을 교차시켜서 송신 측과 수신 측이 올바르게 연결되도록 하고 있다.

<br><br>

# 리피터와 허브의 구조

<br>

## 리피터란?

<br>

> **리피터**(repeater):
> 전기 신호를 정형(일그러진 전기 신호를 복원)하고 증폭하는 기능을 가진 네트워크 중계 장비.

<br>

전기 신호를 전송할 때 전송하는 거리가 멀어지면 신호가 감쇠하는 성질이 있는데, 이때 감쇠된 전송 신호를 새롭게 재생하여 다시 전달하는 신호 중계 장치를 리피터라고 한다.

하지만 요즘은 다른 네트워크 장비가 리피터 기능을 지원하기 때문에 리피터를 쓸 필요가 없다.

<br>

## 허브란?

<br>

리피터 외에도 물리 계층에서 동작하는 네트워크 장비에는 **허브**(hub)라는 장비가 있다.

<br>

> **허브**(hub):
> 랜을 구성할 때 한 사무실이나 가까운 거리에 있는 장비들을 케이블을 사용하여 연결하는 장치.

<br>

허브는 **포트**(실제로 통신하는 통로)를 여러 개 가지고 있고, 리피터 허브라고도 불린다.  
리피터는 일대일 통신만 가능하지만 허브는 포트를 여러 개 가지고 있어서 **컴퓨터 여러 대와도 통신**할 수 있다.

허브는 리피터와 마찬가지로 **전기 신호를 정형하고 증폭하는 기능**을 한다.  
컴퓨터에서 보낸 전기 신호가 허브에 도착하는 동안 노이즈의 영향으로 파형이 변경될 때가 있는데, 그럴 때 허브가 파형을 정상으로 되돌리는 기능을 한다.

허브는 컴퓨터 여러 대를 서로 연결시킬 수 있어서, 직접 컴퓨터끼리 연결하지 않아도 통신할 수 있따.

하지만 허브는 어떤 특정 포트로부터 데이터를 받는다면 해당 포트를 제외한 나머지 모든 포트로도 받은 데이터를 전송하는 특징이 있다.  
이처럼 허브는 스스로 판단하지 않고, 전기 신호를 모든 포트로 보내서 **더비 허브**(dummy hub)라는 이름으로 불리기도 한다.

하지만 이런 단점이 있으면 불필요한 데이터가 전송되어 비효율적이기에 그 대책으로 나온 게 **스위치**(switch)라고 하는 네트워크 장비다.  
스위치는 데이터 링크 계층에서 동작하는 네트워크 장비다.
