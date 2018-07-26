# Stage 1 - 다양한 스타일을 배워보자

## 다양한 스타일

지난 시간에 필수로 알아야하는 태그들과 스타일을 배웠습니다. 이번 시간에는 좀 더 다양한 스타일을 배워볼까요?

| 스타일 | 설 | 사용 예 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| font-size | 글자 크기 | `<div style=“font-size:40px;”>큰 글자</div>` |
| font-weight | 글자 굵기\(100, 200, …, 800\) | `<div style=“font-weight:800;”>진한 글자</div>` |
| text-align | 글자 정렬\(left, right, center\) | `<div style=“text-align:center;”>가운데 정렬</div>` |
| float | 개체 배치 방식\(띄우기 방식 설정\) | `<img src=“이미지 경고”><div style=“float:left;”>이미지 바로 옆에 배치</div>` |
| position | 개체 배치 방식\(절대좌표, 상대좌표 설정\) | `<div style=“position:absolute;top:50px;left:30px;”>정확히 원하는 위치로</div>` |
| z-index | 좌표방식으로 설정되었을 때, 개체의 위아래 우선순위를 설정 | `<div style=“position:absolute;top:50px;left:30px;z-index:300;”>A</div><div style=“position:absolute;top:52px;left:32px;z-index:310;”>B</div>` |
| display | 개체 레이아웃 제어 | `<div style=“display:inline-block;”>박스안 내용물</div>` |

## float

float은 개체를 공중에 띄웁니다.

![&#xD55C;&#xAE00;\(&#xC6CC;&#xB4DC;&#xD504;&#xB85C;&#xC138;&#xC11C;\)&#xC758; &#xBC30;&#xCE58; &#xBC29;&#xBC95;](../.gitbook/assets/image%20%28185%29.png)

한글로 치면, 가장 왼쪽의 나비모양에 해당하겠네요.

### 실습 {#practice-1}

타이핑을 생략하시려면 여기서부터 시작하세요.

```markup
<div style="width: 150px; height: 100px; background-color: yellow;">img here</div>
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.
</body>
```

![float: left;](../.gitbook/assets/image%20%28202%29.png)

![float: right;](../.gitbook/assets/image%20%2864%29.png)

left를 right으로도 바꿔보세요.

```markup
<div style="width: 150px; height: 100px; float: left; background-color: yellow;">img here</div>
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.
</body>
```

## clear

float의 문제는 의도치 않은 겹침문제가 발생할 수 있다는 것 입니다.

![&#xC8FC;&#xD669;&#xC0C9; &#xBC15;&#xC2A4;&#xC640; &#xBE68;&#xAC04;&#xC0C9; &#xBC15;&#xC2A4;&#xAC00; &#xACB9;&#xCE58;&#xACE0; &#xC788;&#xB2E4;.](../.gitbook/assets/image%20%28124%29.png)

빨간색 박스는 **float:right;** 을 통해 오른쪽에 띄운 상태입니다. 그런데 주황색 박스와 겹치고 있네요. 주황색 박스를 겹치지 않게 내리고 싶으면 어떻게 해야 할까요?

### 실습 {#practice-2}

이럴 때 clear를 사용합니다. 주황색 박스에 **clear:both;** 속성을 넣어보세요.

![clear:both](../.gitbook/assets/image%20%28118%29.png)

```markup
<div style="width: 150px; height: 100px; float: right; background-color: yellow;">img here</div>
의미없는 텍스트 의미없는 텍스트 의미없는 텍스트 의미없는 텍스트 의미없는 텍스트 의미없는 텍스트 의미없는 텍스트 의미없는 텍스트 의미없는 텍스트 의미없는 텍스트 의미없는 텍스트 의미없는 텍스트 의미없는 텍스트 의미없는 텍스트 의미없는 텍스트 
<div style="background-color: orange; clear:both;">다른 텍스트</div>
```

## position

공중에 개체를 띄울 수 있는 float 속성을 배우면서 레이아웃을 더 쉽게 짤 수 있게 되었습니다. 대부분의 경우는 float만으로 해결할 수 있지만, 간혹 좀 더 정교한 컨트롤이 필요할 때가 있습니다. 이럴 때는 position을 사용하기도 합니다.

### absolute, relative, fixed, static

**position**은 **absolute, relative, fixed, static**의 속성을 지정할 수 있습니다.

| 스타일 | 속성 | 설명 |
| --- | --- | --- | --- | --- |
| position | absolute | 절대 좌표를 기준으로 표시한다. |
|  | relative | 개체의 현재 위치로부터 상대좌표로 표시한다. |
|  | fixed | 항상 그 위치에 띄운다. |
|  | static | 기본 설정 |

position을 사용해본적이 없다면 이 설명만으로는 이해하기 어렵습니다. 지금부터 자세히 설명해드리겠습니다.

### 실습 - absolute {#practice-3}

타이핑을 생략하시려면 여기서부터 시작하세요.

```markup
<br><br><br>

<div style="width: 300px; height: 200px; background-color: blue; color: #fff;">A</div>

<div style="width: 200px; height: 150px; background-color: orange; color: #ffffff;">B</div>
```

개체를 서로 겹치게 하려면 지금까지 배운 방법으로는 float을 사용해야합니다. 그러나 float은 공중에 띄울뿐 위치에 대한 미세한 컨트롤은 어렵죠. 이럴 때는 **position:absolute;**을 이용해 개체의 절대 좌표를 지정할 수 있습니다.

![&#xC8FC;&#xD669;&#xC0C9; &#xBC15;&#xC2A4;&#xB294; position:absolute;&#xC774; &#xC9C0;&#xC815;&#xB41C; &#xC0C1;&#xD0DC;](../.gitbook/assets/image%20%2889%29.png)

```markup
<br><br><br>

<div style="width: 300px; height: 200px; background-color: blue; color: #fff;">A</div>

<div style="top: 35px; left: 40px; position: absolute; width: 200px; height: 150px; background-color: orange; color: #ffffff;">B</div>
```

position:abolute 속성을 지정하는 순간, top, left, right, bottom을 함께 지정할 수 있습니다. 이는 각각 맨 위, 맨 왼쪽, 맨 오른쪽, 맨 아래로부터 얼마만큼 떨어져 있나 정할 수 있게 해줍니다. 즉 좌표를 정하는 것처럼 특정 위치에 놓이게 할 수 있죠.

#### 다른 사용법

position의 relative, fixed 사용법은 Level Up 1에서 확인하실 수 있습니다.

