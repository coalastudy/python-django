# 모범 답안

models.py를 수정합니다.

{% code-tabs %}
{% code-tabs-item title="models.py" %}
```python
# Week 4 - Challenge 1
class Page(models.Model):
    master      = models.CharField(max_length=120)
    name        = models.CharField(max_length=120)
    text        = models.TextField()
    category    = models.CharField(max_length=120, default='')
    created_at  = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.name
```
{% endcode-tabs-item %}
{% endcode-tabs %}

수정 후  터미널에서 `python manage.py makemigrations` 실행, 이어서 `python manage.py migrate`실행합니다.​

admin.py를 아래와 같이 수정한 후 관리자 페이지에 다시 접속해보세요.

{% code-tabs %}
{% code-tabs-item title="admin.py" %}
```python
from django.contrib import admin

# Register your models here.
from facebook.models import Article
from facebook.models import Page

admin.site.register(Article)
admin.site.register(Page)
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 

