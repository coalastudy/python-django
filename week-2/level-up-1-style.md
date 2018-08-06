# Level Up 1 - 기타 style

## position

**position**은 **absolute, relative, fixed, static**의 속성을 지정할 수 있습니다.

| 스타일 | 속성 | 설명 |
| :--- | :--- | :--- |
| position | absolute | 절대 좌표를 기준으로 표시한다. |
|  | relative | 개체의 현재 위치로부터 상대좌표로 표시한다. |
|  | fixed | 항상 그 위치에 띄운다. |
|  | static | 기본 설정 |

### absolute

이전 실습에 이어서 absolute 부터 시작하겠습니다.

![&#xC8FC;&#xD669;&#xC0C9; &#xBC15;&#xC2A4;&#xB294; position:absolute;&#xC774; &#xC9C0;&#xC815;&#xB41C; &#xC0C1;&#xD0DC;](../.gitbook/assets/image%20%28104%29.png)

```markup
<div style="width: 300px; height: 200px; background-color: blue; color: #fff;">A</div>

<div style="top: 35px; left: 40px; position: absolute; width: 200px; height: 150px; background-color: orange; color: #ffffff;">B</div>
```

여기까지 진행하셨을 겁니다.

### z-index

이때 만약 주황색 B보다 파란색 A가 중요하다고 판단되면, z-index 속성을 통해 순서를 바꿀 수 있습니다.  
박스 A에 z-index: 1000이라 하고, 박스 B에 z-index:999라 하면, z-index 값이 높은 A가 더 위에 올라오게 되고, B는 가려지게 되죠. z-index는 0~9999 사이의 값을 사용할 것을 권장합니다.

```markup
<div style="width: 300px; height: 200px; background-color: blue; color: #fff; position: absolute; z-index: 1000;">A</div>
<div style="top: 35px; left: 40px; position: absolute; width: 200px; height: 150px; background-color: orange; color: #fff; z-index: 999;">B</div>
```

### relative

absolute을 설정하면 **top, bottomm right, left**는 **맨 위/아래/오른쪽/왼쪽**이 기준이 됩니다. 이와는 조금 다르게 relative를 설정하면, 현재 개체가 놓인 위치 그 자체가 기준이되는 거죠.

### fixed

absolute과 똑같은 기준을 사용합니다. 다만 스크롤을 움직여서 창이 보고 있는 화면이 바뀌어도 해당 좌표에 고정된 개체가 따라옵니다. 뉴스 기사를 읽다보면 오른쪽 아래에 **'맨 위로'**라는 버튼이 계속 떠 있는 것을 볼 수 있는데요. 이 같은 경우 fixed로 고정해두어 항상 그 자리에 위치하게끔 설정해둔 것 이랍니다.

![&#xC77C;&#xBC18;&#xC801;&#xC73C;&#xB85C; &#xB9E8;&#xC704;&#xB85C; &#xBC84;&#xD2BC;&#xC740; &#xD56D;&#xC0C1; &#xADF8;&#xC790;&#xB9AC;&#xC5D0; &#xACE0;&#xC815;&#xB418;&#xC5B4; &#xC788;&#xB2E4;.](../.gitbook/assets/image%20%28295%29.png)

## dispaly

이번에는 레이아웃의 형태를 결정하는 display를 배워보겠습니다. 말이 조금 어려운데요, 정의에 신경쓸 필요 없이 실제로 어떻게 동작하는지를 보면 이해가 쉽습니다.

### display:block

![display:block](../.gitbook/assets/image%20%28196%29.png)

display 설정을 안했을때 해당되는 기본 설정입니다. 평소 박스를 그리는 방식과 일치합니다. 박스하나가 한 줄을 통째로 차지하게 되죠.

```markup
안녕하세요. 저는 <div style="background-color: blue; color: #fff; width: 100px; height: 30px; display: block;">최도근</div>입니다.
```

### display:inline

![display:inline](../.gitbook/assets/image%20%28246%29.png)

마치 박스가 글자처럼 변합니다. 이때는 width, height 같이 블럭의 크기를 지정하는 속성들이 무시됩니다. 글자와 똑같은 상태가 되니까요.

```markup
안녕하세요. 저는 <div style="background-color: blue; color: #fff; width: 100px; height: 30px; display: inlin;">최도근</div>입니다.
```

### display:inline-block

![display:inline-block](../.gitbook/assets/image%20%28183%29.png)

박스처럼 부피를 갖으면서 동시에 글자처럼 한줄에 함께 표시될 수 있는 방식입니다. 잘 사용한다면 레이아웃을 만드는데 큰 도움이 됩니다.

```markup
안녕하세요. 저는 <div style="background-color: blue; color: #fff; width: 100px; height: 30px; display: inline-block;">최도근</div>입니다.
```

### display:none

![display:none](../.gitbook/assets/image%20%2840%29.png)

사라져버립니다.

```markup
안녕하세요. 저는 <div style="background-color: blue; color: #fff; width: 100px; height: 30px; display:none;">최도근</div>입니다.
```



