# Level Up 1 - 스크롤 개선

## 스크롤 개선  

![&#xC2A4;&#xD06C;&#xB864;&#xBC14; &#xBB38;&#xC81C;](../.gitbook/assets/image%20%28277%29.png)

브라우저, 스마트폰의 **세로 길이가 짧거나** 위 사진처럼 혹은 **내용물이 길어지면** 하단탭에 가려지는 부분이 생기는데,  스크롤바를 움직여도 보이지가 않습니다. 또한 계속 고정되어 있어야할 상단탭이 함께 움직이는 문제가 발생합니다.

이 내용은 스터디중에는 실습하지 않습니다. 그러나 완성도를 높이고자 하는 **바른 욕심**을 가진 멤버들이 있기에 이 내용을 추가하였습니다.

### 하단탭 겹침 문제

결론적으로 말하면 피드가 표시되는 가운데 내용물의 높이를 하단탭 만큼 더 길게 만들어 주셔야 한다는 것 입니다. 여백을 넣던지 세로길이를 늘리던지 하여 하단탭만큼 남는 여유공간을 만들어준다면 쉽게 해결됩니다.

`.container`에 `padding-bottom`만 추가해주세요.

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```text
.container {
    background-color: #d7d8dc;
    padding-bottom: 50px;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}



![&#xD574;&#xACB0;&#xB41C; &#xBAA8;&#xC2B5;](../.gitbook/assets/image%20%28148%29.png)

### 상단바 이동 문제

페이스북을 보면 검색창이 있는 최상단바는 그자리에 고정되어 있습니다. 이와 달리 저희 상단바는 스크롤에 따라 함께 움직입니다.

이는 `position:fixed` 방식으로 해결할 수 있습니다.

스타일시트에서 아래 클래스 부분을 찾아 수정해주세요. `.container`에 `padding-top`이 추가된 건, `position:fixed`를 하는 순간 공주에 뜨게 되어 겹치는 부분이 발생하기 때문에 인위적으 여백을 넣어주기 위함입니다.

{% code-tabs %}
{% code-tabs-item title="newsfeed.html" %}
```markup
.header {
    background-color: #475d9f;
    color: #fff;
    height: 42px;
    border-bottom: 1px solid #2c3863;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
}
/* 중략 */
.container {
    background-color: #d7d8dc;
    padding-bottom: 50px;
    padding-top: 42px;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 자, 완성됐습니다. 이제 스크롤바가 움직인다고 상단바가 따라가지 않고, 그렇다고 탭바와 내용물이 겹치는 일도 없을 겁니다.

![&#xCD5C;&#xC885; &#xACB0;&#xACFC;](../.gitbook/assets/image%20%2862%29.png)



