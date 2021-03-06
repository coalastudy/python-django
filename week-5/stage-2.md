# Stage 2 - 게시글 생성 로직 연결

## 장고의 로직

이전 스테이지에서 게시물을 올릴 수 있는 페이지를 만들었습니다. 하지만 내용을 입력하고 게시버튼을 눌러도 실제로 글이 등록되지는 않습니다.

![](../.gitbook/assets/image%20%28253%29.png)

방금 만든 게시글 올리기 페이지가 아닌, 관리자 모드에서 글을 직접 생성할 때는 데이터가 제대로 등록됩니다. 문제는 우리가 만든 게시글 올리기 페이지가 제대로 작동하지 않는다는 건데요. **"방금 쓴 내용물로 게시글을 등록해줘"**라고 요청하는 부분은 만든적이 없기 때문입니다. 단지 입력창만 들어간 아무 기능이 없는 빈 페이지만 만든 상태죠.

![](../.gitbook/assets/image%20%2834%29.png)

실제로 동작하게 하려면 위와 같은 흐름을 고려해야합니다. 단지 페이지를 디자인하고 버튼을 넣는게 아니라, "글을 등록해라"라는 기능을 가진 행동이 취해져야 하는 것이고, 이런 작업은 html, css가 아닌 파이썬을 통해 수행됩니다.

![&#xAC8C;&#xC2DC;&#xBC84;&#xD2BC;&#xC744; &#xB204;&#xB974;&#xBA74; &#xD30C;&#xC774;&#xC36C; &#xB85C;&#xC9C1;&#xC774; &#xC791;&#xB3D9;&#xD574;&#xC57C;&#xD55C;&#xB2E4;.](../.gitbook/assets/image%20%28160%29.png)

#### 파이썬이 해야할 일 \(로직 처리\)

1. 게시버튼이 클릭되었다는 것을 인지해야한다.
2. 클릭이 되었다면, 작성된 글쓴이, 비밀번호, 제목, 내용 정보를 가져와야 한다.
3. 가져온 정보를 DB에 등록해줘야 한다.

이때 **로직**이란, 방금 설명한 해야할 일처럼 무언가 기능적으로 처리해야하는 부분을 말합니다.

{% hint style="info" %}
### 장고와 파이썬의 차이가 뭐죠?

장고는 웹개발을 도와주는 남이 이미 만들어둔 파이썬 코드일 뿐 입니다. 현 수준에서는 장고와 파이썬이 같다고 생각해도 좋습니다.
{% endhint %}

## 실습

### 로직 만들기

#### 1. new\_feed.html의 form 부분을 수정해줍니다.

{% code-tabs %}
{% code-tabs-item title="new\_feed.html" %}
```markup
<div class="form_box">
    <form method="POST">
        {% csrf_token %}
        <h3>게시물 올리기</h3>
        <input class="input_field" type="text" placeholder="글쓴이의 이름은?" name="author"><br>
        <input class="input_field" type="password" placeholder="글 비밀번호" name="password"><br>
        <input class="input_field" type="text" placeholder="제목을 입력해주세요." name="title"><br>
        <textarea class="textarea_field" placeholder="내용을 입력해주세요." name="content"></textarea><br>
        <button class="write_button">게시</button>
    </form>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### 2. views.py에 new\_feeed 함수를 찾아 다음과 같은 로직을 추가해줍니다. 

{% code-tabs %}
{% code-tabs-item title="views.py" %}
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

#### 3. 새로고침 후 글이 잘 추가되나 확인합니다.

## 이해

갑자기 글이 추가되기 시작합니다. 원래는 빠져있던, 작성하지 않았던 로직을 파이썬을 통해 만들어줌으로써 가능해진 일입니다.

![](../.gitbook/assets/image%20%2866%29.png)

이 로직을 다시 살펴볼까요?

{% code-tabs %}
{% code-tabs-item title="views.py" %}
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

* views.py 안에 있는 new\_feed가 게시물 쓰기 페이지를 담당중
* 원래는 페이지를 표시하는 `return render()` 기능만 있었음
* 이제는 POST 요청이 들어오면 `Article.objects.create()`를 실행하는 로직이 추가됨

html은 어떤 원리로 작성되었는지 살펴봅시다.

![html&#xC5D0;&#xC11C; POST&#xB85C; &#xB370;&#xC774;&#xD130;&#xB97C; &#xBCF4;&#xB0B4;&#xB294; &#xBC29;&#xBC95;](../.gitbook/assets/image%20%2891%29.png)

이렇게 **name으로 이름을 지정**하여 보내진 데이터는 views.py의 new\_feed 함수에서 `request.POST[name]`을 통해 읽어들일 수 있습니다. 장고가 없다면 훨씬 어렵고 복잡하게 데이터를 가져와야합니다. 그러나 우리는 장고 덕분에, name만 원하는 이름으로 맞춰주면 **쉽게 데이터를 읽을 수 있습니다.** 이 방식에는 엄청난 원리나 철학이 담겨져 있지 않습니다. 단지 그렇게 하도록 **장고에서 미리 규칙을 정했을 뿐** 입니다.

![](../.gitbook/assets/image%20%28242%29.png)

