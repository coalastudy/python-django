# Stage 3 - 파이썬으로 장고 깨닫기

## 파이참에서 파이썬 실행하기

여태까지는 파이썬 IDLE를 이용해 파이썬 코드를 실행하였습니다. 이제부터는 코드가 길어지므로 파이참을 이용하는것이 좋습니다.

![](../.gitbook/assets/image%20%2828%29.png)

### 1. 새 프로젝트를 생성합니다.

![](../.gitbook/assets/image%20%28106%29.png)

### 2. 적당한 프로젝트의 이름을 입력합니다. \(ex python\_practice\)

![](../.gitbook/assets/image%20%2826%29.png)

### 3. 새로운 파이썬 파일을 생성합니다.

![](../.gitbook/assets/image%20%2894%29.png)

![](../.gitbook/assets/image%20%2878%29.png)

### 4. 코드를 이곳에 작성합니다.

![](../.gitbook/assets/image%20%2819%29.png)

IDLE와 달리 입력했을 때 바로 코드가 실행되지 않습니다. 입력이 모두 끝나고 사용자가 코드를 실행했을 때만 입력한 코드가 수행됩니다.

### 5. 작성중인 파일에서 마우스 오른쪽 버튼을 누르고 Run '파일명'을 누르면 실행됩니다.

![](../.gitbook/assets/image%20%2861%29.png)

![&#xC2E4;&#xD589; &#xACB0;&#xACFC;](../.gitbook/assets/image%20%2822%29.png)

## 변수

### 실습 - 변수의 숫자형

```text
26ㅔ페이지 변수의 숫자형


```

{% hint style="info" %}
**%는 나머지를 계산해줍니다**  
`print(10 % 3) # 1출력`
{% endhint %}

### 실습 - 변수의 문자열형

```text
27페이지
```

### 실습 - 변수의 리스트형

```text
28페이지

```

### QUIZ

#### 1. 문자를 더하면?

```text
29page quiz1

```

#### 2. 문자형에 들어 있는 숫자끼리 더하면?

```text
퀴즈2
```

#### 3. K는 어떤 값이 될까요?

```text
퀴즈3
```

#### 답

1. my name is Django
2. 12344321
3. P

## if

### 실습 - 연습

if는 특정 조건에 따라 흐름을 관장하므로 제어문, 조건문이라고도 불립니다.

```text
30페이지 이프문
```

### 실습 - elif와 else

elif는 지금까지 검사한 if, elif가 실행되지 않았을 때, 새로운 조건을 검사합니다.

else는 지금까지 if, elif가 실행되지 않았을 때, 조건 검사 없이 바로 실행합니다.

```text
31페이지 elif
```

## for

### for란 무엇인가?

어떤 반복적인 일을 하고 싶을때 for문을 사용합니다. for 구문의 사용방법은 아래와 같습니다.

![for&#xBB38;&#xC758; &#xC0AC;&#xC6A9;&#xBC95;](../.gitbook/assets/image%20%2840%29.png)

```text
32페이지 포문 위쪽
```

만약 이때 for문을 사용한다면 다음과 같은 코드만으로도 가능합니다.

```text
32페이지 아래쪽 포문
```

결과를 예측해보세요. 어떻게 나올까요? \(직접 코딩해서 확인하는게 제일 좋겠죠\)

### list를 for문을 이용해 출력하기

다음과 같은 리스트가 있다고 가정합시다.

`todo_list = ['이따 밥먹기', '빨래하기', 1, 2, 3, '운동하기']`

이 내용물들을 모두 출력하려면 어떻게 해야 할까요? 오늘 배운대로 라면 이렇게 할 수 있습니다.

```python
print(todo_list[0])
print(todo_list[1])
print(todo_list[2])
print(todo_list[3])
print(todo_list[4])
print(todo_list[5])
```

하지만 너무 반복성이 짙죠. 만약 리스트 내용물이 100개나 있다면, 가히 노가다라 할 만한 작업을 해야할 겁니다. 그나마 100개라면 다행이겠죠.

이러한 반복적인 작업을 대신 수행해주는게 for문입니다. for문을 통해 list를 출력하려면 다음과 같이 입력해주세요.

![for&#xBB38;&#xC5D0;&#xC11C; list &#xC811;&#xADFC;&#xD558;&#xAE30;](../.gitbook/assets/image%20%28118%29.png)

**todo\_list**라는 이름의 리스트에 접근할 것 입니다. 그리고 그 안에 있는 내용물 하나 하나를 **todo**라고 부르겠습니다. todo는 맨 처음에 todo\_list\[0\]이 되었다가 이어서 todo\_list\[1\]이 됩니다. 그리고 todo\_list\[2\]가 되는 작업을 todo\_list가 끝날때까지 반복합니다. 즉 위에서 노가다로 작업한 print 구문과 똑같은 작업을 한다고 볼 수 있습니다.

### 예시

![](../.gitbook/assets/image%20%2824%29.png)

### 실습 - list 출력 개선

stage2\(강의자료 17페이지\)에서 for 문을 사용하지 않고 모든 리스트를 각각 출력해봤습니다. 이제 이 부분을 개선시킬 수 있게 됐습니다.

단 차이점은 장고를 통해 html 에서 for문을 사용한다는 것 입니다. 이는 장고의 템플릿 문법 기능으로 장고가 가지고 있는 특색이자 장점입니다.

{% code-tabs %}
{% code-tabs-item title="play2.html" %}
```text
play2 html 32
page
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### 결과확인

![](../.gitbook/assets/image%20%28110%29.png)

