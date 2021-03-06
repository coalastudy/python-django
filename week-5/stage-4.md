# Stage 4 - 게시글 수정, 삭제 로직 연결

## 게시글 수정 로직

아직은 동작하지 않는 게시글 수정페이지를 만들어봤습니다. 이제 실제로 수정 기능이 동작하도록 로직을 작성해보겠습니다.

### 실습

#### 게시글이 수정되도록 파이썬 로직을 작성합니다.

views.py를 열어 edit\_feed 함수를 수정합니다.

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
def edit_feed(request, pk):
    article = Article.objects.get(pk=pk)

    if request.method == 'POST':
        article.author = '수정된 글쓴이 111!'
        article.title = '수정된 제목 222@@'
        article.text = '수정된 내용 333###'
        article.save()
        return redirect(f'/feed/{ article.pk }')

    return render(request, 'edit_feed.html', {'feed': article})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 이제 게시물을 수정해보세요. 어떤 내용을 입력하더라도 **항상 위에 입력한 값으로 수정**될 것 입니다. 글쓴이명은 '수정된 글쓴이 111!', 제목은 '수정된 제목 222@@' 이렇게요.

즉 저 부분을 사용자가 입력한 데이터로 바꿔넣을 수 있다면, 수정 기능이 올바르게 동작할 것입니다.

#### 게시글이 입력한 내용으로 수정되도록 파이썬 로직을 작성합니다.

form에서 전달받은 데이터로 수정 해줍니다.

{% code-tabs %}
{% code-tabs-item title="views.py" %}
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

 이제 의도한 대로 게시물이 수정될 것 입니다. 확인해보세요!

### 이해하기

수정된 데이터를 모델에 반영 합니다.

![](../.gitbook/assets/image%20%28224%29.png)

## 게시글 삭제 로직

### 실습

#### 게시글이 실제로 수정되도록 파이썬 로직을 작성합니다.

views.py를 열어 edit\_feed 함수를 수정합니다.

{% code-tabs %}
{% code-tabs-item title="views.py" %}
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

### 이해하기

![](../.gitbook/assets/image%20%28255%29.png)



