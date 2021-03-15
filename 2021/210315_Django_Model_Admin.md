## Django Model

### Model

- 단일한 데이터에 대한 정보를 가짐
    - 사용자가 저장하는 데이터들의 필수적인 필드들과 동작들을 포함
- django는 Model을 통해 데이터에 접속하고 관리
- 일반적으로 각각의 model은 하나의 데이터베이스 테이블에 매핑

### Database

- 데이터베이스(DB)
    - 체계화된 데이터의 모임
- 쿼리(Query)
    - 데이터를 조회하기 위한 명령어
    - 조건에 맞는 데이터를 추출하거나 조작하는 명령어

### Database의 기본 구조

- 스키마(Schema)
    - 데이터베이스에서 자료의 구조, 표현방법, 관계 등을 정의한 구조
    - 데이터베이스의 구조와 제약 조건(자료의 구조, 표현 방법, 관계)에 관련한 전반적인 명세를 기술한 것
- 테이블(Table)
    - 열(컬럼/필드)와 행(레코드/값)의 모델을 사용해 조직된 데이터 요소들의 집합.
    - SQL 데이터베이스에서는 테이블을 '관계'라고도 한다.
    - 필드(field) / 컬럼(column) / 속성
    - 레코드 / 행(row) / 튜플
- 열(Column), 커럼
    - 각 열에는 고유한 데이터 형식이 지정된다. (INTEGER, TEXT, NULL 등)
- 행(row), 레코드
    - 테이블의 데이터는 행에 저장된다.
    - 즉, user 테이블에는 행의 개수만큼의 고객정보가 저장되어 있다.
- PK(기본 키)
    - 각 행(레코드)의 고유값으로 Primary Key로 불린다.
    - 반드시 설정하여야 하며. 데이터베이스 관리 및 관계 설정 시 주요하게 활용된다.
- Model > Database
    - Model은 DB보다 큰 개념으로, 웹 애플리케이션의 데이터를 구조화하고 조작하기 위한 도구이다.

---

## ORM

### ORM이란?

"Object-Relational-Mapping"은 객체 지향 프로그래밍 언어를 사용하여 호환되지 않는 유형의 시스템 간에(Django - SQL) 데이터를 변환하는 프로그래밍 기술이다. 이것은 프로그래밍 언어에서 사용할 수 있는 '가상 객체 데이터베이스'를 만들어 사용한다.

<img src="https://images.velog.io/images/gndan4/post/478d201d-188c-4633-8009-5419868f0613/image.png" alt="ORM" width="70%">

### ORM의 장단점

- 장점
    - SQL을 잘 알지 못해도 DB 조작 가능
    - SQL의 절차적 접근이 아닌 객체 지향적 접근으로 인한 높은 생산성
- 단점
    - ORM만으로 완전한 서비스를 구현하기 어려운 경우가 있음
- 현대 웹 프레임워크의 요점은 웹 개발으

> 우리는 DB를 객체(object)로 조작하기 위해 ORM을 사용한다.

### models.py 작성

- models.py는 앱 폴더 내에 생성한다.

```python
from django.db import models

class Article(models.Model):  # 장고에서 미리 정의한 Model을 상속받는다.
    # ORM을 이용해서 id, title, content 컬럼을 가진 DB 모델을 생성해보자.
    # id 컬럼은 자동으로 생성된다.
    # CharField - 길이의 제한이 있는 varchar형 필드. (man_length가 필수 인자임)
    title = models.CharField(max_length=10)
    # TextField - 길이의 제한이 없는 text형 필드.
    content = models.TextField()
    # DateTimeFIeld - DateTime 기록 필드.
    created_at = models.DateTimeField(
        auto_now_add=True)  # auto_now_add - 첫 저장 시 자동 기록
    updated_at = models.DateTimeField(
        auto_now=True)  # auto_now - 저장될 때마다 자동 기록
```

- 하나하나의 클래스 변수는 DB에서의 컬럼과 일치

---

## Migrations

- "django가 model에 생긴 변화(필드 추가, 모델 삭제 등)를 반영하는 방법"
- Migration(마이그레이션) 실행 및 DB 스키마를 다루기 위한 명령어
    - `makemigrations`
    - `migrate`
    - `sqlmigrate`
    - `showmigrations`

### Migrations Commands

- `makemigrations`
    - model을 변경한 것에 기반한 새로운 마이그레이션(like 설계도)을 만들 때 사용
    - `python manage.py makemigrations`
- `migrate`
    - 마이그레이션을 DB에 반영하기 위해 사용
    - 설계도를 실제 DB에 반영하는 과정
    - `python manage.py migrate`
    - 모델에서의 변경 사항들과 DB의 스키마가 동기화를 이룸
    - 클래스를 만들고 처음 반영 시 '앱이름_클래스이름'(lower_case)으로 테이블이 생성된다
