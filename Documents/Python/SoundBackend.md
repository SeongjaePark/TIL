송은우 님의 **깔끔한 파이썬 탄탄한 백엔드** 서적을 통해 공부한 내용 정리

<details>
  <summary>Chapter 3. 첫 API 개발 시작 </summary>

# Chapter 3 첫 API 개발 시작

## ping 엔드포인트 구현하기

### 엔드포인트란?

엔드포인트는 API 서버가 제공하는 통신 채널 혹은 접점이라고 할 수 있다.

프론트엔드 서버 등의 클라이언트가 백엔드 API 서버와 통신할 때 엔드포인트에 접속하는 형태로 통신하게 된다.

각 엔드포인트는 고유의 URL 주소를 가지게 되며, 고유의 URL 주소를 통해 해당 엔드포인트에 접속할 수 있다.

일반적으로 각 엔드포인트는 고유의 기능을 담당하고 있다. 그리고 이러한 엔드포인트들이 모여서 하나의 API를 구성하는 것이다.

- 예: SNS 서비스를 위한 API는 사용자 sign up 엔드포인트, 사용자 로그인 엔드포인트, 새로운 포스팅 생성 엔드포인트, 다른 사요자와 친구 맺기 엔드포인트 등
- cf) 최근에 나온 기술인 GraphQL(Graph Query Language)은 여러 엔드포인트로 구성되어 있지 않고 단 하나의 엔드포인트로 모든 기능을 제공하는 형태로 구성된다.

### ping 엔드포인트

ping 엔드포인트는 단순히 "pong" 이라는 텍스트를 리턴(return) 하는 엔드포인트다. 이름 그대로 ping pong 처럼, ping 엔드포인트를 호출하면 "pong"이라고 응답하는 것이다.

ping 엔드포인트는 주로 API 서버가 현재 운행되고 있는지 아니면 정지된 상태인지를 간단하게 확인할 때 사용된다.

이러한 기능을 하는 엔드포인트를 헬스 체크(health check) 엔드포인트라고 한다. API 서버에 접속하지 않고 해당 API의 정상 운행 여부를 간단하게 체크하는 엔드포인트다.

### 로컬 호스트

로컬 호스트는 시스템이 실행되고 있는 해당 컴퓨터를 이야기한다. 로컬 호스트의 IP 주소는 127.0.0.1 이다. 컴퓨터 환경에선느 자기 자신을 접근하는 경우가 굉장히 자주 있기 때문에 운영 시스템(OS)에서 항상 고정된 호스트 이름과 IP 주소를 제공하는데 이것이 바로 로컬 호스트와 127.0.0.1 이다. 그러므로 127.0.0.1 IP 주소는 예약(reserved)된 IP 주소이며 인터넷상에서 일반 IP로는 쓰일 수 없다.

## 3장 정리

- Flask는 파이썬 웹 애플리케이션을 구현할 때 사용되는 프레임워크이며, Django와 다르게 웹 애플리케이션을 구현할 때 꼭 필요한 기능만을 제공하는 프레임워크다. 그러므로 학습 곡선이 비교적 낮다.
- 파이썬 개발을 할 때에는 먼저 파이썬 가상 환경을 생성한 후 항상 활성화시킨 상태에서 개발, 실행, 테스트를 해야 한다. 파이썬 가상 환경을 생성하는 방법은 여러 가지가 있지만, 콘다를 사용하여 파이썬 개발 환경을 생성하는 것이 선호된다.
- Flask에서는 일반적으로 route 데코레이터를 사용해서 함수들을 엔드포인트로 등록하는 방식이 사용된다. 즉, Flask에서 엔드포인트를 구현한단느 것은 결국은 일반 함수를 구현하는 것과 마찬가지다. 그러므로 백엔드 API 개발도 구조적으로는 크게 어렵거나 복잡할 것이 없다. 해당 API가 제공하는 서비스, 즉 비즈니스 로직 (business logic)을 구현하는 함수들을 개발하는 것이 백엔드 API에서 차지하는 가장 큰 부분이 된다.
- 백엔드 API 개발 입문에서 중요한 것은 먼저 기본적인 개념을 먼저 잘 이해하고, 그러고 난 후 API 코드의 전체적인 구조에 대해서 이해하는 것이 핵심이다. API의 개념을 잘 이해해서 구조를 잘 잡고 나면 그 다음은 필요한 비즈니스 로직을 함수를 통해 구현하기만 하면 된다. API 코드의 전체적인 구조가 일단 잡히면 그 다음부터는 엔드포인트들, 즉 함수들을 구현하는 것이 개발의 대부분이다. 함수를 구현하는 것은 개념적이나 구조적으로는 어려울 것이 없다.
- API를 개발하기 위해 필수적인 기본 개념들 중 가장 중요한 것 하나가 바로 HTTP다 왜냐하면 API는 기본적으로 HTTP 통신에 기반을 두고 있기 때문이다.
</details>

