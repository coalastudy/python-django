---
description: 예상 소요시간은 5~10분입니다.
---

# Level Up 1 - 게시물 작성 후

## 페이지 자동 이동

### 게시물 작성 완료 후 해당 게시물의 자세히보기 페이지로 자동 이동하기

지금 게시물을 작성하고 게시 버튼을 누르면, 작성하기 페이지가 다시한번 로드됩니다. 실제로 작성은 되었지만, 즉각적으로 확인하기 어려운 상태입니다.

일반적으로는 게시글을 작성하면 그 게시물의 자세히보기 페이지로 이동시키는 코드를 심어줍니다.

아래 코드에서 **1번째 줄과 2번째 줄**을 살펴봅시다.

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
from django.shortcuts import render, redirect

# 중간생략

def new_feed(request):
    if request.method == 'POST': # 폼이 전송되었을 때만 아래 코드를 실행
        new_article = Article.objects.create(
            author=request.POST['author'],
            title=request.POST['title'],
            text=request.POST['content'],
            password=request.POST['password']
        )

        # 새글 등록 끝
        return redirect(f'/feed/{ new_article.pk }')

    return render(request, 'new_feed.html')
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 우선 1번째 줄입니다.  
`from django.shortcuts import render, redirect`   
**,\(콤마\)** 뒤에 **redirect가 새로 추가된** 걸 확인하실 수 있습니다.

`from A import B` 구문은 쉽게 말하면 **A에서 B라는 기능을 불러와라**라는 것 입니다. urls.py에서 url을 views의 함수와 연결시킬 `from facebook.views import new_feed`를 사용한것과 같습니다. facebook 폴더의 views에서 new\_feed 함수, 즉 그러한 기능을 불러온 것입니다.

redirect의 기능은 특정 페이지로 이동하게끔 하는 것 입니다. `redirect('http://naver.com')`이라고 입력하면 정말 네이버로 이동됩니다.

우리의 게시물 자세히 보기 주소는 `http://127.0.0.1/feed/1` , `http://127.0.0.1/feed/2`와 같은 형태죠. 1번은 2번은 글의 번호입니다. 위에서 8번째 줄을 보시면 새글이 저장되면서\(create\) 동시에 new\_article에 새롭게 쓰여진 글의 정보가 자동으로 등록됩니다. new\_aritlce.pk는 글의 번호구요.

앞의  `http://127.0.0.1`은 생략할 수 있으니 `/feed/{글 번호}`의 형식으로 redirect 시켜주기만 하면 됩니다. 이 때 `/feed/new_article.pk`라고 하면 정말 주소창에서 `http://127.0.0.1/ffed/new_article.pk`로 이동되고 오류가 나게 됩니다. **new\_article.pk**는 파이썬 기초시간에 배운 **변수**에 해당됩니다. 이러한 **자료를 따옴표 안에 넣으려면 따옴표 맨앞에 f를 붙이고 { } 중괄호 안에 입력**하면 됩니다. 이렇게요.

`f'/feed/{ new_article.pk }'`

## if로 내용 확인

### 아무 내용이 없으면 게시물 작성하지 않기

7번째줄이 추가되었고 8~16번째 줄이 한 탭씩 오른쪽으로 들어가게 됐습니다. 별다른 변화는 없습니다.

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
from django.shortcuts import render, redirect

# 중간생략

def new_feed(request):
    if request.method == 'POST': # 폼이 전송되었을 때만 아래 코드를 실행
        if request.POST['author'] != '' and request.POST['title'] != '' and request.POST['content'] != '' and request.POST['password'] != '':
            new_article = Article.objects.create(
                author=request.POST['author'],
                title=request.POST['title'],
                text=request.POST['content'],
                password=request.POST['password']
            )

            # 새글 등록 끝
            return redirect(f'/feed/{ new_article.pk }')

    return render(request, 'new_feed.html')
```
{% endcode-tabs-item %}
{% endcode-tabs %}

위의 코드가 없었을 때 게시버튼을 누르면 **빈 내용의 글들이 계속하여 등록되었을 겁니다.** 이제 7번째줄을 추가함으로써 그런일은 방지할 수 있게 됐습니다.

원리는 간단합니다. `request.POST['author']`에는 유저가 글쓰기 페이지에서 작성한 **글쓴이의 이름**이 담겨있는데요. 이 부분이 비어있다면, 즉 `''`라는 뜻이므로, **if** 안에 들어갈 수 없게되고 실행이 되지 않는거죠. if는 `''`이 아닐때만 실행하라고 명시되어 있으니까요.

이때 and의 역할을 궁금해하시는 분들이 있습니다.  
`if request.POST['author'] != '' and request.POST['title'] != '' and request.POST['content'] != '' and request.POST['password'] != '':`  
풀이하면, 글쓴이의 이름이 공백이 아니고 제목이 공백이 아니고 내용이 공백이 아니고 패스워드도 공백이 아니라면 if를 실행하라는 의미입니다. **즉 입력 안한 필드가 하나라도 있다면 글은 등록될 수 없습니다.**

