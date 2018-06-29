# 모범 답안

{% code-tabs %}
{% code-tabs-item title="page\_list.html" %}
```markup
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>page list</title>
</head>
<body>
{% for page in pages %}

<div style="border:1px solid #b2b2b2; padding:10px; margin: 10px;">
{{ page.name }} - {{ page.master}} ({{ page.category }})<br>
{{ page.text }}<br>
- {{ page.created_at }}
</div>

{% endfor %}
</body>
</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```python
from facebook.models import Page

# 중간생

def pages(request):
    pages = Page.objects.all()
    return render(request, 'page_list.html', {'pages': pages })
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
from facebook.views import event
from facebook.views import fail, help, warn
from facebook.views import newsfeed
from facebook.views import detail_feed
from facebook.views import pages

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
    path('feed/<pk>/', detail_feed),

    path('pages/', pages)
]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