- `sqlmigraate`
    - 마이그레이션에 대한 SQL 구문을 보기 위해 사용
    - `python manage.py sqlmigrate 앱이름 마이그레이션번호`
        - 예: `python manage.py sqlmigrate articles 0001`
    - 마이그레이션이 SQL 문으로 어떻게 해석되어서 동작할 지 미리 확인할 수 있음
- `showmigrations`
    - 프로젝트 전체의 마이그레이션 상태를 확인하기 위해 사용
    - `python manage.py showmigrations`
    - migrate 되었는지 안 되었는지 여부를 확인할 수 있음

### Migration의 3단계

1. models.py
    - model **변경사항 발생**
2. `python manage.py makemigrations`
    - migrations **파일 생성** (설계도)
3. `python manage.py migrate`
    - DB에 **적용**

SQLite extension 설치 - django 폴더 내 db.sqlite3 파일을 우클릭하면 open database 선택지가 생성됨 - 왼쪽 EXPLOLER에 SQLITE EXPLOLER 탭이 생겨서 그 안에서 DB 테이블 조회 가능!

---

## Database API

### DB API

- "DB를 조작하기 위한 도구"
- django가 기본적으로 ORM을 제공함에 따른 것으로 DB를 편하게 조작할 수 있도록 도와줌
- Model을 만들면 django는 객체들을 만들고 읽고 수정하고 지울 수 있는 database-abstract API를 자동으로 만듦
- database-abstract API 혹은 database-access API라고도 함

### DB API 구문 - Making Queries

<img src="https://images.velog.io/images/gndan4/post/855e653a-d00e-412d-9df8-fdd1dec6d39f/image.png" alt="DB API" width="70%">

### DB API

- **Manager (Model.objects)**
    - django 모델에 데이터베이스 query 작업이 제공되는 인터페이스
    - 기본적으로 모든 django 모델 클래스에 objects라는 Manager를 추가
    - objects는 장고 모델과 DB 사이에서의 소통을 돕는 매니저 역할을 한다.
- **Queryset**
    - 데이터베이스로부터 전달받은 객체 목록
    - queryset 안의 객체는 0개, 1개, 혹은 여러 개일 수 있음
    - 데이터베이스로부터 조회, 필터, 정렬 등을 수행할 수 있음
    - 데이터베이스 조작을 위한 다양한 QuerySet API method들은 [공식문서](https://docs.djangoproject.com/en/3.1/ref/models/querysets/) 참고:

### DB API 실습을 위한 환경설정

장고 내장 기본 셸은 `python manage.py shell`

쿼리 조작을 실습하기 위해서 django third-party 라이브러리 설치 - 셸을 실행할 때  DB API 조작을 위해 필요한 것들을 자동으로 import 해줘서 편리함

django-extensions 설치

`pip install ipython` - > cf) 파이썬 셸 업그레이드

`pip install django-extensions` → 장고 third-party shell extension

settings.py 안의 INSTALLED_APPS 에 추가

```python
INSTALLED_APPS = (
    ...
    'django_extensions',
)
```

`python manage.py shell_plus`로 설치된 extension 실행

---

## CRUD

### CRUD

- 대부분의 컴퓨터 소프트웨어가 가지는 기본적인 데이터 처리 기능들을 묶어서 이르는 말
    - Creae(생성)
    - Read(읽기)
    - Update(갱신)
    - Delete(삭제)

아래에서 살펴볼 CRUD 코드들은 

`python manage.py shell_plus` 를 통해 실행된 django third-party shell 환경 내에서 실행된 것들이다. 

### Create

```bash
# 1. 빈 게시물 인스턴스 생성
a = Ariticle() # 게시물 인스턴스 생성

a.title = 'title1' # 게시물 title 필드 값 입력

a.content = 'content1' # 게시물 content 값 입력

a.save() # 게시물을 DB에 저장

a
# <Article: Article object (None)>
# save를 하기 전에는 아직 DB에 저장된 상태가 아니며, pk값이 주어지지 않아 None으로 나타난다.

# 2. 생성자를 이용해 필드에 값이 있는 게시물 인스턴스 생성
# django에서 제공하는 Model 클래스에 정의되어 있는 생성자를 이용해 인스턴스 생성하는 방법
b = Article(title='second', content'django!!')
b
# <Article: Article object (None)>
b.save()
b
# <Article: Article object (2)>

# 3. create 이용해서 인스턴스 생성 후 바로 저장
# 클래스.objects.create() -> 인스턴스를 생성하지 않고 저장하는 방법
Article.objects.create(title='third', content='django!!!')
# <Article: Article object (3)>
```

### Read

- QuerySet API method를 사용한 다양한 조회를 하는 것이 중요
- 크게 2가지로 분류
    1. Methods that return new querysets
    2. Methods that do not return querysets

