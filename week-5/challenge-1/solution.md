# 모범 답안

views.py안에 있는 new\_feed 함수의 일부부만 수정하면 됩니다.

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
def new_feed(request):
    if request.method == 'POST': # 폼이 전송되었을 때만 아래 코드를 실행
        if request.POST['author'] != '' and request.POST['title'] != '' and request.POST['content'] != '' and request.POST['password'] != '':
            text = request.POST['content']
            text = text + ' - 추신: 감사합니다.'

            new_article = Article.objects.create(
                author=request.POST['author'],
                title=request.POST['title'],
                text=text,
                password=request.POST['password']
            )

            # 새글 등록 끝
            return redirect(f'/feed/{ new_article.pk }')

    return render(request, 'new_feed.html')
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 