<details>
  <summary>Chapter 4. HTTP의 구조 및 핵심 요소</summary>

# Chapter 4 HTTP의 구조 및 핵심 요소

프론트엔드 시스템과 백엔드 API 시스템은 일반적으로 HTTP 프로토콜을 기반으로 통신한다.

# HTTP

HTTP는 HyperText Transfer Protocol의 약자로, 웹상에서 서로 다른 서버 간에 하이퍼텍스트 문서, 즉 HTML을 서로 주고받을 수 있도록 만들어진 프로토콜, 통신 규약임

# HTTP 통신 방식

HTTP 통신 방식에는 2가지 특징이 있음.

1. HTTP의 요청(request)와 응답(response) 방식임
2. stateless임

## 1) HTTP 요청과 응답

HTTP는 기본적으로 요청과 응답의 구조로 되어 있음

클라이언트가 먼저 HTTP 요청을 서버에 보내면 서버는 요청을 처리한 후 결과에 따른 HTTP 응답을 클라이언트에게 보냄으로써 하나의 HTTP 통신이 됨

그러므로 백엔드 API 시스템의 엔드포인트 구현도 기본적으로 HTTP 요청을 인풋으로 받아서 HTTP 응답을 아웃풋으로 리턴하는 구조로 구현하게 됨

Flask가 HTTP 부분을 자동으로 처리해 주기 때문에, Flask를 사용하면 개발자는 최대한 일반 함수를 구현하듯이 엔드포인트를 구현할 수 있다.

## 2) stateless

HTTP 통신은 "stateless"다.

stateless라는 말 그대로 상태(state)가 없다는 뜻으로, HTTP 통신에서는 상태의 개념이 존재하지 않는다.

클라이언트와 서버는 HTTP 통신을 여러 번 주고받는 것이 일반적인데, HTTP 프로토콜에서는 동일한 클라이언트와 서버가 주고받은 HTTP 통신들이라도 서로 연결되어 있지 않다.

즉, 각각의 HTTP 통신은 독립적이며 그 전에 처리된 HTTP 통신에 대해서 전혀 알지 못한다. 그래서 HTTP 프로토콜은 stateless라고 하는 것이다.

HTTP 프로토콜이 stateless 이기 때문에 서버 디자인이 훨씬 간단해지고 효과적인 장점이 있다.

- HTTP 통신들의 상태를 서버에서 저장할 필요가 없으므로 여러 다른 HTTP 통신 간의 진행이나 연결 상태의 처리나 저장을 구현 및 관리하지 않아도 되기 때문이다.
- 오직 각각의 HTTP 요청에 대해 독립적으로 응답만 보내 주면 된다.

다만 단점은 stateless 이기 때문에 HTTP 요청을 보낼 때는 해당 요청을 처리하기 위해 필요한 모든 데이터를 매번 포함시켜여 요청을 보내야 한다는 점이다.

- 예를 들어, 어떤 HTTP 요청을 처리하기 위해서 해당 사용자가 로그인이 되어야 한다고 가정 해보자.
- 해당 사용자가 이미 그 전의 HTTP 통신을 통해서 로그인을 한 상태라고 하더라도 HTTP는 stateless 이기 때문에 새로 보내는 HTTP 통신에서는 해당 사용자가 그 전 HTTP 통신에서 로그인했다는 사실을 알지 못한다.
- 그러므로 새로운 HTTP 요청을 보낼 때 해당 사용자의 로그인 사실 여부를 포함시켜서 보내야 한다.
- 사용자의 로그인 사실 여부를 포함시켜서 HTTP 요청을 보내기 위해서는 클라이언트가 사용자의 로그인 사실 여부를 기억하고 있어야 한다.

이러한 점들을 해결하기 위해서 쿠키(cookie)나 세션(session) 등을 사용하여 HTTP 요청을 처리할 때 필요한 진행 과정이나 데이터를 저장한다.

- 쿠키(cookie)는 웹 브라우저가 웹사이트에서 보내온 정보를 저장할 수 있도록 하는 조그마한 파일을 말한다. 웹 브라우저는 쿠키라고 하는 파일을 사용해서 필요한 정보를 저장한다.
- 세션(session)은 쿠키와 마찬가지로 HTTP 통신상에서 필요한 데이터를 저장할 수 있게 하는 매커니즘이다. 쿠키는 웹 브라우저, 즉 클라이언트 측에서 데이터를 저장하는 반면에 세션은 웹 서버에서 데이터를 저장한다.

