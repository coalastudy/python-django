# 모범 답안



{% code-tabs %}
{% code-tabs-item title="profile.html" %}
```markup
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF
-8">
    <title>Challenge1 - WEEK3</title>
</head>
<body>
    <!--이 안에 있는 내용은 단순 코멘트로 아무런 작동을 하지 않아요-->
    <!--href에는 이동하려는 주소를 입력하면 됩니다-->
    <a href="http://127.0.0.1:8000/play">play으로 이동하기</a><br>
    <!--127.0.0.1:8000은 생략할 수 있습니다.-->
    <a href="/play2">play2으로 이동하기</a>
</body>
</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
def my_profile(request):
    return render(request, 'profile.html')
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="urls.py" %}
```python
from django.contrib import admin
from django.urls import path

from facebook.views import play
from facebook.views import play2
from facebook.views import my_profile

urlpatterns = [
    path('admin/', admin.site.urls),

    path('play/', play),
    path('play2/', play2),
    path('dogeunchoi/profile/', my_profile)
]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

