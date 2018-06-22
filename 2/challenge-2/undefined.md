# 모범 답안

{% code-tabs %}
{% code-tabs-item title="urls.py" %}
```python
from django.contrib import adminfrom django.urls import pathfrom facebook.views import playurlpatterns = [    path('admin/', admin.site.urls),    path('play/', play)]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
from django.contrib import adminfrom django.urls import pathfrom facebook.views import playurlpatterns = [    path('admin/', admin.site.urls),    path('play/', play)]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="play.html" %}
```markup
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>페이지의 타이틀</title>
</head>

<body>
    <style>
        body {
            margin: 0;
            padding: 0;
        }

        .app {
            width: 300px;
            overflow: hidden;
            border: 1px solid #ddd;
        }

        .header {
            text-align: center;
            background-color: #134c7b;
        }

        .container {
            color: #134371;
            font-weight: 600;
        }

        .name {
            padding: 5px;
        }

        .content {
            padding: 5px;
        }
    </style>
    <div class="app">
        <div class="header">
            <img src="/static/insta.png">
        </div>
        <div class="container">
            <div class="name">Cristiano Ronaldo</div>
            <div class="img">
                <img width="100%" src="http://cfile22.uf.tistory.com/image/133BDD394ED7357A166C3D">
            </div>
            <div class="content">♥︎ 100 likes</div>
        </div>
    </div>
</body>

</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

