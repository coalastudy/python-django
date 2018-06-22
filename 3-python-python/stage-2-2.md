# Stage 2 -장고로 파이썬 깨닫기 \(2\)

## list

### list란 무엇인가?

리스트란 온갖 데이터를 담아두는 표라고 생각하시면 됩니다. 한 예로, 게시글을 담아두는 리스트가 있을 수 있고 그 리스트가 게시판이라 볼 수 있죠.

![list](../.gitbook/assets/image%20%2856%29.png)

사용법은 **\[ \]안**에 **,** \(콤마\)로 구분하여 여러 자료들을 집어 넣기만 하면됩니다.

숫자, 문자 등 온갖 자료를 넣을 수 있고 심지어 또 다른 리스트도 넣을 수 있습니다. 자세한 사용법은 Stage3에서 익힐 예정이니 지금은 간단하게 살펴봐요.

![&#xC218;&#xC900;&#xC774; &#xB192;&#xC544;&#xC838; &#xC601;&#xD654; &#xB9AC;&#xC2A4;&#xD2B8;&#xB97C; &#xB9CC;&#xB4E4; &#xC218; &#xC788;&#xB2E4;&#xBA74; &#xC774;&#xB807;&#xAC8C; &#xC0AC;&#xC6A9;&#xD560; &#xC218; &#xC788;&#xACA0;&#xC8E0;.](../.gitbook/assets/image%20%2847%29.png)

### 실습

리스트가 장고에서 어떻게 쓰이는지도 확인해봐야겠죠?

{% code-tabs %}
{% code-tabs-item title="views.py" %}
```text
17page list viewspy
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="play2.html" %}
```text
17page play2 html

```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### 결과 확인

![127.0.0.1:8000/play2](../.gitbook/assets/image%20%2867%29.png)

계속 발전되는 play2를 보실 수 있습니다.

## 함수

### 함수란 무엇인가?

함수는 코드뭉치라 보시면 됩니다. 길게 짜둔 코드가 있는데 다른 프로그램에서 또 그 구문을 실행해야 한다면, 전체 복사 후 붙여넣기 했었죠. 함수는 그런 구문들에 이름을 붙여두고, 다음에 그 이름만 입력하면 똑같은 기능을 수행하게 도와줍니다.

![&#xD615;&#xC2DD;](../.gitbook/assets/image%20%2859%29.png)

### 예시

![](../.gitbook/assets/image%20%2880%29.png)

그동안 작업했던 views.py 안에 있는 play, play2가 기억나시나요? 이 역시 함수입니다.

play의 함수의 경우, 최도근이라는 변수를 가지는 한편 **play.html을 띄워주는 기능을 수행**하는데요. 이렇게 미리 만들어두고 **play라고 이름을 붙여** urls.py에서 `127.0.0.1:8000/play`라는 주소와 연결할 때 다시 사용된 것이죠.

{% hint style="info" %}
### print\(\)도 역시 함수입니다.

화면에 글자를 띄우는 기능은 굉장히 자주 사용됩니다. print라는 함수를 만들고 글자를 출력하는 기능을 코드뭉치로 정리해두면 나중에 또 사용할 수 있게 되는거죠.

`print(‘Hello World!’) # 누군가가 print의 코드를 미리 짜둠`
{% endhint %}

