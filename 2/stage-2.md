# Stage 2 - 레이아웃을 직접 만들어보자

## 온전한 html의 구조

![&#xC628;&#xC804;&#xD55C; html&#xC758; &#xAD6C;&#xC870;](../.gitbook/assets/image%20%281%29.png)

그동안은 html, head, body 같은 태그들을 사용한 적이 없죠. 학습을 효율적으로 하기 위해 간소화해서 스터디를 진행하였습니다. 그러나 웹에 올리는 실제 문서는 위와 같은 형식으로 작성해야 해요.

웹에 올린다는 것은 남들이 보게 한다는 뜻이고, 사람뿐만 아니라 검색엔진\(네이버, 구글\) 등이 자료를 수집해 간다는 것을 의미합니다. 그러려면 그들이 사용하는 규칙에 따라 페이지를 작성할 필요가 있겠죠. 이에 해당하는 것이 위에 이미지에 보이는 구조입니다.

### head

해당 페이지에 대한 정보들을 담습니다. head 안에 있는 **title은 브라우저의 탭의 이름**에 해당합니다.

![&amp;lt;title&amp;gt;Stage 2 - &#xB808;&#xC774;&#xC544;&#xC6C3;&#xC744; &#xC9C1;&#xC811; &#xB9CC;&#xB4E4;&#xC5B4;&#xBCF4;&#xC790;&amp;lt;/title&amp;gt;](../.gitbook/assets/image%20%28183%29.png)

![&#xC2E4;&#xC81C; &#xC18C;&#xC2A4;&#xCF54;&#xB4DC;](../.gitbook/assets/image%20%28127%29.png)

실제로 이 페이지의 소스코드를 살펴보면 title이 위와 같이 정의되어 있습니다. \(data-react-helmet은 무시해도, 쓰지 않아도 상관없습니다.\) title 이외에 페이지에 대한 설명, 키워드 등 개괄적인 정보를 담을 수도 있습니다.

### body

페이지에서 보여줄 내용들이 이곳에 작성됩니다. 저희는 그동안 html을 사용해 페이지를 만들 때, 이 body안에 들어갈 내용만 작성했던 거죠.

## 스타일 적용법

### 인라인 스타일

첫주부터 지금까지 사용한 스타일 방식입니다. 쉽게 사용할 수 있는 대신, 스타일 내용이 길어지면 보기 불편해지는 단점이 있었죠.

![Inline Style](../.gitbook/assets/image%20%2810%29.png)

### 내부 스타일시트

저희가 앞으로 애용할 방식입니다. 정리도 쉽고 사용법도 쉬워 초보자에게 안성맞춤인 방식입니다.

![Internal Style Sheet](../.gitbook/assets/image%20%2867%29.png)

여기서 주목할 점은 **class="test\_class"**입니다. 저 말은, test\_class라는 정의를 **&lt;style&gt;&lt;/style&gt;** 태그 사이에서 찾아 적용하겠다는 것을 의미합니다. **.test\_class**에서 **. \(온점\)**은 클래스를 의미하며, **class="test\_class"라 정의된 모든 개체의 배경색은 파란색으로 지정**됩니다.

원한다면 **.blue\_box**라는 이름을 지어주고 그 의미에 맞게 사용할 수도 있어 **프로젝트가 커질 수록 유용한 방식**입니다.

### 외부 스타일시트

저희가 이번 스터디에서 사용하지는 않습니다. 그러나 **실제 프로젝트에서는 자주 사용**되는 방식으로 알아둘 필요는 있습니다. 파일을 별개로 html파일과 css파일 2개를 구성합니다. 그리고 html 파일에서 css 파일을 불러오는 식으로 사용합니다. 그외 사용법은 내부 스타일시트와 유사합니다.

![test.html](../.gitbook/assets/image%20%28179%29.png)

![style.css](../.gitbook/assets/image%20%28106%29.png)

## 2단 레이아웃

2000년대 초반까지만 해도 모든 웹사이트가 천편일률 적으로 아래와 같이 생긴적이 있었죠.

![2&#xB2E8; &#xB808;&#xC774;&#xC544;&#xC6C3; &#xAD6C;&#xC131;](../.gitbook/assets/image%20%2815%29.png)

![&#xD398;&#xC774;&#xC2A4;&#xBD81;&#xC758; 2&#xB2E8; &#xAD6C;&#xC131;](../.gitbook/assets/image%20%2813%29.png)

2단 구성은 안정적인 느낌을 주는 형태로 페이스북과 같은 유명서비스에서도 유용하게 쓰이고 있습니다. 최근에는 Left가 고정되기 보다는 필요시에만 보여지거나 Right을 보여주는 추세입니다.

구성의 쓰임새는은 차치하더라 배울 필요가 있습니다. 레이아웃을 구성하는 html, css 연습을 하기에 딱 알맞기 때문입니다.

### 실습

```markup
<div class="header">Header</div>
<div class="left">Left</div>
<div class="content">Content</div>
<div class="footer">Footer</div>
```

```markup
<style>
    .header {
        background-color: blue;
        color: #fff;
    }
    .left {
        background-color: orange;
        color: #fff;
        float: left;
        width: 200px;
        height: 300px;
    }
    .content {
        background-color: red;
        color: #fff;
        height: 500px;
        margin-left: 200px;
    }
    .footer {
        background-color: green;
        color: #fff;
    }
</style>
```

위 코드를 타이핑해보고 구조를 이해해보세요. 그리고 다음과 같은 작업들을 해보세요. 이해하는데 큰 도움이 될 겁니다.

1. **.header, .footer에** **height을** **넣어보기**
2. **.left, .content의** **height을** **변경해보기**
3. **.left의** **float:left를** **position:absolute로** **변경해보기**
4. **.content에** **margin-left를** **수정해보기**
5. **margin, padding을** **넣어보기**

