# Stage 4 - 장고 프로젝트를 실행해보자

## 장고 프로젝트 Setting

### 1. 메뉴 -&gt; View -&gt; Tool Windows -&gt; Terminal을 클릭합니다.

![](../.gitbook/assets/image%20%28222%29.png)

### 2. 하단에 Terminal이 표시됩니다.

terminal을 클릭하고 `python - -version` 을 입력합니다. 이어서 `pip list` 를 입력합니다.

![](../.gitbook/assets/image%20%2853%29.png)

\* **이** **정보들이** **제대로** **나오지** **않을** **시에** **Python** **설치문제, Pycharm** **설치문제, PC** **문제** **등** **다양한** **원인이** **있을** **수** **있습니다.** **리더에게** **문의해주세요.**

### 3. 터미널에 `django-admin startproject main .` 을 입력후 Enter

위 명령에서 **마지막 . \(온점\)**을 빼먹지 마세요. 이어서 `python manage.py startapp facebook` 을 입력해줍니다.

![](../.gitbook/assets/image%20%2878%29.png)

### 3-1. 위의 입력 후 아무런 로그가 출력되지 않는게 정상입니다.

좌측 위 Project 탭을 새로고침하여 **facebook** 폴더와 **main** 폴더가 잘 만들어졌는지 확인합니다.

![](../.gitbook/assets/image%20%28206%29.png)

### 4. main폴더를 열고 settings.py를 실행해줍니다.

![](../.gitbook/assets/image%20%2895%29.png)

### 5. 33번째 줄 주변에서 INSTALLED\_APPS라는 문자를 찾습니다.

이후 39번째 줄 아래 캡쳐화면처럼 **‘facebook’**을 입력해줍니다.

![](../.gitbook/assets/image%20%28134%29.png)

  
장고 프로젝트 Setting을 완료했습니다. 지금부터는 장고프로젝트를 **실행**해보겠습니다.

## 장고 프로젝트 실행

### 1. 메뉴 -&gt; run -&gt; edit configurations 실행합니다.

![](../.gitbook/assets/image%20%28211%29.png)

### 2. + 버튼을 클릭한 후 Python을 선택해줍니다.

![](../.gitbook/assets/image%20%28224%29.png)

### 3. 아래 캡쳐화면과 똑같이 설정해줍니다.

![](../.gitbook/assets/image%20%28148%29.png)

### 4. 실행 버튼을 클릭합니다. 일반적으로 우측 상단에 있습니다.

![](../.gitbook/assets/image%20%28199%29.png)

**하단** **터미널에** `http://127.0.0.1:8000/` **에** **글자가** **표시되면** **잘** **실행된** **것** **입니다.**

![](../.gitbook/assets/image%20%28159%29.png)

### 5. 인터넷 브라우저를 열어 `http://127.0.0.1:8000`에 접속해봅니다.

![](../.gitbook/assets/image%20%2832%29.png)

{% hint style="success" %}
## 복잡했죠?

### 원래는 일주일이 족히 걸리는 서버 Setting을 파이썬 장고가 30분내로 할 수 있도록 도와주기 때문입니다. 이후 스터디에서 더이상의 서버 Setting은 없습니다.

**참고\)** **아래의** **순서로** **진행하였습니다.**

1. **장고** **설치**  Pycharm 설치 후 딱 1번만 하시면 됩니다.
2. **장고** **프로젝트** **생성**  새프로젝트를 할 때마다 하셔야 합니다. 즉 실습기간 동안은 1번만 하시면 됩니다.
3. **장고** **프로젝트** **Setting**  프로젝트를 만들었으면 곧 바로 1번 하셔야 합니다.
4. **장고** **프로젝트** **실행**  프로젝트 셋팅이 끝난 후 1회만 하시면 됩니다.  **즉** **대부분의** **작업은** **첫날** **단** **한번만** **하시면** **됩니다.**
{% endhint %}

## 실습

지금부터 Hello World!를 장고에서 띄워보겠습니다.

### 1. 좌측 Project에서 facebook 폴더 내에 templates 폴더 생성. 폴더 생성 후 play.html 생성

![](../.gitbook/assets/image%20%28204%29.png)

### 2. facebook 폴더 내 views.py를 다음과 같이 수정

![](../.gitbook/assets/image%20%28149%29.png)

### 3. main폴더 내 urls.py를 다음과 같이 수정

![](../.gitbook/assets/image%20%28188%29.png)

### 4. play.html 내용을 Hello World!로 채우고 `http://127.0.0.1:8000/play/` 접속해보기

![](../.gitbook/assets/image%20%2849%29.png)