# HTTP 요청 구조

HTTP 요청 메시지는 크게 다음의 세 부분으로 구성되어 있다.

1. Start Line
2. Headers
3. Body

예시:

```
POST /payment-sync HTTP/1.1   #  Start Line

Accept: application/json           # Headers
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 83
Content-Type: application/json
Host: intropython.com
User-Agent: HTTPie/0.9.3

{                                 # Body
	"imp_uid": "imp_123456789,
	"merchant_uid": "order_id_82373532",
	"status": "paid"
}
```

cf) HTTP 요청과 응답 메시지의 모든 부분을 직접 구현할 필요는 없다. Flask(혹은 Django 등의 다른 웹 프레임워크)가 거의 대부분을 알아서 처리해 준다. 일반적으로 개발자가 직접 지정해야 하는 부분은 HTTP 메소드와 status code, 몇 개의 헤더 정보, 그리고 body 부분이다 하지만 그래도 HTTP 응답과 요청의 구조와 내용을 이해는 하고 있어야 한다.

## 1. Start Line

이름 그대로 HTTP 요청의 시작줄임.

예를 들어, "search" 엔드포인트에 GET HTTP 요청을 보낸다면 해당 HTTP 요청의 start line은 다음과 같다.

`GET /search HTTP/1.1`

start line은 세 부분으로 구성되어 있다.

### **1) HTTP 메소드**

- 해당 HTTP 요청이 의도하는 액션(action)을 정의하는 부분
- 서버로부터 어떤 데이터를 받고자 한다면 GET 요청을 보내고, 서버에 새로운 데이터를 저장하고자 한다면 POST 요청을 보내는 식
- GET, POST, PUT, DELETE, OPTION 등 여러 메소드들이 있음. 그 중 GET과 POST가 가장 널리 쓰임

### **2) Request target**

- 해당 HTTP 요청이 전송되는 목표 주소
- "search" 엔드포인트에 보내는 HTTP 요청의 경우 request target은 "/search"가 됨

### **3) HTTP version**

- 해당 요청의 HTTP 버젼을 나타냄
- 현재 "1.0", "1.1", 그리고 "2.0"이 있음
- 버젼을 명시하는 이유는 HTTP 버젼에 따라 HTTP 요청 메시지의 구조나 데이터가 약간씩 다를 수 있으므로 서버가 받은 요청의 HTTP version에 맞추어서 응답을 보낼 수 있도록 하기 위함임

## 2. Header

start line 다음에 나오는 부분은 헤더(header)임

헤더 정보는 HTTP 요청 그 자체에 대한 정보를 담고 있음. ex) HTTP 요청 메시지의 전체 크기(Content-Length)

헤더는 파이썬의 dictionary처럼 key와 value로 되어 있음. `key:value` 로 표현됨

### **다양한 헤더의 종류**

- **Host**
  - 요청이 전송되는 target의 호스트의 URL 주소를 알려줌
  - 예: Host: google.co
- **User-Agent**
  - 요청을 보내는 클라이언트에 대한 정보: ex) 웹 브라우저에 대한 정보
- **Accept**
  - 해당 요청이 받을 수 있는 응답(response) body 데이터 타입을 알려줌
  - MIME (Multipurpose Internet Mail Extension) type이 value로 지정됨. 예를 들어 JSON 데이터 타입을 요청하는 경우에는 application/json MIME type을 value로 지정해 주면 됨. 모든 데이터 타입을 다 허용하는 경우는 \*/ \*로 지정해주면 됨
  - API에서 자주 사용되는 MIME type: application/json, application/octet-stream, text/csv, text/html, image/jpeg, image/png, text/plain, application/xml
  - 예: Accept: \*/\*
- **Connection**
  - 해당 요청이 끝난 후에 클라이언트와 서버가 계속해서 네트워크 연결을 유지할 것인지 아니면 끊을 것인지에 대해 알려 줌
  - HTTP 통신에서 서버 간에 네트워크 연결하는 과정이 다른 작업에 비해 시간이 걸리는 부분이므로 HTTP 요청 때마다 네트워크 연결을 새로 만들지 않고 HTTP 요청이 계속되는 한 처음 만든 연결을 재사용하는 것이 선호되는데, 이에 관한 정보를 전달하는 헤더임
  - connection 헤더의 값이 keep-alive 이면 앞으로도 계속해서 HTTP 요청을 보낼 예정이므로 네트워크 연결을 유지하라는 뜻임
  - 값이 close 라고 지정되면 더 이상 HTTP 요청을 보내지 않을 것이므로 네트워크 연결을 닫아도 된다는 뜻임
  - 예: Connection: keep-alive
