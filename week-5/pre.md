---
description: >-
  반복적이거나 타이핑의 양이 많아 효율성을 저하시키는 코드를 모아 필요시 복사&붙여넣기할 수 있도록 준비하였습니다. 시간이 충분하다면 처음부터
  끝까지 직접 타이핑하며 완성하는게 좋습니다. 주로 시간이 한정되어있는 스터디 중에 이용됩니다.
---

# Pre - 실습 코드 복사

## Stage 1 - 게시글 쓰기 페이지 만들기

### 폼 만들기 연습

#### 강의자료 9page <a id="9p"></a>

```markup
<div>
    <h3>게시물 올리기</h3>
    <input type="text" placeholder="글쓴이의 이름은?" ><br>
    <input type="password" placeholder="글 비밀번호" ><br>
    <input type="text" placeholder="제목을 입력해주세요." ><br>
    <textarea placeholder="내용을 입력해주세요."></textarea><br>
    <button>게시</button>
</div>
```

####  강의자료 11page

{% code-tabs %}
{% code-tabs-item title="style 안에 들어갈 부분" %}
```css
.form_box {
    background-color: #ffffff;
    margin: 10px;
    border-radius: 4px;
    border: 1px solid #ddd;
    padding: 10px;
}
.input_field {
    border: 1px solid #ddd;
    border-radius: 4px;
    padding: 4px;
    margin: 3px 0;
    font-size: 14px;
    width: 100%;
}
.textarea_field {
    border: 1px solid #ddd;
    border-radius: 4px;
    padding: 4px;
    margin: 3px 0;
    font-size: 14px;
    width: 100%;
    height: 160px;
}
.write_button {
    background-color: #475d9f;
    border: 1px solid #323f6b;
    color: #ffffff;
    border-radius: 4px;
    padding: 2px 8px;
    font-size: 18px;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Stage 2 - 게시글 생성 로직 연결

### 로직 만들기

#### 강의자료 18page <a id="18p"></a>

{% code-tabs %}
{% code-tabs-item title="views.py에서 수정될 부분" %}
```python
def new_feed(request):
    if request.method == 'POST': # 폼이 전송되었을 때만 아래 코드를 실행
        new_article = Article.objects.create(
            author=request.POST['author'],
            title=request.POST['title'],
            text=request.POST['content'],
            password=request.POST['password']
        )

        # 새글 등록 끝

    return render(request, 'new_feed.html')
```
{% endcode-tabs-item %}
{% endcode-tabs %}

##  Stage 3 - 게시글을 수정, 삭제하는 페이

### 수정, 삭제 링크 연결

#### 강의자료 25page <a id="25p"></a>

```markup
<div><a href="/feed/{{ feed.pk }}/edit"><img src="/static/ic_edit.png" height="16px"></a> <a href="/feed/{{ feed.pk }}/remove"><img src="/static/ic_delete.png" height="16px"></a></div>
```

### 삭제페이지 폼 만들기 연습

#### 강의자료 28page <a id="28p"></a>

{% code-tabs %}
{% code-tabs-item title="remove\_feed.html에서 수정될 부분" %}
```markup
<div class="form_box">
    <form method="POST">
        {% csrf_token %}
        <h3>{{ feed.title }} - 삭제하기</h3>
        <input class="input_field" type="password" placeholder="글 비밀번호" name="password"><br>
        <button class="write_button">삭제</button>
    </form>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

###  게시글 수정 페이지 만들기

#### 강의자료 31page <a id="31p"></a>

{% code-tabs %}
{% code-tabs-item title="edit\_feed.html에서 수정될 부분" %}
```markup
<div class="form_box">
    <form method="POST">
        {% csrf_token %}
        <h3>글 수정하기</h3>
        <input class="input_field" type="text" placeholder="글쓴이의 이름은?" name="author" value="{{ feed.author }}"><br>
        <input class="input_field" type="password" placeholder="글 비밀번호" name="password"><br>
        <input class="input_field" type="text" placeholder="제목을 입력해주세요." name="title" value="{{ feed.title }}"><br>
        <textarea class="textarea_field" placeholder="내용을 입력해주세요." name="content">{{ feed.text }}</textarea><br>
        <button class="write_button">수정</button>
    </form>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Stage 4 - 게시글 수정, 삭제 로직 연결

### 게시글 수정 로직 짜기

#### 강의자료 34page <a id="34p"></a>

{% code-tabs %}
{% code-tabs-item title="views.py에서 수정될 부분" %}
```python
def edit_feed(request, pk):
    article = Article.objects.get(pk=pk)

    if request.method == 'POST':
        article.author = request.POST['author']
        article.title = request.POST['title']
        article.text = request.POST['content']
        article.save()
        return redirect(f'/feed/{ article.pk }')

    return render(request, 'edit_feed.html', {'feed': article})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

###  게시글 삭제 로직 짜기

#### 강의자료 37page <a id="37p"></a>

{% code-tabs %}
{% code-tabs-item title="views.py에서 수정될 부분" %}
```python
def remove_feed(request, pk):
    article = Article.objects.get(pk=pk)

    if request.method == 'POST':
        if request.POST['password'] == article.password:
            article.delete()
            return redirect('/') # 첫페이지로 이동하기

    return render(request, 'remove_feed.html', {'feed': article})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

