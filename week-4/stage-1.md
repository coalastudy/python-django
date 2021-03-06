# Stage 1 - 함께하는 페이스북 디자인

## 페이스북 레이아웃 잡기 

레이아웃은 웹사이트의 구조 배치를 말합니다. 가장 기본적인 틀을 말하는거죠. 레이아웃을 탄탄히 잡고 거기에 디자인을 덧붙이면 보기좋은 웹사이트가 나오는거죠.

![&#xCD5C;&#xC885; &#xBAA9;&#xD45C;](../.gitbook/assets/image%20%28127%29.png)

저희는 위와 같은 웹페이지를 만들어 볼 것 입니다. \(꽤나 페이스북 같죠?\) 하지만 처음부터 저 모양을 완성하려고 하면 굉장히 어려워요. 아주 간단한 것부터 디테일한 방향으로 천천히 만들어나가는게 해답입니다.

그림을 그린다고 생각해볼까요? 사람을 그릴때 갑자기 눈부터 그리진 않죠. 얼굴형을 잡고 턱을 세우고 머리카락을 배치하면서 점점 디테일 한 작업으로 나아갑니다. 그렇게 눈의 위치가 잡히면 그제서야 눈동자를 그릴 수 있는거죠.

![&#xADF8;&#xB9BC;&#xC744; &#xADF8;&#xB9AC;&#xB294; &#xC21C;&#xC11C;](../.gitbook/assets/image%20%284%29.png)

웹페이지를 만드는 순서도 이와 같습니다. 왕도가 없어요. 쉬운것부터 천천히 어려운것으로 나아가는거죠.

![&#xC6F9;&#xD398;&#xC774;&#xC9C0;&#xB97C; &#xB9CC;&#xB4DC;&#xB294; &#xC21C;&#xC11C;](../.gitbook/assets/image%20%28271%29.png)

## 분석

지난 2주차에서 2단 레이아웃을 배운적이 있습니다.

![](../.gitbook/assets/image%20%28123%29.png)

과제로 레이아웃 만들기를을 연습하면서 페이스북의 틀을 만들어보기도 했어요.

![](../.gitbook/assets/image%20%2823%29.png)

이번 시간에는 이렇게 만들어야 합니다.

![&#xBAA9;&#xD45C;](../.gitbook/assets/image%20%28171%29.png)

![&#xD2C0;](../.gitbook/assets/image%20%2833%29.png)

![&#xBD84;&#xC11D;](../.gitbook/assets/image%20%2878%29.png)

이 자료들을 보면서 나름의 계획을 짜봅시다. 머릿속으로 작업순서라도 그려보세요. 한결 수월해집니다.

## 실습

### 형태 잡기

#### 1. 우선 127.0.0.1:8000/으로 연결되는 페이지를 만듭니다. \(즉 첫페이지 접속시\)

![](../.gitbook/assets/image%20%28103%29.png)

{% code-tabs %}
{% code-tabs-item title="urls.py" %}
```python
from django.contrib import admin
from django.urls import path

from facebook.views import play
from facebook.views import play2
from facebook.views import my_profile
from facebook.views import event
from facebook.views import fail, help, warn
from facebook.views import newsfeed

urlpatterns = [
    path('admin/', admin.site.urls),

    path('play/', play),
    path('play2/', play2),
    path('dogeunchoi/profile/', my_profile),
    path('event/', event),
    path('fail/', fail),
    path('help/', help),
    path('warn/', warn),

    path('', newsfeed),

]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```text
# 위쪽 생

def newsfeed(request):
    return render(request, 'newsfeed.html')
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### 2. 간단하게 div만으로 형태를 잡습니다.

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>뉴스피드</title>
</head>

<body>
    <style>
    </style>
    <div class="header">
        <div class=“btn1">버튼1</div>
        <div class="search">
            <input type="text" class="searchbar" placeholder="Search">
        </div>
        <div class="btn2">버튼2</div>
    </div>
    <div class="container">
        내용물
    </div>
    <div class="footer">
        <div class="tab1">탭1</div>
        <div class="tab2">탭2</div>
        <div class="tab3">탭3</div>
        <div class="tab4">탭4</div>
    </div>
</body>

</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  3. 잘 만들어졌는지 확인할 수 있도록 style 부분을 수정하여 각 div에 배경색을 넣어줍니다.

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
<style>
    .header {
        background-color: #475d9f;
        color: #fff;
    }
    .container {
        background-color: #d7d8dc;
    }
    .footer {
        background-color: gray;
    }
</style>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  4. 결과를 확인하고 이제부터 본격적으로 css 조정작업을 진행합니다.

![](../.gitbook/assets/image%20%2889%29.png)

#### 5. 가운데 위치한 회색 박스\(내용물\), 즉 `.container` 클래스를 가진 div의 높이를 500px로 지정해줍니다.

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
.container {
    background-color: #d7d8dc;
    height: 500px;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

새로고침 후 아래와 같은 결과를 확인합니다.

![&#xACB0;&#xACFC;](../.gitbook/assets/image%20%28276%29.png)

#### 6. `.header`안에 있는 버튼1, search, 버튼2 요소들이 한줄에 오도록 만들어줍니다.

이때 `float:left`, `float:right`을 사용해 띄워줄 수도 있고, `position:absolute`을 사용해 위치를 지정해줄 수도 있으며, `dispaly:inline-block`으로 한줄에 오게할 수 있습니다. 이번에는 `position:absolute`을 사용합니다.

{% hint style="warning" %}
### position:absolute 사용시 주의할 점

주의할 점은 같은 div 안에 있는 모든 요소가 absolute일 때 그 div에 반드시 높이값을 지정해야 한다는 것 입니다. absolute은 공중에 떠있는 상태기 때문에 안 쪽의 모든 요소가 absolute라면 내용물이 없다고 판단하여 높이가 0이 되기 때문입니다.
{% endhint %}

**a\) .header 내의 모든 요소가 float:left이면서 높이값 없을 때**

![&#xC758;&#xB3C4;&#xD558;&#xC9C0; &#xC54A;&#xC740; &#xACB0;&#xACFC;](../.gitbook/assets/image%20%28250%29.png)

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
<style>
    .header {
        background-color: #475d9f;
        color: #fff;
        border-bottom: 1px solid #2c3863;
    }
    .btn1 {
        position: absolute;
        left: 10px;
    }
    .search {
        position: absolute;
        left: 100px;
        right: 100px;
    }
    .btn2 {
        position: absolute;
        right: 10px;
    }
    
    /* 이하 생략 */
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 b\) .header에 높이값을 지정했을 때

![&#xC758;&#xB3C4;&#xD55C; &#xACB0;&#xACFC;](../.gitbook/assets/image%20%28274%29.png)

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
<style>
    .header {
        background-color: #475d9f;
        color: #fff;
        border-bottom: 1px solid #2c3863;
        height: 50px;
    }
    .btn1 {
        position: absolute;
        left: 10px;
    }
    .search {
        position: absolute;
        left: 100px;
        right: 100px;
   }
    .btn2 {
        position: absolute;
        right: 10px;
    }
    
    /* 이하 생략 */ 
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### 7. 이번에는 `float:left` 방식으로 `.footer`안에 있는 탭1, 탭2, 탭3, 탭4가 한줄에 오도록 만들어줍니다.

float 사용시에도 div 안에 있는 모든 요소가 float일 때 그 height 값을 지정해주어야 합니다. 이유는 같습니다.

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
<style>
    /* …생략 */

    .footer {
        border-top: 1px solid #cccccc;
        background-color: #ffffff;
        height: 50px;
    }
    .tab1 {
        float: left;
    }
    .tab2 {
        float: left;
    }
    .tab3 {
        float: left;
    }
    .tab4 {
        float: left;
    }
</style>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

![](../.gitbook/assets/image%20%28270%29.png)

#### 8. 이제 검색창을 수정해보겠습니다. 테두리를 넣고 배경을 넣어줘야합니다.

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```text
.searchbar {
    border: 1px solid #2c3863;
    background-color: #323f6b;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 border의 색상은 background-color 보다 좀 더 진한색을 선택합니다. 다음 색상표를 이용하셔도 좋습니다.

![](../.gitbook/assets/image%20%28199%29.png)

새로고침 후 변경된 검색창을 확인하실 수 있습니다.

![](../.gitbook/assets/image%20%2869%29.png)

#### 9. .header 박스 아래쪽만 테두리를 주고, .footer 박스 색상을 \#fafafa로 변경한 뒤 위쪽으로만 테두리를 만들어 줍니다.

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
.header {
    background-color: #475d9f;
    color: #fff;
    height: 50px;
    border-bottom: 1px solid #2c3863;
}
.footer {
    border-top: 1px solid #cccccc;
    background-color: #fafafa;
    height: 50px;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

![&#xACB0;&#xACFC;](../.gitbook/assets/image%20%28161%29.png)

### 디테일 잡기

실습을 위해 미리 다운받으실 이미지가 있습니다.  
[이미지 다운로드](http://bit.ly/2z4e1rt)

#### 1. 상단부부터 세밀하게 조정해봅시다.

* style 가장 상단에 `* { box-sizing: border-box; margin: 0; padding: 0; }` 이라고 입력해줍니다 \(사이즈를 가장 쉽게 조절하게 해주는 규칙을 적용. 관례적.\)
* 검색창\(`.searchbar`\)의 크기를 100%로 만들고 `border-radius: 4px;` 속성을 이용해 모서리를 둥글게 해줍니다.
* 상단 높이를 50px에서 42px로 줄여줍니다.
* `.serachbar`에 `padding: 6px; margin-top: 7px;` 속성을 넣어 정가운데 위치하게 해줍니다.
* `.search`의 left와 right 값을 줄여 검색창의 크기를 키워줍니다. `.btn1`과 `.btn2`의 left, right 값은 0으로 줄여줍니다.
* 검색키워드의 색을 바꾸기 위해 `.searchbar`에 `color:#ffffff`도 입력해줍니다.
* 다운받은 이미지들을 static 폴더안에 넣은 후, 버튼1을 `<img src="/static/ic_pencil.jpg" width="22px" style="margin:9px 0 0 13px">`로 변경해줍니다.

![&#xACB0;&#xACFC;](../.gitbook/assets/image%20%2836%29.png)

#### 2. 하단부의 탭을 조정해봅시다.

* .tab1, .tab2, .tab3, .tab4 style에 `width:25%` 를 넣어줍니다.
* 가운데 정렬을 하기 위해 `.footer`에 `text-align: center;`를 넣어줍니다.
* 탭1을 `<img src="/static/ic_feed.jpg" width="22px" style="margin-top: 15px”>`
* 탭2를 `<img src="/static/ic_person.jpg" width="20px" style="margin-top: 14px”>`
* 탭3를 `<img src="/static/ic_globe.jpg" width="20px" style="margin-top: 14px">`
* 탭4를 `<img src="/static/ic_etc.jpg" width="20px" style="margin-top: 14px">` 이미지로 각각 변경해줍니다.
* `.footer`에 `position:fixed; bottom: 0; left: 0; right: 0;` 속성을 추가해줍니다.
* .container의 height을 삭제합니다.
* style 최상단에 `body { background-color: #d7d8dc; }`를 추가합니다.

![&#xACB0;&#xACFC;](../.gitbook/assets/image%20%282%29.png)

현재까지 작성한 스타일시트는 아래와 같습니다.

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
<style>
    body { background-color: #d7d8dc; }
    * { box-sizing: border-box; margin: 0; padding: 0; }
    .header {
        background-color: #475d9f;
        color: #fff;
        height: 42px;
        border-bottom: 1px solid #2c3863;
    }
    .btn1 {
        position: absolute;
        left: 0px;
    }
    .search {
        position: absolute;
        left: 50px;
        right: 50px;
    }
    .btn2 {
        position: absolute;
        right: 0px;
    }
    .searchbar {
        border: 1px solid #2c3863;
        background-color: #323f6b;
        width: 100%;
        padding: 6px;
        margin-top: 7px;
        border-radius: 4px;
        color: #fff;
    }

    .container {
        background-color: #d7d8dc;
    }
    .footer {
        position: fixed;
        bottom: 0;
        left: 0;
        right: 0;
        border-top: 1px solid #cccccc;
        background-color: #ffffff;
        height: 50px;
        background-color: #fafafa;
        text-align: center;
    }
    .tab1 {
        float: left;
        width: 25%;
    }
    .tab2 {
        float: left;
        width: 25%;
    }
    .tab3 {
        float: left;
        width: 25%;
    }
    .tab4 {
        float: left;
        width: 25%;
    }
    .date {
        color: #999;
        margin-bottom: 10px;
    }
    .title {
        color: #6184dddd;
        font-weight: 600;
    }
    .content {
        margin-top: 5px;
    }
    .accessory {
        border-top: 1px solid #eee;
        padding-top:10px;
        margin-top:10px;
        color: #999;
        font-size: 14px;
    }

</style>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

####  3. 안쪽 피드를 만들어봅시다.

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
<div class="container">
    <div class="feed">
        <h3 class="name">이름</h3>
        <div class="date">날짜</div>
        <a class="title">글 제목</a>
        <p class="content">글 내용</p>
        <div class="accessory">
            <img src="/static/ic_like.jpg" width="16px"> Like <img src="/static/ic_comment.jpg" width="16px"> Comments
        </div>
    </div>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 위 코드처럼 안쪽 일부만 수정해주세요.

![&#xACB0;&#xACFC;](../.gitbook/assets/image%20%28299%29.png)

#### 4. 안쪽 피드의 스타일을 조정합니다.

이제 스타일을 입혀봅시다.

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
.feed {
    background-color: #ffffff;
    border-top: 1px solid #c0c0c0;
    border-bottom: 1px solid #c0c0c0;
    margin: 7px 0;
    padding: 12px;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 이 간단한 코드만으로도 제법 페이스북의 모습이 갖춰집니다.

![](../.gitbook/assets/image%20%28158%29.png)

#### 5. 피드의 글자 관련 스타일도 변경해봅시다.

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
.date {
    color: #999;
    margin-bottom: 10px;
}
.title {
    color: #6184dddd;
    font-weight: 600;
}
.content {
    margin-top: 5px;
}
.accessory {
    border-top: 1px solid #eee;
    padding-top:10px;
    margin-top:10px;
    color: #999;
    font-size: 14px;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

![&#xACB0;&#xACFC;](../.gitbook/assets/image%20%28291%29.png)

#### 6. `<div class=“feed”>~~~</div>`를 복사해서 한번 더 붙여넣어 봅시다.

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
<div class="container">
    <div class="feed">
        <h3 class="name">이름</h3>
        <div class="date">날짜</div>
        <a class="title">글 제목</a>
        <p class="content">글 내용</p>
        <div class="accessory">
            <img src="/static/ic_like.jpg" width="16px"> Like <img src="/static/ic_comment.jpg" width="16px"> Comments
        </div>
    </div>
    <div class="feed">
        <h3 class="name">이름</h3>
        <div class="date">날짜</div>
        <a class="title">글 제목</a>
        <p class="content">글 내용</p>
        <div class="accessory">
            <img src="/static/ic_like.jpg" width="16px"> Like <img src="/static/ic_comment.jpg" width="16px"> Comments
        </div>
    </div>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

![&#xACB0;&#xACFC;](../.gitbook/assets/image%20%2888%29.png)