- **Content-Type**
  - HTTP 요청이 보내는 메시지 body의 타입을 알려 줌
  - Accept 헤더와 마찬가지로 MIME type이 사용됨.
  - 예: Content-Type: application/json
- **Content-Length**
  - HTTP 요청이 보내는 메시지 body의 총 사이즈를 알려 줌
  - 예: Content-Length: 257

## 3. Body

HTTP 요청 메시지에서 body 부분은 HTTP 요청이 전송하는 데이터를 담고 있는 부분임. 전송하는 데이터가 없다면 body 부분은 비어 있게 됨

# HTTP 응답 구조

HTTP 응답 메시지의 구조도 요청 메시지와 마찬가지로 크게 세 부분으로 구성되어 있음

1. Status Line
2. Headers
3. Body

예시

```
HTTP/1.1 404 Not Found     # Status Line

Connection: close          # Headers
Content-Length: 1573
Content-TYpe: text/html; charset=UTF-8
Date: Mon, 19 Oct 2020 09:53:05 GMT

<!DOCTYPE html>           # Body
###HTML 내용
```

## 1. Status Line

HTTP 응답 메시지의 상태를 간략하게 요약하여 알려 주는 부분

HTTP 요청의 start line과 마찬가지로 status line도 세 부분으로 구성되어 있다

### **1) HTTP Version**

- 사용되고 있는 HTTP 버젼

### **2) Status Code**

- HTTP 응답 상태를 미리 지정되어 있는 숫자로 된 코드로 나타냄
- 예: 요청이 정상적으로 처리된 경우 - 200

### **3) Status Text**

- HTTP 응답 상태를 간략하게 글로 설명해 주는 부분
- 예: 요청이 정상적으로 처리된 경우 - OK

**Status Line** **예시**

```
HTTP/1.1 404 Not Found
```

## 2. Header

HTTP 요청의 헤더 부분과 동일. 다만 HTTP 응답에서만 사용되는 헤더 값들이 있다.

예를 들어, HTTP 응답에는 User-Agent 헤더 대신에 Server 헤더가 사용됨

## 3. Body

HTTP 요청 메시지의 body와 동일. 요청 메시지와 마찬가지로 전송하는 데이터가 없다면 body 부분은 비어있게 됨.

# 자주 사용되는 HTTP 메소드

## GET

- POST 메소드와 함께 가장 자주 사용되는 메소드
- 어떤 데이터를 서버로부터 요청할 때 주로 사용
- 데이터의 생성이나 수정, 그리고 삭제 등의 변경 사항 없이 단순히 데이터를 받아 오는 요청이 주로 GET 메소드로 요청됨
- 해당 HTTP 요청의 body가 비어 있는 경우가 많음

## POST

- GET 메소드와 함께 가장 자주 사용되는 메소드
- 데이터를 생성하거나 수정 및 삭제 요청할 때 사용

## OPTIONS

- 주로 특정 엔드포인트에서 허용하는 메소드들이 무엇이 있는지 알고자 할 때 사용
- 엔드포인트는 허용하는 HTTP 메소드가 지정되도록 되어 있으며, 허용하지 않는 HTTP 메소드의 요청이 들어오면 **405 Method Not Allowed** 응답을 보내게 됨
- 예: ping 엔드포인트에 OPTIONS 요청을 보내면 받는 응답

```
HTTP/1.0 200 OK

Allow: GET, HEAD, OPTIONS
Content-Length: 0
Content-Type: text/html; charset=utf-8
Date: Mon, 19 Oct 2020 14:18:26 GMT
Server: Werkzeug/1.0.1 Python/3.7.9
```

ping 엔드포인트르 구현할 때 GET 메소드만 허용하도록 구현했는데 HEAD OPTIONS 메소드까지 허용되어 있음. Flask가 자동으로 HEAD와 OPTIONS 요청에 대한 응답을 구현해주기 때문. 개발자가 직접 OPTIONS 메소드에 대한 처리를 구현하지 않아도 됨

## PUT

- 데이터를 새로 생성할 때 사용 (POST와 비슷한 의미)
- POST와 중복되는 의미이므로 데이터를 새로 생성하는 HTTP 요청을 보낼 때 굳이 PUT을 사용하지 않고 모든 데이터 생성 및 수정 관련한 요청은 다 POST로 통일해서 사용하는 시스템이 많아지고 있음

