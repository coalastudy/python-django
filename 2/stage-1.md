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

![&#xD55C;&#xAE00;\(&#xC6CC;&#xB4DC;&#xD504;&#xB85C;&#xC138;&#xC11C;\)&#xC758; &#xBC30;&#xCE58; &#xBC29;&#xBC95;](../.gitbook/assets/image%20%28149%29.png)

한글로 치면, 가장 왼쪽의 나비모양에 해당하겠네요.

![float: left;](../.gitbook/assets/image%20%2824%29.png)

![float: right;](../.gitbook/assets/image%20%2844%29.png)

```markup
<style>
    .img {
        width: 150px;
        height: 100px;
        float: left;
        background-color: yellow;
     }
</style>

<div class="img">img here</div>
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.
</body>
```

### clear

float의 문제는 의도치 않은 겹침문제가 발생할 수 있다는 것 입니다.

![&#xC8FC;&#xD669;&#xC0C9; &#xBC15;&#xC2A4;&#xC640; &#xBE68;&#xAC04;&#xC0C9; &#xBC15;&#xC2A4;&#xAC00; &#xACB9;&#xCE58;&#xACE0; &#xC788;&#xB2E4;.](../.gitbook/assets/image%20%2883%29.png)

빨간색 박스는 **float:right;** 을 통해 오른쪽에 띄운 상태입니다. 그런데 주황색 박스와 겹치고 있네요. 주황색 박스를 겹치지 않게 내리고 싶으면 어떻게 해야 할까요?

이럴 때 clear를 사용합니다. 주황색 박스에 **clear:both;** 속성을 넣어보세요.

![clear:both;](../.gitbook/assets/image%20%2871%29.png)

```markup
<style>
    .img {
        width: 150px;
        height: 100px;
        float: right;
        border: 2px solid red;
    }
    .box {
        background-color: orange;
        clear: both;
    }
</style>
<body>
    <div class="img">img here</div>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
    <div class="box">다른 텍스트</div>
</body>
```

## position

공중에 개체를 띄울 수 있는 float 속성을 배우면서 레이아웃을 더 쉽게 짤 수 있게 되었습니다. 대부분의 경우는 float만으로 해결할 수 있지만, 간혹 좀 더 정교한 컨트롤이 필요할 때가 있습니다. 이럴 때는 position을 사용하기도 합니다.

**position**은 **absolute, relative, fixed, static**의 속성을 지정할 수 있습니다.

| 스타일 | 속성 | 설명 |
| --- | --- | --- | --- | --- |
| position | absolute | 절대 좌표를 기준으로 표시한다. |
|  | relative | 개체의 현재 위치로부터 상대좌표로 표시한다. |
|  | fixed | 항상 그 위치에 띄운다. |
|  | static | 기본 설정 |

position을 사용해본적이 없다면 이 설명만으로는 이해하기 어렵습니다. 지금부터 자세히 설명해드리겠습니다.

### absolute

개체를 서로 겹치게 하려면 지금까지 배운 방법으로는 float을 사용해야합니다. 그러나 float은 공중에 띄울뿐 위치에 대한 미세한 컨트롤은 어렵죠. 이럴 때는 **position:absolute;**을 이용해 개체의 절대 좌표를 지정할 수 있습니다.

![&#xC8FC;&#xD669;&#xC0C9; &#xBC15;&#xC2A4;&#xB294; position:absolute;&#xC774; &#xC9C0;&#xC815;&#xB41C; &#xC0C1;&#xD0DC;](../.gitbook/assets/image%20%2874%29.png)

```markup
<style>
    .box1 {
        width: 300px;
        height: 200px;
        background-color: blue;
        color: #fff;
    }

    .box2 {
        top: 35px;
        left: 40px;
        position: absolute;
        width: 200px;
        height: 150px;
        background-color: orange;
        color: #fff;
    }
</style>
<div class="box1">A</div>
<div class="box2">B</div>
```

position:abolute 속성을 지정하는 순간, top, left, right, bottom을 함께 지정할 수 있습니다. 이는 각각 맨 위, 맨 왼쪽, 맨 오른쪽, 맨 아래로부터 얼마만큼 떨어져 있나 정할 수 있게 해줍니다. 즉 좌표를 정하는 것처럼 특정 위치에 놓이게 할 수 있죠.

#### z-index

이때 만약 주황색 B보다 파란색 A가 중요하다고 판단되면, z-index 속성을 통해 순서를 바꿀 수 있습니다.  
박스 A에 z-index: 1000이라 하고, 박스 B에 z-index:999라 하면, z-index 값이 높은 A가 더 위에 올라오게 되고, B는 가려지게 되죠. z-index는 0~9999 사이의 값을 사용할 것을 권장합니다.

```markup
<style>
    .box1 {
        width: 300px;
        height: 200px;
        background-color: blue;
        color: #fff;
        position: absolute;
        z-index: 1000;
    }

    .box2 {
        top: 35px;
        left: 40px;
        position: absolute;
        width: 200px;
        height: 150px;
        background-color: orange;
        color: #fff;
        z-index: 999;
    }
</style>
```

### relative

absolute을 설정하면 **top, bottomm right, left**는 **맨 위/아래/오른쪽/왼쪽**이 기준이 됩니다. 이와는 조금 다르게 relative를 설정하면, 현재 개체가 놓인 위치 그 자체가 기준이되는 거죠.

### fixed

absolute과 똑같은 기준을 사용합니다. 다만 스크롤을 움직여서 창이 보고 있는 화면이 바뀌어도 해당 좌표에 고정된 개체가 따라옵니다. 뉴스 기사를 읽다보면 오른쪽 아래에 **'맨 위로'**라는 버튼이 계속 떠 있는 것을 볼 수 있는데요. 이 같은 경우 fixed로 고정해두어 항상 그 자리에 위치하게끔 설정해둔 것 이랍니다.

![&#xC77C;&#xBC18;&#xC801;&#xC73C;&#xB85C; &#xB9E8;&#xC704;&#xB85C; &#xBC84;&#xD2BC;&#xC740; &#xD56D;&#xC0C1; &#xADF8;&#xC790;&#xB9AC;&#xC5D0; &#xACE0;&#xC815;&#xB418;&#xC5B4; &#xC788;&#xB2E4;.](../.gitbook/assets/image%20%28200%29.png)

## dispaly

이번에는 레이아웃의 형태를 결정하는 display를 배워보겠습니다. 말이 조금 어려운데요, 정의에 신경쓸 필요 없이 실제로 어떻게 동작하는지를 보면 이해가 쉽습니다.

### display:block

![display:block](../.gitbook/assets/image%20%28133%29.png)

display 설정을 안했을때 해당되는 기본 설정입니다. 평소 박스를 그리는 방식과 일치합니다. 박스하나가 한 줄을 통째로 차지하게 되죠.

### display:inline

![display:inline](../.gitbook/assets/image%20%28164%29.png)

마치 박스가 글자처럼 변합니다. 이때는 width, height 같이 블럭의 크기를 지정하는 속성들이 무시됩니다. 글자와 똑같은 상태가 되니까요.

### display:inline-block

![display:inline-block](../.gitbook/assets/image%20%28125%29.png)

박스처럼 부피를 갖으면서 동시에 글자처럼 한줄에 함께 표시될 수 있는 방식입니다. 잘 사용한다면 레이아웃을 만드는데 큰 도움이 됩니다.

### display:none

![display:none](../.gitbook/assets/image%20%2831%29.png)

사라져버립니다.

## 배우지 않은 스타일 속성은 어떻게?

**Q 폰트에 밑줄을 넣고 싶어요  
A 구글에 검색하세요!**

구글에 검색하는 것만으로도 간단하게 답을 찾을 수 있습니다. 같이 해볼까요?

![&#xD0A4;&#xC6CC;&#xB4DC;: css &#xD3F0;&#xD2B8; &#xBC11;&#xC904;](../.gitbook/assets/image%20%285%29.png)

![&#xB9E8; &#xC704; &#xC790;&#xB8CC;&#xC758; &#xB0B4;&#xC6A9;](../.gitbook/assets/image%20%28192%29.png)

이 내용을 보면서 깨달을 수 있습니다. **text-decoration: underline;** 을 하면 되는구나! 쉽죠?

만약 영문 검색을 하실 수 있다면 훨씬 정확하게 자료를 찾으실 수 있습니다.  
**영문 키워드: css font underline**

