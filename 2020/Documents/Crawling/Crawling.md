# 데이터 크롤링 관련 내용 정리

## `requests` 모듈

- 원하는 주소로부터 정보를 받아올 수 있게 해주는 모듈이다.

### 설치

`pip install requests`

### 사용 예시

```python
import requests
URL = '정보를 가져올 페이지 주소'
res = requests.get(URL)
```

- `requests.get(URL)`이 리턴하는 객체의 `text` 속성, `get_json()` 등으로 필요한 형식에 맞게 정보를 가져올 수 있다.

<br><br>

## `BeautifulSoup` 모듈

이 모듈은 `requests` 모듈을 통해 가져온 페이지 정보에서 특정 기준으로 원하는 정보를 추출하는 데에 유용하다.

### 설치

`pip install BeautifulSoup4`

### 사용 예시

```python
import requests
from bs4 import BeautiuSoup

URL = '정보를 가져올 페이지 주소'
res = requests.get(URL)

soup = BeautifulSoup(res.text, 'html.parser')
items = soup.select('CSS 선택자').text
```

위 코드를 실행하면, BeauitfulSoup의 `select` 메소드를 통해 해당 페이지에서, 입력한 CSS 선택자가 적용된 모든 부분을 items에 리스트 형태로 할당하게 된다.