## DELETE

- 데이터 삭제 요청을 보낼 때 사용
- PUT과 마찬가지로, POST에 밀려서 잘 사용되지 않음

# 자주 사용되는 HTTP Status Code와 Text

## 200 OK

- HTTP 요청이 문제 없이 성공적으로 잘 처리 되었을 때 보내는 status code

## 301 Moved Permanently

- HTTP 요청을 보낸 엔드포인트의 URL 주소가 바뀌었다는 것을 나타냄
- 301 status code의 HTTP 응답은 Location 헤더가 포함되는 것이 일반적인데, Location 헤더에 해당 엔드포인트의 새로운 주소가 포함되어 나옴
- 301 요청을 받은 클라이언트는 Location 헤더의 엔드포인트의 새로운 주소에 해당 요청을 다시 보내게 됨. 이러한 과정을 "redirection" 이라고 함.

```
HTTP/1.1 301 Moved Permanently
Location: http://www.example.org/index.asp
```

## 400 Bad Request

- HTTP 요청이 잘못된 요청일 때 보냄
- 주로 요청에 포함된 인풋 값들이 잘못된 경우 사용
- 예: 사용자의 전화번호를 저장하는 HTTP 요청인데 전화번호에 숫자가 아닌 글자가 포함되었을 경우

## 401 Unauthorized

- 해당 요청을 보내는 주체(사용자 혹은 클라이언트)의 신분(credential) 확인이 요구되는 경우에 이를 확인할 수 없었을 때 보냄
- 주로 해당 HTTP 요청을 보내는 사용자가 로그인이 필요한 경우 401 응답을 보냄

## 403 Forbidden

- 요청을 보내는 주체가 해당 요청에 대한 권한이 없음을 나타냄
- 예: 비용을 지불한 사용자만 볼 수 있는 데이터에 대한 HTTP 요청을 보낸 사용자가 아직 비용을 지불하지 않은 상태일 경우

## 404 Not Found

- HTTP 요청을 보내고자 하는 URL이 존재하지 않을 떄 보냄
- 예: "해당 페이지를 찾을 수 없습니다" 라는 메시지가 적인 페이지 = 404 페이지

## 500 Internal Server Error

- 내부 서버 오류가 발생했다는 것을 알려 줌
- HTTP 요청을 받은 서버에서 해당 요청을 처리하는 과정에서 서버 오류가 나서 해당 요청을 처리할 수 없을 때 사용

# API 엔드포인트 아키텍처 패턴

API의 엔드포인트 구조를 구현하는 널리 알려진 패턴에는 크게 2가지가 있음

- REST 방식: 가장 널리 사용되는 API 엔드포인트 아키텍처 패턴임.
- GraphQL: 페이스북이 개발한 기술로 비교적 최근에 나온 기술

## RESTful HTTP API

REST(Representational State Transfer)ful HTTP API

API에서 전송하는 리소스를 URI(Uniform Resource Identifier)로 표현하고 해당 리소스에 행하고자 하는 의도를 HTTP 메소드로 정의하는 방식

각 엔드포인트는 처리하는 리소스를 표현하는 고유의 URI 주소를 가지고 있으며, 해당 리소스에 행할 수 있는 행위를 표현하는 HTTP 메소드를 처리할 수 있게 됨

예: 사용자 정보를 리턴하는 "/users" 라는 엔드포인트에서 사용자 정보를 받아 오는 HTTP 요청은 다음과 같이 표현할 수 있음

```
HTTP GET /users
GET /users
```

새로운 사용자를 생성하는 엔드포인트는 URI를 "/user/로 정하고 HTTP 요청은 다음과 같이 표현할 수 있음

```
POST /user
{
	"name"  : "박성재"
	"email" : "1234@gmail.com"
```

이러한 구조로 설계된 API를 RESTful API라고 함

### 장점

자기 설명력(self-descriptiveness)

- 엔드포인트의 구조만 보더라도 해당 엔드포인트가 제공하는 리소스와 기능을 파악할 수 있음
- API를 구현하다 보면 엔드포인트의 수가 많아지면서 엔드포인트의 역할고 기능 파악이 쉽지 않은데, REST 방식으로 구현하면 구조가 훨씬 직관적이며 간단해짐

## GraphQL

REST 방식으로 구현해도 여전히 구조적으로 생기는 문제들이 있음.

가장 자주 생기는 문제는 API의 구조가 특정 클라이언트에 맞추어져서 다른 클라이언트에서 사용하기에 적합하지 않게 된다는 점임

