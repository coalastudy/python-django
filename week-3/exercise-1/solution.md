# 모범 답안



{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
def fail(request):
    return render(request, 'fail.html')

def help(request):
    return render(request, 'help.html')

def warn(request):
    return render(request, 'warn.html')
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="urls.py" %}
```python
# 상단 생
from facebook.views import fail, help, warn

urlpatterns = [
    path('admin/', admin.site.urls),

    path('play/', play),
    path('play2/', play2),
    path('dogeunchoi/profile/', my_profile),
    path('event/', event),
    path('fail/', fail),
    path('help/', help),
    path('warn/', warn),
]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="fail.html" %}
```markup
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>fail</title>
    <style>
        .container {
            background-color: red;
            color: #ffffff;
            padding: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        비정상적인 접근입니다.
    </div>
</body>
</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="help.html" %}
```markup
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>help</title>
    <style>
        .container {
            background-color: blue;
            color: #ffffff;
            padding: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        무엇을 도와드릴까요?
    </div>
</body>
</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="warn.html" %}
```markup
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>warn</title>
    <style>
        .container {
            background-color: orange;
            color: #ffffff;
            padding: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        다시 확인해주세요.
    </div>
</body>
</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 

