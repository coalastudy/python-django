# 모범 답안

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
def event(request):    choidogeun = '최도근'    age = 20    global count # 바깥영역의 변수를 사용할 때 global    count = count + 1 # 접속할 때마다 방문자 1 증가    if age > 19: # age가 19 보다 크면?        status = '성인'    else: # 성인이 아닌 경우        status = '청소년'    if count is 7:        lottery = '당첨!'    else:        lottery = '꽝...'    return render(request, 'event.html', { 'name': choidogeun, 'cnt': count, 'age': status, 'lottery': lottery })
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="urls.py" %}
```python
from facebook.views import eventurlpatterns = [    path('admin/', admin.site.urls),    path('play/', play),    path('play2/', play2),    path('dogeunchoi/profile/', my_profile),    path('event/', event),]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="event.html" %}
```markup
<!DOCTYPE html><html lang="en"><head>    <meta charset="UTF-8">    <title>event</title></head><body>    {{ name }}님({{ age }}) 안녕하세요? <br>    {{ cnt }} 번째 방문자이십니다!<br>    {{ lottery }}입니다</body></html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