REST 방식의 API에서는 클라이언트들이 API가 엔드포인트들을 통해 구현해 놓은 틀에 맞추어 사용해야 하다 보니 그 틀에서 벗어나는 사용은 어려워 진다.

이러한 문제를 해결하기 위해서 페이스북은 GraphQL을 만들게 된다.

GraphQL은

- 엔드포인트가 오직 하나
- 엔드포인트에 클라이언트가 필요한 것을 정의해서 요청
- 기존 REST 방식의 API와 반대(서버가 정의한 틀에서 클라이언트가 요청하는 것이 아니라, 클라이언트가 필요한 것을 서버에 요청하는 방식)

### 예시

아이디가 1인 사용자의 정보와 그의 친구들의 이름 정보를 API로부터 받아와야 하는 경우

REST 방식 API - 아래와 같이 두 번의 HTTP 요청을 보내야 함

```
GET /users/1
GET /users/1/friends
```

위의 요청을 한 번의 HTTP 요청으로 줄이기 위해서는 아래와 같이 보내야 함

```
GET /users/1?include=friends.name
```

둘 다 비효율적이고 불필요하게 복잡함.

만일 사용자 정보들 중 다 필요하지 않고 이름만 필요하든가 혹은, 친구들의 이름 외에도 친구들의 이메일도 필요하다면 HTTP 요청은 더 복잡해질 것임

GraphQL을 사용하면 아래와 같이 HTTP 요청을 보내면 됨

```
POST /graphql

{
	user(id: 1) {
		name
		age
		friends {
			name
		}
	}
}
```

만일 사용자 정보는 이름만 필요하고, 대신 친구들의 이름과 이메일이 필요한 경우

```
POST /graphql

{
	user(id: 1) {
		name
		friends {
			name
			email
		}
	}
}
```

GraphQL은 장점이 많지만, REST에 비해서는 나온 지 오래 되지 않은 기술이므로 REST 만큼은 널리 사요되고 있지 않음. 그에 비해 REST는 알려진 지 오래 되었으므로 이미 여러 시스템에서 사용되고 있음

# 4장 정리

- HTTP 통신은 요청과 응답으로 이루어져 있음. 클라이언트가 HTTP 요청을 보내면 서버는 해당 요청에 대한 응답을 보내는 것이 하나의 HTTP 통신임
- HTTP 통신은 stateless 임. 클라이언트와 서버는 통신을 여러 번 주고받는 것이 일반적인데, HTP 프로토콜에서는 동일한 클라이언트와 서버가 주고 받은 HTTP 통신들이라도 서로 연결되어 있지 않음. 즉, 각각의 HTTP 통신은 독립적이며, 그 전에 처리된 HTTP 통신에 대해서 전혀 알지 못함
- HTTP 요청 메시지는 크게 세 부분으로 구성되어 있음
  - Start Line
  - Header
  - Body
- HTTP 응답 메시지도 세 부분으로 구성되어 있음
  - Status Line
  - Header
  - Body
- 자주 사용되는 HTTP 메소드에는 GET, POST, OPTIONS, PUT, DELETE 등이 있음
- 자주 사용되는 HTTP 응답 코드와 응답 텍스트에는 200 OK, 301 Moved Permanently, 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 500 Internal Server Error 등이 있음
- API 엔드포인트 아키텍쳐 패턴 중 가장 널리 사용되는 패턴은 REST임. REST는 엔드포인트의 고유 주소(URI)와 허용하는 HTTP 메소드를 통해서 제공하는 리소스와 기능을 알 수 있게 해줌으로써 클라이언트가 API를 더 쉽게 이해하고 사용할 수 있게 해줌
- GraphQL은 REST보다 더 유연한 엔드포인트 구조를 구현할 수 있지만, REST 보다는 아직 널리 사용되고 있지 않음

</details>

<details>
  <summary>Chapter 5. 본격적으로 API 개발하기</summary>

# Chapter 5. 본격적으로 API 개발하기

구현할 API 시스템은 미니터(미니 트위터)

# 미니터의 기능

- 회원가입
- 로그인
- 트윗(tweet)
- 다른 회원 팔로우하기
- 다른 회원 언팔로우 하기
- 타임라인(해당 사용자와 사용자가 팔로우하는 사용자들의 트윗들)

실제 트위터처럼 많은 수의 동시 접속이나 HTTP 요청 처리 속도를 고려한 구현은 포함하지 않음

# 회원가입

사용자에게 이름, 이메일, 비밀번호 등의 기본적인 회원 정보를 HTTP 요청을 통해 받은 후 시스템상에 저장

