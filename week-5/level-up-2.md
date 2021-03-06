---
description: 예상 소요시간은 5~10분입니다.
---

# Level Up 2 - 오류 페이지 띄우기

## 비밀번호 오류 페이지 띄워주기

지금은 비밀번호를 잘못 입력하더라도 틀려서 수정이 실패한건지 아니면 인터넷이 끊긴건지 확인할 방법이 없습니다. 사용자의 혼란을 줄이기 위해 어떤 동작, 명령에 따른 따른 결과 메시지를 출력하는 것이 일반적입니다.

이 Level Up을 진행하려면 우선 `127.0.0.1/fail` 페이지가 만들어져 있어야합니다. 이 페이지를 만드는 작업은 **3주차 자율과제1**에서 진행하였습니다. 당시에 만든 페이지의 디자인을 개선하고 비밀번호가 틀렸을 때 그 페이지가 띄워지도록 로직을 수정해봅시다.

### 페이지 디자인

![&#xB514;&#xC790;&#xC778; &#xBAA9;&#xD45C;](../.gitbook/assets/image%20%28266%29.png)

위와 같은 디자인으로 페이지를 재구성해봅시다. 그동안 작업한 파일들, 특히 new\_feed.html을 복사하여 일부부문 수정하면 쉽게 만들 수 있습니다.

아래 소스코드를 참고해주세요.

{% code-tabs %}
{% code-tabs-item title="fail.html" %}
```markup
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>뉴스피드</title>
</head>
<body>
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

    .feed {
        background-color: #ffffff;
        border-top: 1px solid #c0c0c0;
        border-bottom: 1px solid #c0c0c0;
        margin: 7px 0;
        padding: 12px;
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
    .more {
        font-size: 14px;
        color: #6184dddd;
    }
    a {
        color: inherit;
        text-decoration: none;
    }

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
        font-soze: 18px;
    }
</style>
<div class="header">
    <div class="btn1"><a href="/new"><img src="/static/ic_pencil.jpg" width="22px" style="margin:9px 0 0 13px"></a></div>
    <div class="search">
        <input type="text" class="searchbar" placeholder="Search">
    </div>
    <div class="btn2"><img src="/static/ic_info.jpg" width="22px" style="margin:9px 13px 0 0"></div>
</div>
<div class="container">
    <div class="form_box">
        <h3>비밀번호가 틀렸습니다.</h3>
        <a href="javascript:history.back()">뒤로가기</a>
    </div>
</div>
<div class="footer">
    <div class="tab1"><img src="/static/ic_feed.jpg" width="22px" style="margin-top: 15px"></div>
    <div class="tab2"><img src="/static/ic_person.jpg" width="20px" style="margin-top: 14px"></div>
    <div class="tab3"><img src="/static/ic_globe.jpg" width="20px" style="margin-top: 14px"></div>
    <div class="tab4"><img src="/static/ic_etc.jpg" width="20px" style="margin-top: 14px"></div>
</div>
</body>

</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 이제 로직을 건드려야합니다.

아래 코드에서 10번째 줄, 25번재 줄 주변을 살펴보시면 됩니다. 이 코드를 추가함으로써 비밀번호가 틀렸을 때 오류페이이지로 이동할 수 있게 됐습니다.

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
def remove_feed(request, pk):
    article = Article.objects.get(pk=pk)

    if request.method == 'POST':
        if request.POST['password'] == article.password:
            article.delete()
            return redirect('/') # 첫페이지로 이동하기

        else:
            return redirect('/fail/')  # 비밀번호 오류 페이지 이동하기

    return render(request, 'remove_feed.html', {'feed': article})

def edit_feed(request, pk):
    article = Article.objects.get(pk=pk)

    if request.method == 'POST':
        if request.POST['password'] == article.password:
            article.author = request.POST['author']
            article.title = request.POST['title']
            article.text = request.POST['content']
            article.save()
            return redirect(f'/feed/{ article.pk }')
        else:
            return redirect('/fail/')  # 비밀번호 오류 페이지 이동하기

    return render(request, 'edit_feed.html', {'feed': article})
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 

