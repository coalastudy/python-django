---
description: '이제 모양, 크기, 색 등의 스타일을 결정하는 css를 배워볼까요?'
---

# Stage 4 - 크기, 색을 다루는 style을 배워보자

## css의 기본 형태 \(inline 방식\)

html: 요소를 다룬다  
css: 스타일을 다룬다

계속 반복해서 말씀드렸기 때문에 이제는 잘 아실거예요. 지금부터는 스타일을 다루는 css를 배워볼게요.

![css&#xC758; &#xAE30;&#xBCF8; &#xD615;&#xD0DC; - inline &#xBC29;&#xC2DD;](../.gitbook/assets/image%20%2865%29.png)

![&#xC608;&#xC81C;](../.gitbook/assets/image%20%2856%29.png)

## 크기, 색 스타일

| **스타일** | **설명** | **사용** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| color | 글자색상 지정 | `<div style=“color:red”>글자색이 빨간색</div>` |
| background-color | 배경색상 지정 | `<div style=“background-color:red”>박스안 내용물</div>` |
| border | 테두리 지정 | `<div style=“border:3px solid #0a0a0a”>박스안 내용물</div>` |
| border-radius | 테두리의 둥근 정도를 설정 | `<div style=“border:3px solid #0a0a0a; border-radius: 12px;”>박스안 내용물</div>` |
| width, height | 각각 가로, 세로 길이 | `<div style=“width:100px; height:50px; background-color:red;”>박스안 내용물</div>` |
| margin | 외부 여백 지정 | `<div style=“margin: 30px; background-color:red;”>박스안 내용물</div>` |
| padding | 내부 여백 지정 | `<div style=“padding: 40px; background-color:red;”>박스안 내용물</div>` |

### margin, padding

![margin&#xB3C4; &#xAC19;&#xC740; &#xBC29;&#xC2DD;&#xC73C;&#xB85C; &#xC124;&#xC815;&#xD560; &#xC218; &#xC788;&#xB2E4;.](../.gitbook/assets/image%20%287%29.png)

![padding&#xC758; &#xB124; &#xBC29;&#xD5A5;&#xC744; &#xC124;&#xC815;&#xD558;&#xB294; &#xBC29;&#xBC95;](../.gitbook/assets/image%20%2832%29.png)

## 색상 선택기

background-color: \#ff0000;  
color: red;  
위와 같이 색상을 표현하고 있습니다.

![&#xB124;&#xC774;&#xBC84;&#xC758; &#xC0C9;&#xC0C1;&#xCF54;&#xB4DC;&#xD45C;](../.gitbook/assets/image%20%2863%29.png)

원하는 색을 찾을 때 네이버에서 쉽게 찾을 수 있어요. css에서는 색상을 지정하는 여러가지 방법이 있지만, 가장 많이 쓰이는 방법은 아래와 같이 세가지 방식입니다.

### 16진수

**\#FF0000**처럼 16진수로 된 6자리 코드표\(경우에 따라 8자리\)를 사용해 색을 표현합니다.

### RGB

**color: \#FF00000**은 **color: rgb\(255, 0, 0\)**으로 대체할 수도 있습니다.

### 색상 이름

**color: red**라고 표현할 수도 있습니다. 자주 쓰이는 색상인 red, white, black, magenta, ...은 색상의 이름으로도 지정할 수 있지요. 그러나 세밀한 색 표현이 제한적으로만 쓰입니다.

## 실습

실생활에서는 m, cm 같은 단위를 많이 사용하죠? 코드에서 자주 보이는 **px**은 웹에서 가장 많이 쓰이는 단위입니다. 픽셀이라는 말을 많이 들어보셨을 거에요. **pixel\(픽셀\)**은 간단하게 **색을 표현하는 점 하나**라고 생각하시면 됩니다. pixel 줄여 px라 표현하고, css에서는 `width: 100px;` 와 같은 방식으로 크기를 나타냅니다.

{% hint style="info" %}
px 말고도 pt, %, ex, em 등 여러 종류의 단위가 있습니다. 그러나 초보자가 가장 명확하게 이해하고 쉽게 사용할 수 있는 것은 픽셀 뿐이죠. 최근 디바이스\(컴퓨터, 스마트폰 등\)의 크기가 다양해지며 픽셀이 아닌 다른 단위를 사용하는 개발자들도 많이 있습니다.

상황에 맞는 효율적인 크기 표현 방식이 있습니다. 인쇄용, 웹용, 큰 모니터, 작은 모니터 등 등 여러 상황이 있고 목적에 맞는 단위 설정이 중요합니다. 픽셀은 그 중 가장 무난한 방법이라 할 수 있겠네요.
{% endhint %}

```markup
<div style="background-color:green; border: 5px solid #0a0a0a; border-radius:12px; width: 100px; height: 200px; margin: 15px; padding: 40px;">
박스 안 내용물
</div>
```

![](../.gitbook/assets/image%20%2836%29.png)

{% hint style="info" %}
**스타일링이 좀 어렵다구요?**

네, 스타일링이 마냥 쉬운건 아니예요. 그러나 그건 스타일링 자체의 난이도가 높다기 보다는 익숙하지 않은 탓 입니다. **"웹의 화가가 되어보자"**라는 1주차의 제목이 기억 나시나요? 화가가 되려면 점, 선, 면을 수만번 그리며 손의 작은 근육과 큰 근육들을 고르게 발달 시키는 지루한 과정이 따라오죠.

웹 디자인도 마찬가지로 어느정도는 인내심을 가지고 지루한 반복작업들을 통해 스타일링 근육을 길러야 한답니다. 지금 당장 잘 안된다고해도 상관없어요. 차분하게 실습하다보면 어느새 실력이 크게 상승해 있을거예요!
{% endhint %}