- id
- name
- email
- password
- profile

## 회원가입 기능 구현 엔드포인트

```python
from flask import Flask, jsonify, request # 1

app = Flask(__name__)
app.users = {} # 2
app.id_count = 1 # 3

@app.route("/sign-up", methods=['POST']) # 4
def sign_up():
	new_user = request.json # 5
	new_user["id"] = app.id_count # 6
	app.users[app.id_count] = new_user # 7
	app.id_count = app.id_count + 1 # 8

	return jsonify(new_user) # 9
```

1. 필요한 Flask의 모듈들 임포트
   - request를 통해 사용자가 HTTP 요청을 통해 전송한 JSON 데이터를 읽어들일 수 있음.
   - jsonify는 dictionary 객체를 JSON으로 변환하여 HTTP 응답으로 보낼 수 있게 됨
2. 새로 가입한 사용자를 저장할 dictionary를 users 라는 변수에 정의
   - 키(key) = 사용자 아이디, 값(value) = dictionary에 저장되어 있는 사용자 정보가 될 것임
3. 회원가입하는 사용자의 id 값을 저장하는 변수
   - id는 1부터 시작하며 새로운 사용자가 회원가입을 할 때마다 id 값이 하나씩 증가
   - CF) 엄밀히 말하면 문제가 있을 수 있음. 만일 HTTP 요청들이 동시에 전송될 경우 id 값이 잘못 지정될 가능성이 있음. 이를 예방하기 위해서 atomic increment operation(여러 스레드가 동시에 값을 증가시킬 수 없고, 한 번에 한 스레드만 값을 증가시키는 것)을 사용해야 함.
   - 그러나 미니터에서 데이터베이스에 데이터를 저장할 것이고, id 값은 데이터베이스에서 자동 생성 해준다. atomic 연산은 API 개발 입문과는 직접 관련 X. 개인적으로 알아보기
4. route 데코레이터를 사용해서 엔드포인트 정의
   - 엔드포인트의 고유 주소는 "/sign-up"으로 정의하고, HTTP 메소드는 POST로 함
5. HTTP 요청을 통해 전송된 회원 정보를 읽어 들임
   - request는 엔드포인트에 전송된 HTTP 요청 정보(헤더, body 등)를 저장하고 있음
   - request.json은 해당 HTTP 요청을 통해 전송된 JSON 데이터를 파이썬 dictionary 형태로 변환해 줌
6. HTTP 요청으로 전송된 회원가입 정보에 id 값을 더해 줌
7. 회원가입하는 사용자의 정보를 #2 에서 생성한 dictionary에 저장
8. id_count, 즉 id 값에 1을 더해 줌.
   - 다음 회원 id 값이 이미 회원가입한 사용자들의 id 값과 겹치지 않게 함
9. 회원가입한 사용자의 정보를 JSON 형태로 전송함
   - jsonify를 사용해 dictionary를 JSON 형태로 변환
   - status code는 200이 됨. 원래는 status code도 지정해 주어야 하지만, 만일 지정해 주지 않으면 디폴트 값으로 200이 리턴 됨

## 실행

터미널을 열고 해당 파일이 있는 디렉토리로 이동 후 파이썬 가상 환경 활성화 후 Flask 실행

```
(api) [api] FLASK_ENV=development FLASK_APP=app.py flask run

 * Serving Flask app "app.py" (lazy loading)
 * Environment: development
 * Debug mode: on
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 270-073-916
```

FLASK_ENV는 Flask가 실행되는 개발 스테이지를 뜻함

- "developement"로 정해 놓으면 debug mode가 실행됨. debug mode가 실행되면 코드가 수정될 때마다 Flask가 자동으로 재실행되어 수정된 코드가 반영되도록 해줌

## 회원가입 요청 보내기

httpie를 사용하여 터미널에서 회원가입 HTTP 요청 보내기

```
(api) [api] http -v POST localhost:5000/sign-up name=박성재 email=1234@gmail.com password=test1234

POST /sign-up HTTP/1.1
Accept: application/json, */*;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 81
Content-Type: application/json
Host: localhost:5000
User-Agent: HTTPie/2.2.0

{
    "email": "1234@gmail.com",
    "name": "박성재",
    "password": "test1234"
}

HTTP/1.0 200 OK
Content-Length: 104
Content-Type: application/json
Date: Tue, 20 Oct 2020 07:41:27 GMT
Server: Werkzeug/1.0.1 Python/3.7.9

{
    "email": "1234@gmail.com",
    "id": 1,
    "name": "박성재",
    "password": "test1234"
}
```

