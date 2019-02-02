# Stage 4 - 배포/재배포 방법

## python anywhere에서 설정하기

### 실습

#### 1. [https://www.pythonanywhere.com](https://www.pythonanywhere.com) 에 로그입합니다.

#### 2. 상단에서 `Dashboard`탭에 접속합니다.

![](../.gitbook/assets/image%20%2848%29.png)

#### 3. `$Bash`를 클릭합니다.

![](../.gitbook/assets/image%20%28241%29.png)

#### 4. 웹에 나타나는 터미널에 git clone [https://git~~복사한git주소~~facebook.git](https://git~~복사한git주소~~facebook.git) 입력합니다.

![](../.gitbook/assets/image%20%2851%29.png)

#### 5. 터미널에 `cd django_facebook` 를 입력합니다.

#### 6. 이어서 `virtualenv --python=python3.6 venv` 를 입력합니다. \(환경설정&설치가 1~5분 정도 소요됩니다.\)

#### 7. 설치가 끝나면 `source venv/bin/activate` 을 입력합니다.

#### 8. 장고를 설치합니다. 

`pip install django`

#### 9. 터미널에 다음 두 명령을 입력합니다. 

`python manage.py makemigrations`

`python manage.py migrate`

#### 10. 관리자 계정도 새로 만들어줍니다. 

`python manage.py createsuperuser`

## python anywhere에서 배포하기

### 실습

#### 1. Web 탭을 선택합니다.

![](../.gitbook/assets/image%20%2818%29.png)

#### 2. Add a new web app을 클릭하고 곧바로 Next를 누릅니다.

![](../.gitbook/assets/image%20%2886%29.png)

#### 3. Manual configuration을 선택합니다.

![](../.gitbook/assets/image%20%28196%29.png)

#### 4. Python 3.6을 선택합니다.

![](../.gitbook/assets/image%20%28100%29.png)

#### 5. Next를 클릭합니다.

![](../.gitbook/assets/image%20%2877%29.png)

#### 6. Virtualenv 주소를 입력합니다.

`/home/dogeunchoi/django_facebook/venv`

![](../.gitbook/assets/image%20%28168%29.png)

![\* &#xC798;&#xBABB; &#xC124;&#xC815;&#xD558;&#xBA74; &#xC704;&#xC640; &#xAC19;&#xC740; &#xC624;&#xB958;&#xAC00; &#xD45C;&#xC2DC;&#xB429;&#xB2C8;&#xB2E4;.](../.gitbook/assets/image%20%28180%29.png)

#### 7. WSGI를 설정합니다.

아래의 파란색 글씨인 `/home/dogeunchoi/` 부분에서 **dogeunchoi**가 **자신의 pythonanywhere 이름**입니다. 잠시 후 사용해야하니 기억해주세요.

![&#xCD08;&#xB85D;&#xC0C9; &#xBD80;&#xBD84; &#xD074;&#xB9AD;!](../.gitbook/assets/image%20%28220%29.png)

#### 8. 아래의 wsgi.py의 내용을 복사해 그대로 붙여넣습니다.

{% code-tabs %}
{% code-tabs-item title="wsgi.py" %}
```python
import os
import sys

path = '/home/자신의pythonanywhere이름/django_facebook'
if path not in sys.path:
    sys.path.append(path)

os.environ['DJANGO_SETTINGS_MODULE'] = 'main.settings'

from django.core.wsgi import get_wsgi_application
from django.contrib.staticfiles.handlers import StaticFilesHandler
application = StaticFilesHandler(get_wsgi_application())
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**4번째 줄**에 `자신의 python anywhere 이름` 부분을 올바르게 수정합니다. 7번에서 확인한 자신의 이름 잘 기억하고 계시죠?

![](../.gitbook/assets/image%20%28143%29.png)

#### 9. Save 후 뒤로가기를 누릅니다.

![](../.gitbook/assets/image%20%28141%29.png)

#### 10. Reload하여 모든 변경사항을 적용합니다.

![](../.gitbook/assets/image%20%287%29.png)

#### 11. reload 버튼 위의 자신의 web app 주소에 접속해봅니다.

![](../.gitbook/assets/image%20%286%29.png)

## 업데이트 된 내용을 다시 배포해보기

### 실습

#### 1. Pycharm terminal을 열고 다음과 같이 입력합니다.

git에 커밋을 한 후,

`git add -A`  
`git commit -m “Republish Test”`

github에 업로드해야합니다.

`git push -u origin master` \(왼쪽 명령이 작동하지 않을 경우 `git push origin master`\)

#### 2. [https://www.pythonanywhere.com](https://www.pythonanywhere.com) 에 로그입합니다.

#### 3. 상단에서 Dashboard탭에 접속합니다.

![](../.gitbook/assets/image%20%28130%29.png)

#### 4. $Bash를 클릭합니다.

![](../.gitbook/assets/image%20%28131%29.png)

#### 5. 터미널에 `cd django_facebook` 를 입력합니다.

#### 6. 이어서 `git pull origin master` 를 입력 후 자신의 git 아이디와 패스워드를 입력합니다. \(아이디가 이미 저장되어 있어서 패스워드만 요구할 경우도 있습니다.\)

#### 7. 웹탭에서 Reload하여 모든 변경사항을 적용합니다.

![](../.gitbook/assets/image%20%28210%29.png)

#### 8. reload 버튼 위의 자신의 web app 주소에 접속해봅니다.

![](../.gitbook/assets/image%20%28122%29.png)

