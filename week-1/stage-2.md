---
description: '이미지, 폼 등을 다루는 또 다른 태그도 배워볼까요?'
---

# Stage 2 - 이미지, 폼을 다루는 HTML tag를 배워보자

## 이미지, form 관련 태그 4종

| **태그** | **설명** | **사용 예** |
| --- | --- | --- | --- | --- |
| img | 이미지 파일을 넣습니다. | `<img src=“이미지 주소”>` |
| div | 사각형의 박스를 넣습니다. | `<div>내용물</div>` |
| input | 입력 필드를 만듭니다. e.g 제목 입력 | `<input type=“text” placeholder=“제목을 입력하세요” >` |
| textarea | 큰 입력 필드를 만듭니다. e.g 내용 입력 | `<textarea>내용을 입력하세요.</textarea>` |

### 태그들의 속성

태그에는 속성이 있습니다. 이미지를 넣는데, 그 이미지의 가로랑 세로 크기 정도는 정하고 싶을거 아니예요? 로그인 창의 아이디 입력필드에 '아이디를 입력해주세요'라는 힌트 글자를 넣어둘 수도 있겠죠. 이렇게 태그를 좀더 세밀하게 조정할 수 있는 기능이 속성입니다.

| **태그** | **속** | **설명** | **사용** |
| --- | --- | --- | --- | --- | --- | --- |
| input | type | 입력 필드의 종류를 선택한다. e.g 제목입력, 비밀번호 입력 | `<input type=“text” >` `<input type=“password” >` |
|  | value | 초기값을 설정한다. | `전화번호 <input type=“text” value=“010-” >` |
|  | readonly | 읽기 전용으로 설정해 수정불가능하게 만든다. | `<input type=“text” readonly >` |
| textarea | rows | 세로 줄수\(세로 크기와 관련\) | `<textarea rows=“13”></textarea>` |
|  | cols | 가로 줄수\(가로 크기와 관련\) | `<textarea cols=“50”></textarea>` |
| img | width, height | 가로 세로 크기 | `<img src=“이미지주소” width=“100px” height=“30px”>` |

{% hint style="info" %}
**속성과 css의 차이**

html이 요소를 결정하고 css가 크기, 모양 색 등을 결정한다고 했는데, 크기를 결정하는 html 속성이 있다는 말이 헷갈리지 않나요?

img 태그의 경우 width, height라는 가로와 세로 길이를 설정하는 속성을 사용할 수 있습니다. 이 속성을 사용하지 않아도 앞으로 배울 style을 사용하면, 마찬가지로 가로와 세로 길이를 설정할 수 있죠. 즉 모양과 크기를 결정하는 일부분은 속성으로 대체할 수 있는 부분도 있긴 합니다. 다만 그 사용이 제한되어 있어서 세밀한 디자인은 css를 통해야만 가능한거죠.
{% endhint %}

## 실습

아래 내용을 직접 타이핑해보고 또 변경해보면서 결과를 확인해봅시다.

```markup
<img width="100px"
 src="https://www.seoclerk.com/pics/523331-1e2qQI1490977998.jpg"><br>
html, css 대표 이미지

<div>로그인 해주세요!<br>
아이디 <input type="text" placeholder="아이디"><br>
비밀번호 <input type="password" placeholder="비밀번호">
</div>

코멘트 남기기<br>
<textarea cols="30" rows="10"></textarea>
```

![&#xACB0;&#xACFC;&#xBB3C;](../.gitbook/assets/image%20%283%29.png)