```bash
# 1. all - 모든 데이터 조회
Article.objects.all()
# <QuerySet [<Article: Article object (1)>, <Article: Article object (2)>, <Article: Article object (3)>]>

# 2. first - 가장 첫번째 데이터 조회
a = Article.objects.first() # articles_article 테이블의 첫 번째 레코드 read
a.title
# 'title1'
a.content
# 'content1'
a
# <Article: Article object (1)>
a.pk
# 1
a.id
# 1

# 3. get - unique한 값(pk)을 통해 조회할 떄 사용
b = Article.objects.get(pk=2)
b
# <Article: Article object (2)>

# 해당하는 객체가 없을 경우 에러 발생
# DoesNotExist: Article matching query does not exist.

# 해당하는 객체가 여러 개일 경우 에러 발생
# ultipleObjectsReturned: get() returned more than one Article -- it returned 2!

# 4. filter - 지정된 매개변수와 일치하는 객체를 모두 포함하는 'QuerySet' 반환
# (해당하는 레코드가 단 하나일 경우에도 QuerySet 형태로 반환됨에 주의!)

# 1번 레코드와 같은 content 값을 가지는 새로운 레코드 저장
# DB에 저장과 동시에, 생성된 인스턴스를 반환한다.
Article.objects.create(title='title4', content='django!')
# <Article: Article object (4)>
Article.objects.filter(content='django!')
# <QuerySet [<Article: Article object (1)>, <Article: Article object (4)>]>
```

### Field Lookups