httpie를 사용해서 POST로 JSON 데이터를 보내는 것은 아주 간단함.

- HTTP 요청을 보내는 엔드포인트 주소 다음에 field=value 의 형태로 보내면 됨
- 예를 들어 "name" 필드의 값을 "박성재"로 JSON 데이터 형태로 전송하기 위해서는 name=박성재 라고 지정해 주면 됨

# 300자 제한 트윗 올리기

메인 기능인 300자 제한 트윗 글 올리기 엔드포인트 구현

- 사용자는 300자를 초과하지 않는 글을 올릴 수 있음
- 만일 300자를 초과하면 엔드포인트는 400 Bad Request 응답을 보내야 함
- 사용자가 300자 이내의 글을 전송하면 엔드포인트는 사용자의 글을 저장하고 있어야 하고 사용자의 타임라인 엔드포인트를 통해서 읽을 수 있어야 함

## Tweet 엔드포인트를 호출할 때 전송하는 JSON 데이터

```
{
	"id" : 1,                    # 1
	"tweet" : "My First Tweet"   # 2
}
```

1. 트윗을 보내는 사용자의 아이디
2. 트윗 내용

## 트윗 엔드포인트 구현

```python
app.tweets = []   # 1

@app.route('/tweet', methods=['POST']) # 2
def tweet():
	payload = request.json
	user_id = int(payload['user_id'])
	tweet = payload['tweet'] # 3

	if user_id not in app.users:   # 4
		return '사용자가 존재하지 않습니다', 400

	if len(tweet) > 300:   # 5
		return '300자를 초과했습니다', 400

	app.tweets.append({
		'user_id' : user_id,
		'tweet' : tweet
		})

	return '', 200
```

1. 사용자들의 트윗들을 저장할 디렉토리. key는 사용자 아이디
   - key는 사용자 아이디, value는 사용자들의 트윗을 담고 있는 리스트
2. 엔드포인트의 주소는 "/tweet", HTTP 메소드는 POST
3. HTTP 요청으로 전송된 JSON 데이터에서 "tweet" 필드를 읽어 들임
4. 만일 해당 사용자 아이디가 존재하지 않으면 400 Bad Request 오류 메시지를 전송함
5. 만일 해당 사용자의 트윗이 300자를 넘었으면 "300자를 초과했습니다"라는 메시지와 함께 400 Bad Request 응답을 보냄
6. HTTP 요청으로 전송된 JSON 데이터에서 사용자 아이디를 읽어 들임
7. 해당 사용자 아이디와 트윗을 딕셔너리로 생성해서 app.tweets 리스트에 저장함.
   - 이후 타임라인 엔드포인트에서 app.tweets 리스트를 읽어 들임

## 실행

```
(api) [api] http -v POST localhost:5000/tweet id=1 tweet="My First Tweet"

POST /tweet HTTP/1.1
Accept: application/json, */*;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 38
Content-Type: application/json
Host: localhost:5000
User-Agent: HTTPie/2.2.0

{
    "id": "1",
    "tweet": "My First Tweet"
}

HTTP/1.0 400 BAD REQUEST
Content-Length: 38
Content-Type: text/html; charset=utf-8
Date: Tue, 20 Oct 2020 09:19:12 GMT
Server: Werkzeug/1.0.1 Python/3.7.9

사용자가 존재하지 않습니다
```

사용자가 생성이 안 되어서 400 Bad Request 오류가 난다.

회원가입 엔드포인트를 통해 사용자를 추가한 뒤 다시 시도해 보자

- 이미 사용자를 생성했다고 하더라도 만일 API가 재실행되면 기존에 생성했던 사용자 및 데이터들은 전부 지워짐
- 아직 데이터베이스에 데이터들을 저장하는 것이 아니라 메모리 상에서만 저장하는 것이므로 서버가 재실행되는 순간 메모리 상의 데이터들은 전부 지워짐

```
(api) [api] http -v POST localhost:5000/tweet id=1 tweet="My First Tweet"

POST /tweet HTTP/1.1
Accept: application/json, */*;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 38
Content-Type: application/json
Host: localhost:5000
User-Agent: HTTPie/2.2.0

{
    "id": "1",
    "tweet": "My First Tweet"
}

HTTP/1.0 200 OK
Content-Length: 0
Content-Type: text/html; charset=utf-8
Date: Tue, 20 Oct 2020 09:23:51 GMT
Server: Werkzeug/1.0.1 Python/3.7.9
```

200 OK 응답이 오면 정상적으로 구현된 것임

# 팔로우와 언팔로우 엔드포인트

</details>
