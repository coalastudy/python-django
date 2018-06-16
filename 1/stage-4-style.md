---
description: '이제 모양, 크기, 색 등의 스타일을 결정하는 css를 배워볼까요?'
---

# Stage 4 - 크기, 색을 다루는 style을 배워보자

## css의 기본 형태 \(inline 방식\)

html: 요소를 다룬다  
css: 스타일을 다룬다

계속 반복해서 말씀드렸기 때문에 이제는 잘 아실거예요. 지금부터는 스타일을 다루는 css를 배워볼게요.

![css&#xC758; &#xAE30;&#xBCF8; &#xD615;&#xD0DC; - inline &#xBC29;&#xC2DD;](../.gitbook/assets/image%20%2821%29.png)

![&#xC608;&#xC81C;](../.gitbook/assets/image%20%2817%29.png)

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

![margin&#xB3C4; &#xAC19;&#xC740; &#xBC29;&#xC2DD;&#xC73C;&#xB85C; &#xC124;&#xC815;&#xD560; &#xC218; &#xC788;&#xB2E4;.](../.gitbook/assets/image%20%282%29.png)

![padding&#xC758; &#xB124; &#xBC29;&#xD5A5;&#xC744; &#xC124;&#xC815;&#xD558;&#xB294; &#xBC29;&#xBC95;](../.gitbook/assets/image%20%2810%29.png)

## 실습

실생활에서는 m, cm 같은 단위를 많이 사용하죠? 코드에서 자주 보이는 **px**은 웹에서 가장 많이 쓰이는 단위입니다. 픽셀이라는 말을 많이 들어보셨을 거에요. **pixel\(픽셀\)**은 간단하게 **색을 표현하는 점 하나**라고 생각하시면 됩니다. pixel 줄여 px라 표현하고, css에서는 `width: 100px;` 와 같은 방식으로 크기를 나타냅니다.

{% hint style="info" %}
px 말고도 pt, %, ex, em 등 여러 종류의 단위가 있습니다. 그러나 초보자가 가장 명확하게 이해하고 쉽게 사용할 수 있는 것은 픽셀 뿐이죠. 최근 디바이스\(컴퓨터, 스마트폰 등\)의 크기가 다양해지며 픽셀이 아닌 다른 단위를 사용하는 개발자들도 많이 있습니다.

상황에 맞는 효율적인 크기 표현 방식이 있습니다. 인쇄용, 웹용, 큰 모니터, 작은 모니터 등 등 여러 상황이 있고 목적에 맞는 단위 설정이 중요합니다. 픽셀은 그 중 가장 무난한 방법이라 할 수 있겠네요.
{% endhint %}

```markup
<div style="background-color:green; border: 5px solid #0a0a0a; border-radius:12px; width: 100px; height: 200px; margin: 15px; padding: 40px;">박스 안 내용물</div>
```

![](../.gitbook/assets/image%20%2812%29.png)

