참고: [TCP School](http://tcpschool.com/html-input-types/hidden)

---

# `<input type="hidden">`

Django 인강을 들으면서 게시글 내용 수정 기능을 구현할 때, 해당 url의 html 작성 시
form에 `<input type="hidden">` 을 포함시키는 것을 보고, 왜 이것을 사용하는지에 대한 궁금증이 생겨 검색해 보았다.

`<input type="hidden">`는 사용자에게는 보이지 않는 **숨겨진 입력 필드**를 정의한다.
숨겨진 입력 필드는 렌더링이 끝난 웹 페이지에서는 전혀 보이지 않으며, 페이지 콘텐츠 내에서 이걸 볼 있게 만들 방법도 없다.

## 그렇다면, 이러한 숨겨진 입력 필드를 사용하는 이유는 무엇일까?

숨겨진 입력 필드는 폼 제출 시에 사용자가 변경해서는 안 되는 데이터를 함께 보낼 때 유용하게 사용된다.

예를 들면, 수정할 게시글이 데이터베이스 테이블에서 가지고 있는 Primary Key 값이 이에 해당될 수 있다. 
이 값이 입력 필드에 포함되어 있어야 사용자가 다른 수정사항을 폼에 입력하여 제출할 때 (사용자는 인지하지 못하지만) 같이 제출되는 이 PK 값을 통해 DB에서 해당 레코드를 식별하여 정보를 알맞게 수정할 수 있는 것이다.

이러한 입력 필드는 앞서 말한 것처럼 업데이트 되어야 하는 데이터베이스의 레코드를 저장하거나, 고유한 보안 토큰 등을 서버로 보낼 때 주로 사용된다고 한다.

## 예시
```html
<!DOCTYPE html>
<html lang="ko">
<head>
	<meta charset="UTF-8">
	<title>HTML input tag - type="hidden"</title>
</head>
<body>

    <form action="/examples/media/action_target.php" method="get">
        아이디 : <input type="text" name="user_id"><br>
        비밀번호 : <input type="password" name="user_pw"><br>
        <input type="hidden" id="gameToken" name="game_token" value="xm234jq">
        <input type="submit">
    </form>
    
</body>
</html>
```
[TCP School](http://tcpschool.com/html-input-types/hidden)에서 제공하고 있는 위 예제 코드의 결과는 아래와 같다.

<img src="https://images.velog.io/images/gndan4/post/535de519-1b96-4671-93fc-cc7a2d7e1b19/image.png" width="400">

아이디와 비밀번호를 받는 필드, 그리고 버튼만 렌더링 되고, 숨겨진 입력 필드는 렌더링 되지 않는 것을 확인할 수 있다.