- 조회 시 특정 조건을 적용시키기 위해 사용
- QuerySet Method(get, filter, exclude)에 대한 키워드 인자로 사용됨
- 참고: [https://docs.djangoproject.com/en/3.1/topics/db/queries/#field-lookups](https://docs.djangoproject.com/en/3.1/topics/db/queries/#field-lookups)

```bash
# content 필드에 '!'를 포함하는 레코드 조회
Article.objects.filter(content__contains='!')
# <QuerySet [<Article: Article object (1)>, <Article: Article object (2)>, <Article: Article object (3)>, <Article: Article object (4)>]>
```

`

### Update

```python
article = Article.objects.get(pk=1)
article
# <Article: Article object (1)>

article.title
# 'first'
article.title = 'byebye'
article.title
# 'byebye'
a.save() # Update (반드시 save해야 함. 그래야만 DB에 수정사항이 반영됨)
```

### Delete

```bash
article = Article.objects.get(pk=1)
article.delete() # 삭제
# (1, {'articles.Article': 1})

article
# <Article: Article object (None)> pk가 사라져 None으로 표시되는 것을 확인할 수 있다.

Article.objects.get(pk=1) # 실제 DB에서 pk가 1인 레코드가 사라져 오류가 남
# DoesNotExist: Article matching query does not exist.

# 이후 새로운 레코드를 저장하면?
Article.objects.create(title='test', content='test!!!')
# <Article: Article object (5)>
# 삭제된 pk값(1)을 재사용 하지 않는다. pk값 5로 저장됨
```

---

## Admin Site

### Automatic admin interface

- 사용자가 아닌 서버의 관리자가 활용하기 위한 페이지
- Article class를 admin.py에 등록하고 관리
- django.contrib.auth 모듈에서 제공
- record 생성 여부 확인에 매우 유용하며 직접 record를 삽입할 수도 있음

articles 앱 폴더 내의 [admin.py](http://admin.py) 파일에 다음과 같이 작성한다.

```bash
from django.contrib import admin
from .models import Article

# 'admin, site에, 등록한다' 로 외우자.
admin.site.register(Article)
```

콘솔에서 `python manage.py createsuperuser` 를 통해 admin 계정을 하나 생성한다.

만든 계정이 들어갈 테이블은 어디에?? - 프로젝트에서 처음 migrate 할 때 auth_user 테이블이 생성됨. (settings.py에서 INSTALLED_APP에 기본적으로 'django.contrib.auth' 앱이  등록되어 있기 때문에 가능)

굉장히 편리하게도, 장고는 기본적으로 관리자 페이지 기능을 제공한다.

이에 필요한 'django.contrib.admin' 도 프로젝트 생성 시 자동으로 INSTALLED_APP에 등록되어 있다.

서버를 실행하고 'adimn/' url로 접속하면 다음과 같은 관리자 페이지가 나타난다.

<img src="https://images.velog.io/images/gndan4/post/e0e9e0c9-5de2-4922-be01-0bc04698c61f/image.png" alt="Admin Login" width="70%">

- 이곳에 방금 전 생성한 계정으로 로그인 하면 아래와 같은 화면이 나타난다.

<img src="https://images.velog.io/images/gndan4/post/278602ba-a371-4154-826b-47cd4701ef12/image.png" alt="Admin Index" >

- admin.py에 등록한 Article이 있는 것을 확인할 수 있다.

<img src="https://images.velog.io/images/gndan4/post/62c59c0f-cd67-4ea0-9dba-8c92f15ac700/image.png" alt="Admin Articles" width="70%">

- 이곳에서 실제 DB에 있는 데이터를 간단하게 조작할 수 있다 (CRUD)
- 아래와 같이 admin.py를 수정함으로써 관리자 페이지를 커스터마이징 할 수 있다.

```python
from django.contrib import admin
from .models import Article

class ArticleAdmin(admin.ModelAdmin):
    list_display = ('pk', 'title', 'content', 'created_at', 'updated_at',)

# 'admin, site에, 등록한다' 로 외우자.
admin.site.register(Article, ArticleAdmin)
```

<img src="https://images.velog.io/images/gndan4/post/d9cba2f0-2322-403d-ac21-8bb343f5bfc6/image.png" alt="Admin Customized" width="70%">

- 관리자 페이지에서 Article 모델의 레코드 정보를 다르게 표현하고 있는 것을 확인할 수 있다.

---

## Model-Template-View 연동해보기

현재까지 배운 Template, View, Model의 개념을 연계하여 활용해보자.

### URL

```python
from django.urls import path
from . import views

app_name = 'articles'
urlpatterns = [
    path('index/', views.index, name='index'),
]
```

### Model

```python
from django.db import models

# Create your models here.

class Article(models.Model):
    title = models.CharField(max_length=10)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
```

### View

```python
from django.shortcuts import render
from .models import Article

# Create your views here.

def index(request):
    # 모든 게시글을 조회
    articles = Article.objects.all()
    context = {
        'articles': articles,
    }
    return render(request, 'index.html', context)
```

### Template (base.html)

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Document</title>
</head>

<body>
  {% block content %}
  {% endblock %}
</body>

</html>
```

### Template (index.html)

```html
{% extends 'base.html' %}

{% block content %}
<h1>INDEX</h1>
{% for article in articles %}
<p>글 번호: {{ article.pk }}</p>
<p>글 제목: {{ article.title }}</p>
<p>글 내용: {{ article.content }}</p>
<hr>
{% endfor%}
{% endblock  %}
```

### 구현된 화면

<img src="https://images.velog.io/images/gndan4/post/08af60a9-1034-4058-a5bd-16dca9d95901/image.png" alt="index page">

---

## GET, POST와 CSRF

form에서 다음과 같이 GET 메소드를 사용하고 있을 때 사용자가 submit 버튼을 누르면 새로 간 주소 맨 뒤에 '?title=입력된제목&content=입력된내용'이 표시되는 것을 확인할 수 있다.

GET 방식은 사용자가 입력한 데이터를 url에 넣어서 보낸다.

```html
<form action="{% url 'articles:create' %}" method="GET">
    <div class="mb-3">
      <label for="title" class="form-label">제목</label>
      <input name="title" type="text" class="form-control" id="title" placeholder="제목을 입력해주세요">
    </div>
    <div class="mb-3">
      <label for="content" class="form-label">내용</label>
      <textarea name="content" class="form-control" id="content" rows="3" placeholder="내용 입력"></textarea>
    </div>
    <input type="submit" class="btn btn-primary"></input>
  </form>
```

하지만 form 태그에서 POST 메소드를 사용할 경우 아래와 같은 오류가 발생한다. (인증 실패)

<img src="https://images.velog.io/images/gndan4/post/7c7c3608-6a04-4650-9443-99ccec90a21e/image.png" alt="403 forbiden">

CSRF 검증이 실패되었다고 나온다.

CSRF는 Cross-Site Request Fordery의 약자로, 사이트 간 요청 위조를 뜻한다.

장고에서는 이러한 공격을 막기 위해 믿을 수 있는 사이트에서 보낸 POST 요청만 처리할 수 있도록 클라이언트에게 csrf token이라는 것을 발급한다.

form 태그 안에 DTL을 활용하여 csrf_token을 발급하고 렌더링하면 form 태그 안에 hidden 타입을 가진 input 태그가 하나 생기는데, 이 안에 장고가 발급한 csrf_token이 들어있다. 이는 새로고침할 때마다 다른 값이 나타난다.

장고는 페이지를 요청받을 때마다 페이지에 각각 다른 도장을 찍어 보내는 것과 같다.

즉, 이 도장이 없거나 잘못된 도장을 가지고 있는 요청이 서버로 들어오게 될 경우 403 Forbiden 에러가 뜨면서 접근이 금지되는 것이다.

### GET과 POST의 차이

1. GET은 데이터가 url에 포함됨, POST는 url에 포함되지 않음
2. 의미가 다름 (GET 방식은 '데이터를 주세요'라고 한다면, POST는 '데이터를 보낼테니까 처리해주세요')