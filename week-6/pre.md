---
description: >-
  반복적이거나 타이핑의 양이 많아 효율성을 저하시키는 코드를 모아 필요시 복사&붙여넣기할 수 있도록 준비하였습니다. 시간이 충분하다면 처음부터
  끝까지 직접 타이핑하며 완성하는게 좋습니다. 주로 시간이 한정되어있는 스터디 중에 이용됩니다.
---

# Pre - 실습 코드 복사

## Stage 1 - 코멘트 모델링

### 코멘트 모델링

#### 강의자료 7page <a id="7p"></a>

{% code-tabs %}
{% code-tabs-item title="models.py에 추가될 부분" %}
```python
# 코멘트 모델
class Comment(models.Model):
    article     = models.ForeignKey(Article, on_delete=models.CASCADE, related_name='comments')
    author      = models.CharField(max_length=120)
    text        = models.TextField()
    password    = models.CharField(max_length=120)
    created_at  = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.text
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Stage 2 - 살아있는 코멘트

### 코멘트 보기 부분 html 작성

#### 강의자료 12page <a id="12p"></a>

{% code-tabs %}
{% code-tabs-item title="detail\_feed.html에 추가될  부분" %}
```markup
<div class="comment_list">
    <div class="comment"><span class="name">코멘트 글쓴이</span> 코멘트 내용</div>
    <div class="comment__date">코멘트 생성일 <a href="/코멘트삭제주소"><img src="/static/ic_delete.png" height="16px"></a></div>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  강의자료 13page <a id="13p"></a>

이미 기존 코드에 &lt;style&gt;&lt;/style&gt;이 있을 겁니다. 그 태그 밑에 또 새로운 &lt;style&gt;&lt;/style&gt;을 삽입해주세요. 삽입할 코드는 아래와 같습니다.

{% code-tabs %}
{% code-tabs-item title="detail\_feed.html의 style  부분" %}
```markup
<style>
    /* 이 밑으로는 코멘트와 관련된 스타일입니다. */
    /* 이 안에 둘러쌓인 글은 프로그램에 영향을 미치지 않는 메모입니다. */
    .comment_list {
        background-color: #f0f1f4;
        border-bottom: 1px solid #bcbdc3;
        padding-top: 0.1px;
    }

    .comment {
        background-color: #fff;
        border-radius: 30px;
        margin: 15px;
        padding: 15px;
        margin-bottom: 0;
    }

    .comment__date {
        margin: 0 15px;
        padding: 8px 15px;
        padding-bottom: 0px;
        font-size: 13px;
    }

    .name {
        font-weight: bold;
        color: #445994;
    }

    .form-wrapper {
        padding: 15px;
    }

    /* 똑같은 스타일을 적용하고 싶으면 ,를 입력해주면 됩니다. */
    .form-wrapper input,
    .form-wrapper textarea {
        border: 1px solid #ddd;
        width: 100%;
        padding: 5px;
        font-size: 14px;
        box-sizing: border-box;
        border-radius: 5px;
        margin-top: 2px;
        margin-bottom: 5px;
    }

    button {
        border: 1px solid #405ea3;
        background-color: #4967ad;
        color: #fff;
        font-weight: 500;
        font-size: 15px;
        padding: 3px 16px;
        border-radius: 2px;
    }
</style>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### 코멘트 쓰기 폼 만들기

####  강의자료 20page <a id="20p"></a>

{% code-tabs %}
{% code-tabs-item title="detail\_feed.html에 추가될 부분" %}
```markup
<div>
    <span>Comments</span>
    <form action="" method="POST">
        {% csrf_token %}
        <input type="text" name="author" placeholder="이름" /><br/>
        <input type="password" name="password" placeholder="비밀번호" /><br/>
        <textarea name="text" placeholder="코멘트 내용"></textarea>
        <button type="submit">등록</button>
    </form>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### 코멘트 쓰기 로직 연결

#### 강의자료 24page <a id="24p"></a>

{% code-tabs %}
{% code-tabs-item title="views.py에 수정될 부분" %}
```python
def detail_feed(request, pk):
    article = Article.objects.get(pk=pk)

    if request.method == 'POST':  # new comment
        Comment.objects.create(
            article=article,
            author=request.POST['author'],
            text=request.POST['text'],
            password=request.POST['password']
        )

        return redirect(f'/feed/{ article.pk }')

    return render(request, 'detail_feed.html', {'feed': article})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Stage 3 - 배포 준비

### 배포를 위한 코드 수정

#### 강의자료 29page <a id="29p"></a>

```python
ALLOWED_HOSTS = ['localhost', '127.0.0.1', '.pythonanywhere.com']
```

```markup
<meta name="viewport" content="width=device-width, user-scalable=no">
```

### git 저장소 생성하고 저장하기

#### 강의자료 31page <a id="31p"></a>

{% code-tabs %}
{% code-tabs-item title=".gitignore" %}
```text
*.pyc
*~
__pycache__
myvenv
venv
django_venv
django_env
db.sqlite3
/static
.DS_Store
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Stage 4 - 배포/재배포 방법

### python anywhere에서 배포하기

#### 강의자료 42page <a id="42p"></a>

{% code-tabs %}
{% code-tabs-item title="wsgi.py" %}
```python
import os
import sys

path = '/home/자신의pythonanywhere이름/django_facebook'
if path not in sys.path:
    sys.path.append(path)

os.environ['DJANGO_SETTINGS_MODULE'] = 'main.settings'

from django.core.wsgi import get_wsgi_application
from django.contrib.staticfiles.handlers import StaticFilesHandler
application = StaticFilesHandler(get_wsgi_application())
```
{% endcode-tabs-item %}
{% endcode-tabs %}

