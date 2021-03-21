배너: [godori](https://velog.io/@godori)님이 만드신 [배너 메이커](https://velog.io/@godori/banner-maker) 활용

---

## Web Framework

Django is a python web framework

### 웹 프레임워크란?

- 동적인 웹 페이지나, 웹 애플리케이션, 웹 서비스 개발 보조용으로 만들어지는 애플리케이션 프레임워크의 일종
- **웹 페이지를 개발하는 과정에서 겪는 어려움을 줄이는 것이 주 목적**으로 통상 DB 연동, 템플릿 형태의 표준, 세션 관리, 코드 재사용 등의 기능을 포함하고 있다.
- 애플리케이션 프레임워크는 소프트웨어 개발자가 응용 소프트웨어의 표준 구조를 구현하기 위해 사용하는 소프트웨어 프레임워크로 구성된다.
- 즉, 프로그래밍에서 운영체제를 위한 응용 프로그램 표준 구조를 구현하는 클래스와 라이브러리의 모임이다.

웹 프레임워크가 기본적인 구조나 필요한 코드들은 알아서 제공해주기 때문에, 사용자는 그냥 **좋은 웹 서비스를 만드는 것에 집중**할 수 있다.

---

## django

django는 파이썬으로 작성된 오픈소스 웹 애플리케이션 프레임워크로, **모델-뷰-컨트롤러 모델 패턴**을 따르고 있다.

- 모델-뷰-컨트롤러(Model-View-Controller, MVC)는 소프트웨어 공학에서 사용되는 **소프트웨어 디자인 패턴**이다.
- 이 패턴을 성공적으로 사용하면, 사용자 인터페이스로부터 비즈니스 로직을 분리하여 애플리케이션의 시각적 요소나 그 이면에서 실행되는 비즈니스 로직을 서로 영향 없이 쉽게 고칠 수 있는 애플리케이션을 만들 수 있다.
- MVC에서 모델은 애플리케이션의 정보(데이터)를 나타내며, 뷰는 텍스트, 체크박스 항목 등과 같은 사용자 인터페이스를 나타내고. 컨트롤러는 데이터와 비즈니스 로직 사이의 상호동작을 관리한다.

### django에서의 MVC 패턴

django에서는 MVC 패턴에서 M, V, C에 해당하는 요소를 각각 Model, Template, View로 지칭한다.

- MVC 패턴: Model, View, Controller
- django: Model(DB 관리), Template(레이아웃, 화면), View(중심 컨트롤러, 심장)

<img src="https://images.velog.io/images/gndan4/post/86c6a8f7-65bc-4a69-b613-abe0ac7cbd91/Untitled.png" alt="Django MTV" width="70%">

- 위 순서에 따라 url, views, template 순서로 코드를 작성한다.

**model**

- 응용 프로그램의 데이터 구조를 정의하고 데이터베이스의 기록을 관리(추가, 수정, 삭제)

**template**

- 파일의 구조나 레이아웃을 정리
- 실제 내용을 보여주는 데에 사용 (presentation)

**view**

- HTTP 요청을 수신하고 HTTP 응답을 반환
- Model을 통해 요청을 충족시키는데 필요한 데이터에 접근
- template에게 응답의 서식 설정을 맡김

### django 명령어

프로젝트 생성

- `django-admin sartproject 프로젝트이름`

서버 실행

- `python manage.py runserver`

애플리케이션 생성

- `python manage.py startapp 애플리케이션이름`

### APP 이름 작성 시 유의할 점

1. app 이름은 **'복수형'**으로 (이후에 클래스 명과 겹치지 않게 하기 위함)
2. **먼저 app을 생성**한(`python manage.py startapp 앱이름`) **이후**에 settings.py에서 app 등록

### 프로젝트 폴더 내 파일

\_\_init\_\_.py

- 프로젝트 폴더를 하나의 패키지로 인식할 수 있게 해주는 파일. (비어있는 상태로 놔둔다)

asgi.py

- django 3 버전에서 새로 생긴 파일
- 장고 어플리케이션이 비동기식 웹 서버와 연결 및 소통하는 것을 도움

settings.py

- django 웹 사이트의 모든 설정을 포함하고 있는 파일
- 애플리케이션 등록, 파일들의 위치, DB 세부사항, 보안 관련 사항 등

url.py

- 사이트의 url과 view의 연결을 지정
- 사용자의 HTTP 요청을 받았을 때 요청을 적절한 view로 포워드 해줌

wsgi.py

- Web Server Gateway Interface
- 장고 앱이 웹서버와 연결 및 소통하는 것을 도움
- 배포할 때 사용

### 애플리케이션 폴더 내 파일

\_\_init\_\_.py

- 앱 폴더를 하나의 패키지로 인식할 수 있게 해주는 파일. (비어있는 상태로 놔둔다)

admin.py

- 관리자 사이트를 커스텀하는 파일

apps.py

- 앱에 대한 정보를 담고 있는 파일 (수정하지 않는다)

models.py

- MTV에서 M을 담당하는 파일 (DB 관리)

test.py

- 테스트코드를 작성하는 파일

views.py

- MTV에서 V를 담당하는 파일 (중간 관리자)

### 프로젝트 폴더 내 settings.py 설정

- INSTALLED_APPS에서는 애플리케이션을 local app, third-party app, django app 순서로 작성한다.

**firstpjt/firstpjt/settings.py**

```python
# Application definition

INSTALLED_APPS = [
  # 1. local apps
  'articles',
  # 2. 3rd-party apps
  # 3. django apps
  'django.contrib.admin',
  'django.contrib.auth',
  'django.contrib.contenttypes',
  'django.contrib.sessions',
  'django.contrib.messages',
  'django.contrib.staticfiles',
]
```

- 마지막에 콤마가 붙어있는데, django에서는 이를 trailing comma 라고 부른다. django에서 권장하는 사항이다.

- Internalization에서 국제화 및 국지화 설정을 한다

**firstpjt/firstpjt/settings.py**

```python
# Internationalization
# https://docs.djangoproject.com/en/3.1/topics/i18n/

LANGUAGE_CODE = 'ko-kr'

TIME_ZONE = 'Asia/Seoul'

USE_I18N = True

USE_L10N = True

USE_TZ = True
```

    - LANGAGE_CODE를 'en-us'에서 'ko-kr'로 바꿔준다.
    - TIME_ZONE은 'UTC'에서 'Asia/Seoul'로 바꿔준다. (DB Time Zone)

### urls.py

- 장고 서버로 http 요청(request)이 들어오면 그 요청이 어디로 가야하는지 인식하고 관련된 함수(view)로 넘겨준다.
- `views.py`에서 만든 함수를 연결시켜 준다.

**firstpjt/firstpjt/urls.py**

```python
urlpatterns = [
  path('admin/', admin.site.urls),
]
```

- django에서는 사용자가 따로 등록하지 않아도 처음부터 admin 앱이 등록되어 있음 (기본적으로 관리자 페이지 제공)

**firstpjt/firstpjt/urls.py**

```python
from django.contrib import admin
from django.urls import path
from articles import views

urlpatterns = [
  path('admin/', admin.site.urls),
  path('index/', views.index),
]
```

- 위의 `urls.py`에서 클라이언트의 요청에 따라 적절한 view로 연결시켜줌
- `from 앱이름 import views.py` 를 해줘야 적절한 앱의 적절한 view 함수를 연결해줄 수 있다.

- 참고로, 웹 브라우저에서 url을 입력할 때 혹은 서버에서 링크를 작성할 때 항상 'index/'와 같이 슬래쉬(/)까지 붙여줘야 한다.
  - 만약 '/'를 붙이지 않은 경우에는 장고가 이를 장고가 알아채서 클라이언트에게 301 HTTP response (Permanently Moved)를 보내고 'index' 뒤에 슬래쉬를 붙인 주소로 자동으로 리다이렉트하고 그에 대한 HTTP response를 다시 클라이언트에게 보내준다 (HTTP response 순서: 301 → 200, 구글 개발자 도구 network탭에서 확인 가능). 이는 장고 세팅에서 기본으로 `APPEND_SLASH = True`로 설정되어 있기 때문이다.
  - 반대로, urls.py의 `path()`함수에서 'index'와 같이 뒤에 슬래쉬를 안 붙이면 브라우저에서 'index'와 같이 끝에 슬래쉬를 붙이지 않고 접근한다고 해도 페이지를 받아올 수 없다. 이는 장고가 요청된 주소의 끝에 '/'가 없음을 감지하고 자동으로 '/'를 붙여서 리다이렉트 하기 때문이다.(HTTP response 순서: 301 → 404)

### views.py 작성

- 각 애플리케이션 내에 views.py 파일이 존재한다. 이 안에 요청에 따라 실행할 함수들을 작성한다.
- HTTP 요청을 수신하고 HTTP 응답을 반환하는 함수 작성
- Model을 통해 요청에 맞는 필요 데이터에 접근
- template에게 HTTP 응답 서식을 맡김
- 사용자가 만드는 view 함수의 첫 번째 인자는 반드시 request
- 템플릿을 띄워주기 위해 django.shortcuts 모듈의 render 함수를 사용하는데, 이 함수의 첫 번째 인자 또한 request
  - `return render(request, '템플릿 경로')` 형식으로 작성해서 템플릿을 띄워준다
  - 이때 템플릿 경로는 반드시 전체 프로젝트 내부의 프로젝트 폴더 혹은 앱 폴더 바로 안에 있는 templates 폴더 내에 존재하는 파일이어야 한다
    - 예: 'firstpjt/firstpjt/templates/base.html', 'firstpjt/articles/templates/index.html'

---

## Django Template

- 데이터 표현을 제어하는 도구이자 표현에 관련된 로직

### Django Template Language (DTL)

- django template에서 사용하는 built-in template system
- 조건, 반복, 변수 치환, 필터 등의 기능을 제공
- 단순히 Python이 HTML에 포함된 것이 아니며, 프로그래밍적 로직이 아니라 **프레젠테이션**을 표현하기 위한 것
- 파이썬처럼 일부 프로그래밍 구조(if, for 등)를 사용할 수 있지만, 이것은 해당 **Python 코드로 실행되는 것이 아님**

### DTL Syntax - Variable

- `{{ variable }}`
- `render()`를 사용하여 views.py에서 정의한 변수를 template 파일로 넘겨 사용하는 것
- 변수명은 영어, 숫자와 밑줄(\_)의 조합으로 구성될 수 있으나, 밑줄로는 시작할 수 없음
  - 공백이나 구두점 문자 또한 사용할 수 없음
- `dot(.)`를 사용하여 변수 속성에 접근할 수 있음 (`article.title`)
- `render()`의 세 번째 인자로 `{'key': value}`와 같이 딕셔너리 형태로 넘겨주며, 여기서 정의한 key에 해당하는 문자열이 template에서 사용 가능한 변수명이 됨

**firstpjt/articles/views.py**

```python
from django.shortcuts import render

def greeting(request):
    foods = ['apple', 'banana', 'coconut', ]
    info = {
       'name': 'Harry'
    }
    context = {
        'info': info,
        'foods': foods,
    }
    return render(request, 'greeting.html', context)
```

**firstpjt/articles/templates/index.html**

```django
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <h1>안녕하세요 저는 {{ info.name }}입니다.</h1>
    <p>제가 가장 좋아하는 음식은 {{ foods }}입니다.</p>
    <p>{{ foods.0 }}를 가장 좋아합니다.</p>
  </body>
</html>
```

**보여지는 화면**

<img src="https://images.velog.io/images/gndan4/post/5310ecb3-a5a9-4f79-9be5-3cd738ef7067/Untitled.png" alt="DTL Variable" width="40%">

### DTL Syntax - Filters

- `{{ variable|filter }}`
- 표시할 변수를 수정할 때 사용
- 파이프(`|`)를 사용하여 적용
- 예시
  - `{{ name|lower }}`
  - name 변수를 모두 소문자로 출력
- 60개의 built-in template filters를 제공
- chaining이 가능하며 일부 필터는 인자를 받기도 함

  - `{{ variable|truncatewords:30 }}`
  - variable 변수가 가지고 있는 문자열에서 앞의 30자까지만 출력

**firstpjt/articles/views.py**

```python
def dinner(request):
  foods = ['족발', '피자', '햄버거', '초밥',]
  pick = random.choice(foods)
  context = {
    'pick': pick,
    'foods': foods,
  }
  return render(request, 'dinner.html', context)

```

**firstpjt/articles/templates/dinner.html**

```django
<h1>오늘 저녁은 {{ pick }}!!</h1>
<p>{{ pick }}은 {{ pick|length }}</p>
```

화면

  <img src="https://images.velog.io/images/gndan4/post/182f9e06-f242-43f7-b701-2af3d6f74f35/Untitled.png" alt="DTL Filters" width="40%">

### DTL Syntax - Tags

- `{{ tag }}`
- 출력 텍스트를 만들거나, 반복 또는 논리를 수행하여 제어 흐름을 만드는 등 변수보다 복잡한 일들을 수행
- 일부 태그는 시작과 종료 태그가 필요
  - `{% tag %} ... {% endtag %}`
- 약 24개의 built-in template tags를 제공

**firstpjt/articles/views.py** - 동일

**firstpjt/articles/templates/dinner.html**

```django
<body>
  <h1>오늘 저녁은 {{ pick }}!!</h1>
  <p>{{ pick }}은 {{ pick|length }}</p>
  <p>메뉴판</p>
  <ul>
    {% for food in foods %}
    <li>{{ food }}</li>
    {% endfor %}
  </ul>
</body>
```

**화면**

  <img src="https://images.velog.io/images/gndan4/post/f7b835a8-546e-410f-9873-4430d918587a/Untitled.png" alt="DTL Tags" width="40%">

### DTL Syntax - Comments

- `{# lorem ipsum #}`
- django template에서 줄의 주석을 표현하기 위해 사용
- 아래처럼 유효하지 않은 템플릿 코드가 포함될 수 있음
  - `{# {% if ... %}text{% else %} #}`
- 한 줄 주석에만 사용할 수 있음 (줄 바꿈이 허용되지 않음)
- 여러 줄 주석은 `{% comment %}`와 `{% endcomment %}` 사이에 입력

### Template Inheritance

- 템플릿 상속은 기본적으로 코드의 재사용성에 초점을 맞춤
- 템플릿 상속을 사용하면 사이트의 모든 공통 요소를 포함하고, 하위 템플릿이 override할 수 있는 블록을 정의하는 기본 'skeleton' 템플릿을 만들 수 있음

- 주로 자주 사용되는 기본적인 공통 템플릿의 경우 전체 프로젝트 내의 프로젝트명 폴더 안의 templates 폴더에 base.html을 만들고 이 템플릿을 다른 템플릿들에서 상속하여 재사용한다. (`'project/project/templates/base.html'`)
  - 참고로, 장고는 INSTALLED_APP에 등록된 앱 폴더의 templates 폴더 내의 경로들을 알고 있다.
  - 하지만 전체 프로젝트 내부의 프로젝트명 폴더 안의 templates 폴더는 인식하지 못한다.
  - 따라서 settings.py에서 TEMPLATES의 DIRS 안에 이 경로를 추가해 줘야 한다.

**firstpjt/firstpjt/settings.py**

```python
TEMPLATES = [
  {
    'BACKEND': 'django.template.backends.django.DjangoTemplates',
    'DIRS': [BASE_DIR / 'firstpjt' / 'templates', ],
    'APP_DIRS': True,
    'OPTIONS': {
      'context_processors': [
        'django.template.context_processors.debug',
        'django.template.context_processors.request',
        'django.contrib.auth.context_processors.auth',
        'django.contrib.messages.context_processors.messages',
      ],
    },
  },
]
```

- 위 코드에서 `BASE_DIR / 'firstpjt' / 'templates'`와 같이 경로를 표현하는 이유는 OS에 상관 없이 경로가 호환되도록 하기 위함이다. (각 OS에 맞게 경로를 하드코딩 했을 때의 문제를 피할 수 있음) (python 'pathlib' 라이브러리 참고)
- BASE_DIR 같은 경우 프로젝트 생성시 settings.py에 자동으로 아래와 같이 설정되어 있다. 이 BASE_DIR은 현재 프로젝트의 루트 디렉토리를 가리킨다.

**firstpjt/firstpjt/settings.py**

```python
from pathlib import Path

# Build paths inside the project like this: BASE_DIR / 'subdir'.
BASE_DIR = Path(__file__).resolve().parent.parent
```

**`extends` tag**

- `{% extends %}`
- 자식(하위) 템플릿이 부모 템플릿을 확장한다는 것을 알림
- 반드시 **템플릿 최상단**에 작성되어야 함 (즉, 2개 이상 사용할 수 없음)

**`block` tag**

- `{% block %}`

- 하위 템플릿에서 override할 수 있는 블록을 정의
- 즉, 하위 템플릿이 채울 수 있는 공간
- 가독성을 높이기 위해 선택적으로 `{% endblock %} 태그에 이름 지정

```django
{% block content %} {% endblock content %}
```

**템플릿 상속 예시**

**firstpjt/firstpjt/templates/base.html**

```django
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta2/dist/css/bootstrap.min.css"
      rel="stylesheet"
      integrity="sha384-BmbxuPwQa2lc/FVzBcNJ7UAyJxM6wuqIj61tLrc4wSX0szH/Ev+nYRRuWlolflfl"
      crossorigin="anonymous"
    />
    <title>Document</title>
  </head>
  <body>
    <nav class="navbar navbar-light bg-light">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">Navbar</a>
      </div>
    </nav>
    <div class="container">{% block content %} {% endblock %}</div>
    <script
      src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta2/dist/js/bootstrap.bundle.min.js"
      integrity="sha384-b5kHyXgcpbZJO/tY9Ul7kGkf1S0CWuKcCD38l8YkeH8z8QjE0GmW1gYU5S9FOnJ0"
      crossorigin="anonymous"
    ></script>
  </body>
</html>
```

**firstpjt/articles/templates/index.html**

```django
{% extends 'base.html' %} {% block content %}
<h1>만나서 반가워요!!!</h1>
<a href="{% url 'greeting' %}">greeting</a>
<a href="{% url 'dinner' %}">dinner</a>
<a href="{% url 'throw' %}">throw</a>
{% endblock %}
```

- 부모 템플릿을 상속받은 index.html 자식 템플릿의 경우 중복되지 않는 부분만 간단하게 추가함으로써필요한 화면을 구현할 수 있다.

### Django Template System (django 설계 철학)

1. "표현과 로직(view)을 분리"
   - 템플릿 시스템은 표현을 제어하는 도구이자 표현에 관련된 로직일 뿐이다
   - 즉, 템플릿 시스템은 이러한 기본 목표를 넘어서는 기능을 지원하지 말아야 한다.
2. "중복을 배제"
   - 대다수의 동적 웹사이트는 공통 header footer navbar 같은 사이트 공통 디자인을 갖는다.
   - Django 템플릿 시스템은 이러한 요소를 한 곳에 저장하기 쉽게 하여 중복 코드를 없애야 한다.
   - 이것이 템플릿 상속의 기초가 되는 철학이다.

참고: [https://developpaper.com/djangos-design-philosophy-and-philosophy/](https://developpaper.com/djangos-design-philosophy-and-philosophy/)

---

## HTML form

### HTML form element

- 웹에서 사용되는 정보를 입력하는 여러 방식(text, button, checkbox, file, hidden, image, password, radio, reset, submit)을 제공하고, 사용자로부터 할당된 데이터를 서버로 전송하는 역할을 담당
- 핵심 속성
  - action: 입력 데이터가 전송될 URL 지정
  - method: 입력 데이터 전달 방식 지정

### HTML input element

- 사용자로부터 데이터를 입력받기 위해 사용
- type 속성에 따라 동작 방식이 달라짐
- 핵심 속성
  - name
  - 중복 가능, 양식을 제출했을 때 name이라는 이름에 설정된 값을 넘겨서 값을 가져올 수 있음
  - 주요 용도는 GET/POST 방식으로 서버에 전달하는 파라미터(name은 key, value는 value)로 `?key=value&key=value` 형태로 전달

### HTTP

- HyperText Transfer Protocol
- HTML 문서와 같은 리소스들을 가져올 수 있도록 해주는 포로토콜(규칙, 규약)
- 웹에서 이루어지는 모든 데이터 교환의 기초
- 주어진 리소스가 수행할 원하는 작업을 나타내는 request methods를 정의
- HTTP request method 종류
  - GET, POST, PUT, DELETE 등

### HTTP request method - GET

- 서버로부터 정보를 조회하는 데 사용
- 데이터를 가져올 때만 사용해야 함
- 데이터를 서버로 전송할 때 body가 아닌 Query String Parameters를 통해 전송
- 우리는 서버에 요청을 하면 HTML 문서 파일 한 장을 받는데, 이때 사용하는 요청의 방식이 GET

### `HttpRequest` object

- `views.py` 내에 정의한 뷰 함수에 전달되는, HTTP 요청 간의 모든 정보를 담고있는 변수
- 페이지가 요청되면 Django는 요청에 대한 메타 데이터를 포함하는 `HttpRequest` 객체를 만든다.
- 그런 다음 Django는 적절한 view 함수를 로드하고 `HttpRequest` 객체를 뷰 함수의 첫 번째 인자로 전달한다.
- 그리고 각 view는 `HttpResponse` 객체를 반환한다.

https://docs.djangoproject.com/en/3.1/ref/request-response/#module-django.http

---

## URL

### Django URLs

- Dispatcher(발송자, 운항 관리자)로서의 URL
- 웹 애플리케이션은 URL을 통한 클라이언트의 요청에서부터 시작됨 (따라서 이 요청을 받을 urls.py부터 작성)

### App URL mapping

- app의 view 함수가 많아지면서 사용하는 `path()` 또한 많아지고, app 또한 더 작성되기 때문에 프로젝트의 urls.py에서 모두 관리하는 것은 코드 유지보수에 좋지 않음.
- 이제는 각 app에 urls.py를 작성하게 됨
- 하나의 프로젝트에 여러 앱이 존재한다면, 각각의 앱 안에 `urls.py`를 만들고 프로젝트 `urls.py`에서 각 앱의 `urls.py` 파일로 URL 매핑을 위탁하게 할 수 있다.

<img src="https://images.velog.io/images/gndan4/post/ab3a7cbd-c240-4d87-b8ae-2a5915e678bc/Untitled.png" alt="App URL Mapping" width="70%">

**firstpjt/articles/urls.py**

```python
from django.urls import path
# 명시적 상대경로 표현
from . import views


urlpatterns = [
    path('index/', views.index),
    path('greeting/', views.greeting),
    path('dinner/', views.dinner),
    path('throw/', views.throw),
    path('catch/', views.catch),
]
```

- 주의: `urlpatterns` 리스트가 없는 경우 에러가 발생한다.

**firstpjt/firstpjt/urls.py**

```python
from django.contrib import admin
from django.urls import path, include


urlpatterns = [
    path('admin/', admin.site.urls),
    path('articles/', include('articles.urls')),
    path('pages/', include('pages.urls')),
]
```

- 프로젝트 폴더의 urls.py에서는 `include()` 함수 활용하여 `path()` 함수의 첫 번째 인자와 매칭된 이후의 부분은 연결된 앱의 urls.py로 넘겨줘서 처리하게 함

**`include()`**

- 다른 URLconf(`urls.py`)들을 참조할 수 있도록 도움
- 함수 `include()`를 만나게 되면, URL의 그 지점까지 일치하는 부분을 잘라내고, 남은 문자열 부분을 후속 처리를 위해 include된 URLconf로 전달한다.

### Variable Routing

- 주소 자체를 변수처럼 사용해서 동적으로 주소를 만드는 것
- form tag과 input tag를 사용하지 않고도 클라이언트로부터 필요한 간단한 정보를 받을 수 있고 그것이 `views.py` 내에서 인자로 들어오기 때문에 활용하기 좋다.
- 예: `'hello/<str:name>/'`
  - int는 생략할 수 없지만, string은 기본 값으로 생략할 수 있다
  - 예: `'hello/<name>/'`
- Vriable Routing 활용 예시

**firstpjt/firstpjt/urls.py**

```python
from django.urls import path
# 명시적 상대경로 표현
from . import views

urlpatterns = [
    ...
    path('hello/<str:name>/', views.hello),
    # path('hello/<name>/', views.hello),
]
```

**firstpjt/articles/views.py**

```python
def hello(request, name): # url 주소에 포함되어 있던 name이 인자로 들어옴
    context = {
        'name': name,
    }
    return render(request, 'hello.html', context)
```

**hello.tml**

```django
{% extends 'base.html' %} {% block content %}
<h1>만나서 반가워요 {{ name }}님!</h1>
{% endblock %}
```

### Naming URL patterns

- Django는 URL에 이름을 지정하는 방법을 제공함으로써 뷰 함수와 템플릿에서 특정 주소를 쉽게 참조할 수 있도록 돕는다.
- 이제는 링크에 url을 직접 작성하는 것이 아니라 `path()` 함수의 name 인자를 정의해서 사용
- Django Template Tag 중 하나인 url 태그를 사용해서 `path()` 함수에 작성한 name을 사용할 수 있음
- url 설정에 정의된 특정한 경로들의 의존성을 제거할 수 있음
  - 앱 내 `views.py` 파일: `path('index/', views.index)` → `path('index/', views.index, name='index'),`
  - templates 내 html 파일: `<a href="/index/">메인 페이지</a>` → `<a href="{% url 'index' %}">메인 페이지</a>`

**`{% url '' %}`**

- 주어진 URL 패턴 이름 및 선택적 매개 변수와 일치하는 절대 경로 주소를 반환
- 템플릿에 URL을 하드 코딩하지 않고도 DRY(Don't Repeat Yourself) 원칙을 위반하지 않고 링크를 출력하는 방법

---

## Namespace

> 개체를 구분할 수 있는 범위를 나타내는 namespace

### 두 번째 앱의 index 페이지 작성

```python
# pages/urls.py

from django.urls import path
from . import views


urlpatterns = [
    path('index/', views.index, name='index'),
]
```

```python
# pages/views.py

def index(request):
    return render(request, 'index.html')
```

```django
<!-- pages/templates/index.html -->

{% extends 'base.html' %} {% block content %}
<h1>두번째 앱의 index</h1>
{% endblock %}
```

```django
<!-- articles/templates/index.html -->

{% extends 'base.html' %} {% block content %}
<h1>만나서 반가워요!</h1>
<a href="{% url 'greeting' %}">greeting</a>
<a href="{% url 'dinner' %}">dinner</a>
<a href="{% url 'dtl_practice' %}">dtl-practice</a>
<a href="{% url 'throw' %}">throw</a>

<h2><a href="{% url 'index' %}">두번째 앱 index로 이동</a></h2>
{% endblock %}
```

**2가지 문제**

1. articles app index 페이지에서 '두 번째 앱 index로 이동' 하이퍼 링크를 클릭 시 두 번째 앱의 index가 아니라, 현재 페이지로 다시 이동 됨
   - URL namespace
2. pages app index url로 이동해도 articles app의 index 페이지 출력
   - Template namespace

### URL namespace

**`urls.py` 파일 안에 `app_name` attribute 작성**

```python
# pages/urls.py

app_name = 'pages'
urlpatterns = [
    path('index/', views.index, name='index'),
]
```

```python
# articles/urls.py

app_name = 'articles'
urlpatterns = [
    ...,
]
```

**`app_name` attribute**

- URL namespace를 사용하면 서로 다른 앱에서 동일한 URL 이름을 사용하는 경우에도 이름이 지정된 URL을 고유하게 사용할 수 있음
- `urls.py`에 `app_name` attribute 값 작성

**url 참조**

- `:` 연산자를 사용하여 지정
- 예를 들어, `app_name`이 `articles`고 URL name이 `index`인 주소 참조는 `articles:index`

**URL tag 변경**

```django
<!-- articles/templates/index.html -->

{% extends 'base.html' %}

{% block content %}
  <h1>만나서 반가워요!</h1>
  <a href="{% url 'articles:greeting' %}">greeting</a>
  <a href="{% url 'articles:dinner' %}">dinner</a>
  <a href="{% url 'articles:throw' %}">throw</a>

  <h2><a href="{% url 'pages:index' %}">두번째 앱 index로 이동</a></h2>
{% endblock %}

```

### Template namespace

- Django는 기본적으로 `app_name/templates/` 경로에 있는 templates 파일들만 찾을 수 있으며, `settings.py` 안의 `INSTALLED_APPS` 리스트에 작성한 app 순서로 template을 검색 후 렌더링한다.
- 임의로 templates의 폴더 구조를 `app_name/templates/app_name` 형태로 변경해 임의로 이름 공간 생성 후 변경된 추가 경로 작성

```python
# articles/views.py

return render(request, 'articles/index.html')
```

```python
# pages/views.py

return render(request, 'pages/index.html')
```
