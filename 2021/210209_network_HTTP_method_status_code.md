참고: [HTTP Method](https://medium.com/@lyhlg0201/http-method-d561b77df7), [Status Code](https://ko.wikipedia.org/wiki/HTTP#cite_note-8)

---

## HTTP Method

<img src="https://images.velog.io/images/gndan4/post/3481532e-c393-468c-9c75-297a152a41f9/image.png" width="70%">

### GET

서버에게 Resource를 보내도록 요청하는 데 사용한다. (서버의 Resource를 읽음)

<img src="https://images.velog.io/images/gndan4/post/5be165da-9fd2-4368-a52d-e58ec6050af4/Screen%20Shot%202021-02-09%20at%207.51.49%20PM.png" width="70%">

### HEAD

GET과 동일하지만 **서버에서 Body를 Return하지 않음**

- Resource를 받지 않고 오직 찾기만을 원할 때 사용
- object가 존재할 경우 응답의 상태 코드 확인할 때
- 서버의 응답 헤더를 봄으로써 Resource가 수정되었는 지 확인

<img src="https://images.velog.io/images/gndan4/post/57f1cd14-9b8f-4460-a155-e5ad45e4b0e1/Screen%20Shot%202021-02-09%20at%207.52.52%20PM.png" width="70%">

### PUT

서버에서 문서를 쓸 때 사용(GET과 반대)

- PUT 메서드는 서버가 **클라이언트가 보낸 요청의 Body를 확인**한다.
- 요청된 URL에 정의된 **새로운 Resource를 생성**하기 위함
- 요청된 URL이 존재할 경우 대체

<img src="https://images.velog.io/images/gndan4/post/d7a92f9f-214c-4a73-895c-390435d64305/image.png" width="70%">

### POST

**서버에 인풋 데이터를 보내기 위함** (HTML form에 많이 사용)

#### PUT vs POST

- PUT은 서버의 Resource에 데이터를 저장하기 위한 용도
- POST는 서버에 데이터를 보내기 위한 용도

<img src="https://images.velog.io/images/gndan4/post/8869aed5-db58-4f58-a9b2-335a5f406925/image.png" width="50%">

<img src="https://images.velog.io/images/gndan4/post/5c10fff0-62fd-46ce-ba35-6c1bcc3151c8/image.png" width="70%">

### TRACE

클라이언트로부터 Request Packet이 방화벽, Proxy Server, Gateway 등을 packet의 변조가 일어날 수 있는데, 이때 **서버에 도달했을 때의 최종 Packet의 Request Packet을 볼 수 있다.**

- 즉, 원본 데이터와 서버에 도달했을 때의 비교본 데이터를 서버의 응답 Body를 통해 확인할 수 있다.
- 요청의 최종 수신자는 반드시 **송신자에게 200(OK) 응답의 내용(Body)으로 수신한 메세지를 반송**해야 한다.
- 최초 클라이언트의 요청에는 Body가 포함될 수 없다.

<img src="https://images.velog.io/images/gndan4/post/fb030cb8-7804-4b18-9dc2-8ca1e3e6f6fe/image.png" width="70%">

### OPTION

타겟 서버의 지원 가능한 메서드들을 알아보기 위함

<img src="https://images.velog.io/images/gndan4/post/16cd98c9-136e-450e-b70b-71a5f51cb568/image.png" width="70%">

### DELETE

- Resource를 삭제하도록 요청
- 그러나 HTTP 규격에는 클라이언트의 요청도 서버가 무효화시킬 수 있도록 정의되어 있음
- DELETE 메서드는 항상 보장되지는 않는다.

<img src="https://images.velog.io/images/gndan4/post/5594a3d6-5ef9-4d48-87d2-a81382f20022/image.png" width="70%">

---

## HTTP Status Code

### 1XX (정보 제공)

| 코드 |       메시지        |                                                  설명                                                  |
| :--: | :-----------------: | :----------------------------------------------------------------------------------------------------: |
| 1XX  |  Information(정보)  |                                               정보 교환                                                |
| 100  |      Continue       | 클라이언트로부터 일부 요청을 받았으니 나머지 요청 정보를 계속 보내주길 바람. (HTTTP 1.1에서 처음 등장) |
| 101  | Switching Protocols |  서버는 클라이언트의 요청대로 Upgrade 헤더를 따라 다른 프로토콜로 바꿀 것임 (HTTP 1.1에서 처음 등장)   |

### 2XX (성공)

| 코드 |           메시지           |                                                                 설명                                                                 |
| :--: | :------------------------: | :----------------------------------------------------------------------------------------------------------------------------------: |
| 2XX  |       Success(성공)        |                                   데이터 전송이 성공적으로 이루어졌거나, 이해되었거나, 수락되었음                                    |
| 200  |             OK             |                                                         오류 없이 전송 성공                                                          |
| 202  |          Accepted          |                                                  서버가 클라이언트의 요청을 수락함                                                   |
| 203  | Non-authorized Information |                                                서버가 클라이언트 요구 중 일부만 전송                                                 |
| 204  |        Non Content         |                                         클라이언트의 요구를 처리했으나 전송할 데이터가 없음                                          |
| 205  |       Reset Content        | 새 문서 없음. 하지만 브라우저는 문서 창을 리셋해야 함(브라우저가 CGI 폼 필드를 전부 지우도록 할 때 사용 됨) (HTTP 1.1에서 처음 등장) |
| 206  |      Partial Content       |                 클라이언트가 Range 헤더와 함께 요청의 일부분을 보냈고 서버는 이를 수행했음 (HTTP 1.1에서 처음 등장)                  |

### 3XX (리다이렉션)

| 코드 |         메시지         |                                                                             설명                                                                             |
| :--: | :--------------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------: |
| 3XX  | Redirection(방향 바꿈) |                                                                    자료의 위치가 바뀌었음                                                                    |
| 300  |    Multiple Choices    |                                                                 최근에 옮겨진 데이터를 요청                                                                  |
| 301  |   Moved Permanently    |                                                            요구한 데이터를 변경된 URL에서 찾았음                                                             |
| 302  |   Moved Permanently    |                                요구한 데이터가 변경된 URL에 있었음을 명시. 301과 비슷하지만 새 URL은 임시 저장 장소로 해석됨                                 |
| 303  |       See Other        |                                                      요구한 데이터를 변경하지 않았기 때문에 문제가 있음                                                      |
| 304  |      Not modified      | 클라이언트의 캐시에 이 문서가 저장되었고 선택적인 요청에 의해 수행됨 (보통 지정된 날짜보다 더 나중의 문서만을 보여주도록 하는 If-Modified-Since 헤더의 경우) |
| 305  |       Use Proxy        |                                  요청된 문서는 Location 헤더에 나열된 프록시를 통해 추출되어야 함 (HTTP 1.1에서 처음 등장)                                   |
| 307  |   Temporary Redirect   |                                                                   자료가 임시적으로 옮겨짐                                                                   |

### 4XX (클라이언트 요청 오류)

|  코드  |            메시지             |                                                                      설명                                                                      |
| :----: | :---------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------: |
|  4XX   | Client Error(클라이언트 오류) |                                        클라이언트 측의 오류. 주소를 잘못 입력하였거나 요청이 잘못되었음                                        |
|  400   |         Bad Requeset          |                                        요청 실패. 문법 상 오류가 있어서 서버가 요청사항을 이해하지 못함                                        |
| 401.1  |         Unauthorized          |                       권한 없음(접속 실패). 서버에 로그온 하려는 요청사항이 서버에 들어있는 권한과 비교했을 떄 맞지 않음                       |
| 401.2  |         Unauthorized          |             권한 없음(서버 설정으로 인한 접속 실패). 서버에 로그온 하려는 요청사항이 서버에 들어있는 권한과 비교했을 때 맞지 않음              |
| 401.3  |         Unauthorized          |                             권한 없음(자원에 대한 ACL에 기인한 권한 없음). 클라이언트가 특정 자료에 접근할 수 없음                             |
| 401.4  |         Unauthorized          |                  권한 없음(필터에 의한 권한 부여 실패). 서버에 접속하는 사용자들을 확인하기 위해 설치한 필터 프로그램이 있음                   |
| 401.5  |         Unauthorized          | 권한 없음(ISA PI/CGI 어플리케이션에 의한 권한부여 실패). 이용하려는 서버의 주소에 ISA PI나 CGI 프로그램이 설치되어 있고, 권한을 부여할 수 없음 |
|  402   |       Payment Required        |                                                                     예약됨                                                                     |
| 403.1  |           Forbidden           |                         금지(실행접근 금지). 실행시키지 못하도록 되어 있는 디렉토리 내의 실행 파일을 실행하려고 하였음                         |
| 403.2  |           Forbidden           |                                        금지(읽기접근 금지)/ 접근한 데릭토리에 가용한 기본 페이지가 없음                                        |
| 403.4  |           Forbidden           |                                         금지(SSL 필요함). 접근하려는 페이지가 SSL로 보안유지 되고 있음                                         |
| 403.5  |           Forbidden           |                                       금지(SSL 128 필요함). 페이지가 128비트의 SSL로 보안유지 되고 있음                                        |
| 403.6  |           Forbidden           |                                          금지(IP 주소 거부됨). 사용자가 허용되지 않은 IP로부터 접근함                                          |
| 403.7  |           Forbidden           |                                   금지(클라이언트 확인 필요). 클라이언트가 자료에 접근할 수 있는지 확인 요함                                   |
| 403.8  |           Forbidden           |                  금지(사이트 접근 거부됨). 서버가 요청사항을 수행하고 있지 않거나, 해당 사이트에 접근하는 것이 허락되지 않음                   |
| 403.9  |           Forbidden           |                                접근금지(연결된 사용자 수 과다). 서버가 BUSY 상태에 있어서 요청을 수행할 수 없음                                |
| 403.10 |           Forbidden           |                                                         접근금지(설정이 확실하지 않음)                                                         |
| 403.11 |           Forbidden           |                                               접근금지(패스워드 변경됨). 잘못된 암호를 입력했음                                                |
| 403.12 |           Forbidden           |                           접근금지(Mapper 접근 금지됨). 클라이언트 인증용 맵이 해당 웹 사이트에 접근하는 것이 거부됨                           |
|  404   |           Not Found           |                                        문서를 찾을 수 없음. 서버가 요청한 파일이나 스크립트를 찾지 못함                                        |
|  405   |      Method not allowed       |                         메서드 허용 안 됨. 요청 내용에 명시된 메서드를 수행하기 위한 해당 자원의 이용이 허용되지 않음                          |
|  406   |        Not Acceptable         |                                                                받아들일 수 없음                                                                |
|  407   | Proxy Authentication Required |                                                          프록시 서버의 인증이 필요함                                                           |
|  408   |        Request timeout        |                                                                요청 시간이 지남                                                                |
|  409   |           Conflict            |       요청을 처리하는 데 문제가 있음. 보통 PUT 요청과 관계가 있다. 보통 다른 버전의 파일을 업로드할 경우 발생함 (HTTP1.1에서 새로 등장)        |
|  410   |             Gone              |                                                           영구적으로 사용할 수 없음                                                            |
|  411   |        Length Required        |                      클라이언트가 헤더에 Content-Length를 포함하지 않으면 서버가 처리할 수 없음 (HTTP 1.1에서 새로 등장)                       |
|  412   |      Precondition Failed      |                                     선결조건 실패. 헤더의 하나 이상의 선결조건을 서버에서 충족시킬 수 없음                                     |
|  413   |     Request-URI too long      |                                                              요청한 URI가 너무 김                                                              |
|  414   |    Unsupported media type     |                                             요청이 알려지지 않은 형태임. (HTTP 1.1에서 새로 등장)                                              |
|  415   |    Unsupported media type     |                                             요청이 알려지지 않은 형태임. (HTTP 1.1에서 새로 등장)                                              |

### 5XX (서버 응답 오류)

| 코드 |           메시지           |                                                              설명                                                              |
| :--: | :------------------------: | :----------------------------------------------------------------------------------------------------------------------------: |
| 5XX  |  Server Error(서버 오류)   |                                         서버 측의 오류로 올바른 요청을 처리할 수 없음                                          |
| 500  |   Internal Server Error    |                                                         서버 내부 오류                                                         |
| 501  |      Not Implemented       |                                              필요한 기능이 서버에 구현되지 않았음                                              |
| 502  |        Bad gateway         |                                                      게이트웨이 상태 나쁨                                                      |
| 503  |    Service Unavailable     |                                외부 서비스가 죽었거나 현재 멈춘 상태 또는 이용할 수 없는 서비스                                |
| 504  |      Gateway timeout       | 프록시나 게이트웨이 역할을 하는 서버에서 볼 수 있음. 초기 서버가 원격 서버로부터 응답을 받을 수 없음. (HTTP 1.1에서 새로 등장) |
| 505  | HTTP Version Not Supported |                                                 해당 HTTP 버전을 지원하지 않음                                                 |
