# Stage 3 - 배포 준비

## 준비사항

### 깃허브 회원가입

https://github.com/에 접속하여 회원가입해주세요.

### 파이썬애니웨어 회원가입

[https://www.pythonanywhere.com](https://www.pythonanywhere.com)에 회원가입 해주세요.

### git 설치

#### 1. [https://git-scm.com에](https://git-scm.com에) 접속하여 git을 설치합니다.

![](../.gitbook/assets/image%20%2880%29.png)

![](../.gitbook/assets/image%20%28134%29.png)

#### 2. pycharm을 종료하고 다시 실행해주세요.

## 배포를 위한 코드 수정

배포를 위해 일부 코드를 수정하겠습니다.

### 실습

#### 1. settings.py를 열고 28번째 주변에서 다음 코드를 수정합니다.

```python
ALLOWED_HOSTS = ['localhost', '127.0.0.1', '.pythonanywhere.com']
```

 위 코드는 pythonanywhere 서버에서 작동할 수 있도록 허용해줍니다. 장고의 최소한의 보안 중 하나라고 보시면 됩니다.

#### 2. 스마트폰에서 제대로 된 모바일뷰를 보여주기 위해 모든 html 파일 상단에 다음 부분을 추가합니다.

아래 코드 예시처럼 3번째 줄에 있는 `<meta name="viewport" ~>`만 추가해주시면 됩니다.

{% code-tabs %}
{% code-tabs-item title="예시" %}
```markup
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, user-scalable=no">
    <title>뉴스피드</title>
</head>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 이 부분을 추가하지 않으면 모바일 접속시 화면이 축소된 상태로 보여집니다.

![2&#xBC88; &#xC791;&#xC5C5; &#xC548;&#xD588;&#xC744; &#xB54C; &#xC2A4;&#xB9C8;&#xD2B8;&#xD3F0; &#xD654;&#xBA74;](../.gitbook/assets/image%20%2876%29.png)

![2&#xBC88; &#xC791;&#xC5C5; &#xD6C4; &#xC2A4;&#xB9C8;&#xD2B8;&#xD3F0; &#xD654;&#xBA74;](../.gitbook/assets/image%20%28166%29.png)

#### 3. urls.py를 열고 모든 주소규칙이 **`/`** 로 끝나도록 정비합니다.

기본적으로 urls.py 안에 있는 주소규칙, 즉 `'주소'`는 모두 `'주소/'`의 형태로 만들어주어야 합니다.

![](../.gitbook/assets/image%20%28219%29.png)

## 간단한 git 사용법

우리는 방대한 문서파일을 관리하기 위해 주로 구글 드라이브를 사용합니다. 안정적으로 보관할 수 있고, 언제 올렸는지 언제 작업한 파일인지 상태를 관리할 수도 있기 때문입니다.

소스코드는 이런 관리작업이 더 중요합니다. git은 코드 파일들을 관리하는 가장 좋은 시스템입니다. 그러나 우리는 git을 이렇게까지 상세하게 알 필요는 없습니다. 당연히 아래 명령어를 암기할 필요도 없습니다. 간단하게 확인만 하고 넘어갑시다.

| **명령어** | **용도** |
| :--- | :--- |
| git init | git을 setting합니다. 한 프로젝트마다 한번씩만 실행하면 됩니다. |
| git config | git 사용자 정보를 설정합니다.  git config --global user.name “Dg”  git config --global user.email my@email.com |
| git add -A | 현재까지 작업한 모든 내용을 저장 예정 목록에 올려달라는 명령입니다.  어떤 작업을 했는지 체크하는 행위입니다. |
| git commit -m “메시지” | 저장 예정 목록에 있는 모든 깃 변경사항을 로컬에 저장합니다. 메시지를 입력해주면 어떤 작업을 했는지 기록할 수 있습니다. **아직** **깃허브에는** **올리지** **않은** **상태입니다.**  여태까지 한 작업이 무슨 작업이었는지 시간, 변경내용 등을 기록합니다. |
| git list | 그동안의 git 내역을 확인합니다.이 작업은 구글드라이브에서 파일 수정일을 확인하는 것과 비슷합니다. |
| git remote add origin 주소 | github 저장소와 내 로컬 깃을 연결합니다.  git remote add origin [https://gi~~복사한git주소~~facebook.git](https://xn--gi~~git~~facebook-3522ejx3ad9dnu5ch58c.git)  이 작업은 구글드라이브 아이디를 연결하는 것과 비슷합니다. |
| git push -u origin master | 최신 작업내역을 **github에** **새로** **올려줍니다.** 즉 업데이트 작업입니다.  이 작업은 구글드라이브에 파일을 다시 올리는 것과 비슷합니다.  git push -u origin master |

만약 소스코드를 제대로 관리하고 싶다면, 프로젝트를 좀 더 체계적으로 관리하고 싶다면 반드시 git을 익히셔야합니다. **git을 모르고 개발자라 칭할 수 있는 사람은 없을 정도입니다.** git을 좀 더 쉽게 사용할 수 있도록 도와주는 source tree라는 프로그램도 있습니다. 이에 대해서는 Level Up 1 에서 배워보겠습니다.

## git 저장소 생성하고 저장하기

내 소스코드 작업 내역을 저장할 수 있도록 git을 세팅해보겠습니다.

### 실습

#### 1. Pycharm terminal을 열고 다음과 같이 입력합니다.

`git init`  
`git config --global user.name “Dg”`  
`git config --global user.email my@email.com`

2. 아래의 내용을 복사합니다.

{% code-tabs %}
{% code-tabs-item title=".gitignore" %}
```text
*.pyc
*~
__pycache__
myvenv
venv
django_venv
django_env
db.sqlite3
/static
.DS_Store
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### 3. manage.py와 같은 폴더에 .gitignore라는 파일을 만들고 복사한 내용을 붙여 넣습니다.

즉 프로젝트 최상단 폴더 바로 밑 위치해야합니다. 저희 같은 경우는 my\_facebook이 되겠죠.

#### 4. 계속하여 터미널에 다음 두 명령을 입력합니다.

`git add -A`  
`git commit -m “My Facebook app”`

![commit &#xBA85;&#xB839;&#xC5C5; &#xC785;&#xB825; &#xC774;&#xD6C4;. &#xC2DC;&#xC810;&#xC5D0; &#xB530;&#xB77C; &#xCD9C;&#xB825;&#xACB0;&#xACFC;&#xAC00; &#xC870;&#xAE08; &#xB2E4;&#xB97C; &#xC218; &#xC788;&#xC74C;.](../.gitbook/assets/image%20%28193%29.png)

## github 저장소 생성하기

구글에 첫 로그인을 했을 때 구글 드라이브를 생성하는 것과 같은 작업입니다.

### 실습

#### 1. 로그인 후 우측 상단의 + 버튼을 클릭합니다. 여기서 New repository를 클릭합니다.

![](../.gitbook/assets/image%20%28260%29.png)

#### 2. repository name을 설정합니다. 다른 설정은 캡쳐와 동일하게 해주세요.

name은 아무 이름으로 지정해 상관없으나 실습의 편의성을 위해 django\_facebook으로 통일합니다.

준비가 완료되면 하단의 **Create repository**를 클릭해주세요.

![](../.gitbook/assets/image%20%28167%29.png)

3. HTTPS 탭을 클릭하고 git 주소를 복사합니다.

![](../.gitbook/assets/image%20%28126%29.png)

## github에 파일 올리기

구글 드라이브로 치면 파일을 업로드하는 것과 같습니다.

### 실습

#### 1. 다시 Pycharm terminal을 열고 다음과 같이 입력합니다.

`git remote add origin https://gi~~복사한git주소~~facebook.git`  
`git push -u origin master`

#### 2. 자신의 github 아이디 / 비밀번호를 입력하세요.

![](../.gitbook/assets/image%20%28198%29.png)

