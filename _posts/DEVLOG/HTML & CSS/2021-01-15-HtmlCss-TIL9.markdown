---
layout: post
title: '[HTML & CSS] TIL 9. 레이아웃, 미디어쿼리'
date: 2021-01-15 22:07:44 +0900
subtitle: '레이아웃, 미디어쿼리'
categories: DEVLOG
tags: HtmlCss
comments: true
toc: true
---

> 

<br>

[boostcourse](https://www.boostcourse.org/)의 **[웹 UI 개발](https://www.boostcourse.org/web344)** 강의를 듣고 정리한 필기입니다. 😀 
{: .notice--warning}

<br>


# 레이아웃

### 1. `display`

`display`속성의 기본값은 요소마다 다르다. 또, 블록 요소를 인라인요소처럼 보여줄 수도 있고, 반대로 인라인요소를 블록 라인 요소처럼 보여줄 수도 있다. 다시말해, 블록 레벨, 인라인 레벨 등 **렌더링 박스의 유형이 결정**되며, 심지어 변경할 수도 있다. **렌더링 여부도 결정** 할 수 있으니, `display` 속성을 잘 알아야 요소가 화면에 표현되는 방식을 이해하기가 쉬울 것이다.

```
display: value;
```

다른 속성과는 달리 `display` 속성 값은 value로 나타냈다. 이는 css가 없데이트 됨에 따라 그 값이 추가되고 있기 때문이다. (아래 코드는 value에 해당하는 값들을 나열해 본 것이다.)

```css
display : none;
display : inline;
display : block;
display : inline-block;
display : lish-item;
display : flex;
display : inline-flex;
display : none;
```

아래의 네가지는 실무에서 자주 사용되는 것으로 알고있으면 웹 UI 개발을 할때 편하다.

- **none** : 요소가 렌더링 되지 않아, 화면에 보이지 않게 된다.

- **inline** : inline level 요소처럼 렌더링

- **block** : block level 요소처럼 렌더링

- **inline-block** : inline level 요소처럼 렌더링(배치)되지만 block level의 성질을 가진다.


그 외에 list-item, flex, inline-flex, table, table-cell 등 다양한 속성 값 존재한다. 이러한 `display` 속성 값에 따라 box model의 속성들을 적용할 수 있고 없고의 차이가 있다.

#### 1.1 inline와 inline-block의 차이

inline 요소의 경우 공백과 개행에 대해서 하나의 여백으로 받아들인다. 따라서 inline와 inline-block의 경우 태그 사이의 공백이나 개행이 있을 경우 약 4px의 여백을 가지게 됩니다.

둘의 차이점은 콘솔창을 열어 확인해보면, inline은 콘텐츠 영역에서 auto * auto 값이 뜨지만, inline-block은 block 처럼 렌더링 값을 갖는다. 즉, height 나 width 등과 같은 박스모델 속성을 적용할 수 있다는 말이다.


#### 1.2 display와 box model의 관계

![title](/assets/img/DEVLOG/HTML & CSS/TIL9/2021-01-15-HC-TIL9-1.png)

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>display</title>
  <style>
    .inline{
        width: 100px;
        height: 100px;
        margin: 10px;
        border: 10px solid red;
        background: pink;
    }
  </style>
</head>

<body>
    <div>
        <div style = "display:inline" class = "inline">box</div>
    </div>
</body>
</html>
```

위에 코드를 보면 margin와 border에 10px의 값을 주었다.  콘솔창, box modle 부분을 참고해보면  margin, padding, border 모두 좌/우뿐만 아니라, 상/하에도 적용됨을 알 수 있다. 하지만 실제 브라우저에서 적용된 것을 확인해보면 좌/우에만 margin 영역이 잡힌다. 

![title](/assets/img/DEVLOG/HTML & CSS/TIL9/2021-01-15-HC-TIL9-2.png)

또, 이들의 부모 요소를 선택해보면, 부모 요소는 자식요소의 콘텐츠 (box)만큼만 선언되는 것을 볼 수 있다. 이렇듯 상/하 padding/border는 line-box에는 영향을 주지 못하기 때문에 위와 같이 부모 요소의 박스에 반영되지 않는다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL9/2021-01-15-HC-TIL9-3.png)


### 2. `visibility`

 `visibility` 속성은 요소의 화면 표시 여부를 지정하는 속성이다. CSS에서 요소를 숨기는 방법이 몇 가지 있다. display에서 아예 렌더링이 되지 않게끔 할 수도 있고, 다른 위치 관련 속성들을 이용해서 안 보이게 숨기는 방법도 있다. 하지만 요소를 숨긴다는 의미로만 해석하면 가장 명시적은 방법은 `visibility` 속성을 이용하는 것이다. 문법은 아래와 같다.

```
visible | hidden | collapse | initial | inherit;
```

- **visible** : 화면에 표시 

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <style>
    table.myTABLE {
	  background-color:yellow;
  	  visibility:visible; 
	}
  </style>
</head>

<body>
    <div>
        <p>
            This example demonstrates how the visibility property behaves on TABLE elements:
        </p>
        <table  class = "myTABLE ">
            <tbody>
                <tr>
                    <td>A TD element.</td>
                    <td>Another TD element.</td>
                </tr>
                </tr>
            </tbody>
        </table>
        <p>
            <b>Noto:</b>
            "The value "collapse" can only be used on TABLE elements."
        </p>
        <p>
            <b>Noto:</b>
            "The TABLE does only "collapse" in IE and Firefox."
        </p>
    </div>
</body>
</html>
```

![title](/assets/img/DEVLOG/HTML & CSS/TIL9/2021-01-15-HC-TIL9-4.png)
<br>

- **hidden** : 화면에 표시되지 않음(공간은 차지함) <br>

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <style>
    table.myTABLE {
	  background-color:yellow;
  	  visibility:hidden; 
	}
  </style>
</head>

<body>
    <div>
        <p>
            This example demonstrates how the visibility property behaves on TABLE elements:
        </p>
        <table  class = "myTABLE ">
            <tbody>
                <tr>
                    <td>A TD element.</td>
                    <td>Another TD element.</td>
                </tr>
                </tr>
            </tbody>
        </table>
        <p>
            <b>Noto:</b>
            "The value "collapse" can only be used on TABLE elements."
        </p>
        <p>
            <b>Noto:</b>
            "The TABLE does only "collapse" in IE and Firefox."
        </p>
    </div>
</body>
</html>
```

![title](/assets/img/DEVLOG/HTML & CSS/TIL9/2021-01-15-HC-TIL9-5.png)

<br>

- **collapse** : 셀 간의 경계를 무시하고 숨김(테이블 관련 요소에만 적용 가능)<br>

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <style>
    table.myTABLE {
	  background-color:yellow;
  	  visibility:collapse; 
	}
  </style>
</head>

<body>
    <div>
        <p>
            This example demonstrates how the visibility property behaves on TABLE elements:
        </p>
        <table  class = "myTABLE ">
            <tbody>
                <tr>
                    <td>A TD element.</td>
                    <td>Another TD element.</td>
                </tr>
                </tr>
            </tbody>
        </table>
        <p>
            <b>Noto:</b>
            "The value "collapse" can only be used on TABLE elements."
        </p>
        <p>
            <b>Noto:</b>
            "The TABLE does only "collapse" in IE and Firefox."
        </p>
    </div>
</body>
</html>
```

![title](/assets/img/DEVLOG/HTML & CSS/TIL9/2021-01-15-HC-TIL9-6.png)


#### display: none과 차이점

- **display** : none: 요소가 렌더링 되지 않음(DOM에 존재하지 않음)
- **visibility** : hidden: 요소가 보이지는 않지만 렌더링 되며 화면에 공간을 가지고 있음(DOM에 존재함)




### 3. `float`

`float` 속성은 요소를 보통의 흐름에서 벗어나게 할지를 지정하는 속성이다. *요소를 보통의 흐름에서 벗어난다?* 모든 요소는 기본적으로 위에서 아래로, 좌에서 우로 배치된다. 요소 박스의 경계를 기준으로 배치되는데, `float` 속성은 이런 흐름을 벗어나  독자적인 공간에 배치되게 한다. `float` 속성을 사용한 이유는 주변 요소들과 더 자연스럽게 배치하기 위함이지만 floating되지 않은 주변 요소에도 영향을 주기 때문에 그 원리를 잘 알고 있어야 한다. **주변 텍스트나 인라인 요소가 주위를 감싸는 특징이 있다. 또 대부분 요소의 display 값을 block으로 변경됩니다.**(display 값 변경 예외: inline-table, flex 등)

```
 none | left | right | initial | inherit;
```

- **none** : float 시키지 않음(기본값)

![title](/assets/img/DEVLOG/HTML & CSS/TIL9/2021-01-15-HC-TIL9-8.png)

- **left** : 좌측으로 float 시킴

![title](/assets/img/DEVLOG/HTML & CSS/TIL9/2021-01-15-HC-TIL9-9.png)

- **right** : 우측으로 float 시킴

![title](/assets/img/DEVLOG/HTML & CSS/TIL9/2021-01-15-HC-TIL9-7.png)



### 4. `clear`

`clear`는 floating된 요소의 영향에서 벗어나게 해주는 속성이다. `float` 속성으로 인해 주변도소들이 의도치 않은 대로 나타날 수 있다. 그때, `clear`이라는 속성을 사용하면 이 문제를 해결할 수 있다. 

```
none | left | right | both | initial | inherit;
```

- **none** : 양쪽으로 floating 요소를 허용(기본값)<br>
- **left** : 왼쪽으로 floating 요소를 허용하지 않음<br>
- **right** : 오른쪽으로 floating 요소를 허용하지 않음<br>
- **both** : 양쪽으로 floating 요소를 허용하지 않음

### 5. `position`

`position` 속성은 요소의 위치를 원하는 곳으로 이동시킬 때 사용한다. `position`속성을 좌표 속성인 `offset`과 함께 사용하면 더 다양하고 화려한 레이아웃을 구현할 수 있다.

#### 5.1 `postion`

```
static | absolute | fixed | relative | sticky | initial | inherit;
```

- **static**
  - Normal-flow 에 따라 배치되며 offset 값이 적용되지 않는다. (기본값)
  - **Normal-flow** : 일반적인 상황에서 각의 요소들의 성질에 따라 배치 되는 순서(흐름)를 뜻한다. 예를 들면, block 레벨 요소들은 상하로 배치되고, inline 레벨 요소들은 좌우로 배치되는 것을 말한다.
  
- **absolute**
  - 부모 요소의 위치를 기준으로 offset 에 따라 배치된다.
  - 부모가 position 값(static 제외)을 가지면 offset 값의 시작점이 된다.
  - 부모의 position 값이 static 인 경우, 조상의 position 값이 static이 아닐 때까지 거슬러 올라가 기준으로 한다.
  - Normal-flow의 흐름에서 벗어난다.
    - **Normal-flow** : 일반적인 상황에서 각의 요소들의 성질에 따라 배치 되는 순서(흐름)를 뜻한다. 예를 들면, block 레벨 요소들은 상하로 배치되고, inline 레벨 요소들은 좌우로 배치되는 것을 말한다.
- **fixed**
  - 뷰포트(브라우저의 창)를 기준으로 offset 에 따라 배치된다. 즉, 화면 스크롤에 관계없이 항상 화면의 정해진 위치에 정보가 나타난다.
  - 부모의 위치에 영향을 받지 않는다.
- **relative**
  - 자신이 원래 있어야 할 위치를 기준으로 offset 에 따라 배치된다. 부모의 position 속성에 영향을 받지 않는다. 
  - Normal -flow의 흐름에 따른다. 
  - 주변 요소에 영향을 주지 않으면서 offset 값으로 이동한다

#### 5.2 `offset`

```
top|bottom|left|right: auto|length|initial|inherit;
```

```css
top: 50%;
left: 10px;
bottom: -10px;
right: auto;
```

`offset` 속성은 top, bottom (상하) 는 기준이 되는 요소의 height 값 left, right (좌우) 는 width값에 대하여 계산된다.

### 6. `z-index`

PPT 작업을 하다보면 요소들끼리 겹칠 때 어떤 요소가 위로 올지, 혹은 아래로 갈지를 결정할 수 있다. CSS에서도 `z-index` 속성을 사용하면 겹쳐있는 요소의 순서를 결정하는 작업이 가능하다.

```
auto | number | initial | inherit;
```

- **auto** : 쌓임 순서를 부모와 동일하게 설정(기본값) 
- **number** : 해당 수치로 쌓임 순서를 설정(음수 허용)

```css
z-index: 1;
```

- position 값이 static이 아닌 경우 지정가능
- 순서 값이 없을 경우 생성순서(코드상 순서)에 따라 쌓임
- 부모가 z-index 값이 있을 경우 부모 안에서만 의미있음
- 큰 값이 가장 위쪽(음수 사용 가능)



<br>

***

# 미디어쿼리

> 들어가기 전, 여기 적혀있는 것은 CSS3 미디어 쿼리 표준 명세를 기준으로 작성되었지만, 미디어 쿼리 level 4에서는 대부분의 미디어 특성 중 일부 속성이 폐기 될 것이니 [Media Queries Level 4](https://www.w3.org/TR/mediaqueries-4/#media-types)를 꼭 참고하자.

요즘 웹 사이트들은 다양한 기기를 지원하기 위해서 반응형으로 제작하고 있다. 이러한 반응형 웹사이트 제작에 이어서 반드시 필요한 기술 중 하나가 **미디어쿼리**이다. 

이러한 미디어 쿼리는 각 미디어 매체에 따라 다른 스타일을 적용할 수 있게 만드는 것이다. 여기서 미디어 매체는 모니터, 프린트, 스크린 리더와 같은 것들을 이야기한다. 미디어 쿼리는 CSS2 의 미디어 타입을 확장해서 만들어졌다. CSS는 이론적으로는 훌륭했지만, 당시 미디어 매체가 다양하지 않았기 때문에 반응형이 아니더라도 충분했다고 한다. 

### 1. 미디어 타입 & 미디어 특성

`@media`로 시작하면 이제부터 미디어 쿼리를 시작한다는 뜻이다. 

```css
@media mediaqueries { /* style rules  */ }
```

이렇게 선언된 미디어 쿼리는 논리적으로 판단한다. **참이면 `{}(중괄호)`뒤에 있는 스타일이 적용되고, 거짓이면 그렇지 않다.** 이러한 구문은 미디어 타입과, 미디어 특성으로 이루어져 있다.

#### 1.1 미디어 타입(Media Types)

> **all**, braille, embossed, handheld, **print**, projection, **screen**, speech, tty, tv

우리는 위의 타입들 중에서 굵게 칠해진 **all**, **print**, **screen**만 알아도 된다. 

- **screen** :  화면에 출력하는 디스플레이가 있는 미디어들은 screen에 해당하기 때문에 현실적으로 고려해야하는 미디어들은 전부 여기에 해당한다.
- **print** : 스크린을 통해 접근하는 문서와 실제로 출력했을 때 종이로 보는 문서의 차이 때문에 간혹 쓰기는 한다. 예로 인쇄할 때는 가독성 때문에 스크린보다는 더 큰 폰트를 사용하거나 잉크 문제로 배경 색상을 없앤다든가 하는 용도로 쓰이기는 한다. 꼭 인쇄하지 않더라도 브라우저의 인쇄 미리보기 화면을 통해서도 적용된 모습을 확인할 수 있다. 
- **all** : 모든 미디어에 적용되는 타입으로써, 미디어 매체를 구분하지 못하기 때문에 유용하지는 않다.

#### 1.2 미디어 특성(Media Features)

> **width**, height, device-width, device-height, **orientation**, aspect-ratio, device-aspect-ratio, color, color-index, monochrome, resolution, scan, grid

여기서도 역기서도 역시 굵게 표시된 **width**와 **orientation**만 알아도 된다. 

- **width**은 스크린 크기가 아니라, 브라우저 창의 너비를 말한다. 
- **orientation**은 미디어가 세로 모드인지, 가로모드인지를 구분한다. 
  - **가로모드인지, 세로모드인지는 어떻게 구분할까?** width와 height의 값을 비교해서 구분한다.
    -  height가 width보다 같거나 크면 세로모드로 해석하여, portrait 키워드와 매칭된다.
    - 반대인 경우에는 가로모드라로 해석하여, landscape 키워드와 매칭된다.

### 2. 미디어 쿼리 문법

아래 코드들는 CSS3 미디어 쿼리 표준 명세에 나와 있는 Syntax 부분 중 강의에 나온 부분만을 가지고 온 것이다.

**👉  media_query_list**

- **S, \*** : 공백에 관련된 표현으로 그냥 없다고 보면 이해하기가 쉽다.
- **[ a ]** : a가 나올 수도 있고 나오지 않을 수도 있다. 생략이 가능하다는 표시이다.

> **아래 코드 해석**<br>
>	여러 개의 미디어 쿼리로 이루어진 리스트로 작성 가능하다.<br>
>	코드에 `'(홀따옴표)`로 적혀있는 부분들은 실제로 구문에 이 문자가 그대로 들어가야 함을 나타낸다.<br>
>	쉼표를 이용해서 구분한다. 

```css
media_query_list
 : S* [media_query [ ',' S* media_query ]* ]?
 ;
```

**👉 media_query**

- **a \| b** : a가 나올 수도 있고 b가 나올 수도 있다.
- **a?** : a가 0번 나오거나 1번만 나올 수 있음
- **a\*** : a가 0번 나오거나 그 이상 계속 나올 수 있음
- **media_type** : all, screen, print 등 명세에 정의된 미디어 타입
>**아래 코드 해석**<br>
>​	**A 형태** <br>
>​	미디어 타입에 and 키워드를 이용해서 미디어 표현식을 붙일 수 있다. <br>
>​	and는 소문자로 쓰여도 대문자로 쓰여도 상관이 없지만 보통 소문자로 쓰여진다. <br>
>​	미디어 타입 앞에는 only 또는 not 키워드가 올 수 있다.(생략도 가능하다.) <br>
>​	(표현식 앞에는 붙을 수 없다.) 미디어 표현식은 생략 가능하기 때문에 미디어 타입 단독으로 사용될 수 있다.<br>
>​	**B 형태** <br>
>​	미디어 타입 없이 미디어 표현식이 바로 나올 수 있습니다.(미디어 타입이 명시되지 않으면 all로 간주한다.)<br>
>​	미디어 표현식은 and 키워드를 이용해서 계속해서 나올 수 있다.

```css
media_query
 : [ONLY | NOT]? S* media_type S* [ AND S* expression ]*
 | expression [ AND S* expression ]*
 ;
```

**👉 expression**

- **media_feature** : width, orientation 등 명세에 정의된 미디어 특성

>**아래 코드 해석**<br>
>​	미디어 표현식은 무조건 괄호로 감싸야한다.<br>
>​	이 표현식은 특성 이름과 그것을 평가하는 값(expr) 이 두가지로 이루어져있다.<br>
>​	이름과 값은 `:` 기호로 연결한다.<br>
>​	값이 없이 특성 이름만으로도 작성할 수 있다.<br>

```css
expression
 : '(' S* media_feature S* [ ':' S* expr ]? ')' S*
 ;
```

#### 2.1 **min-/max- 접두사**

특성에 붙일 수 있는 프리픽스는 이 min프리픽스와 max 프리픽스 두 개이다. 이 프리픽스를 붙이게 되면 이름대로 최소 또는 최대 이렇게 구간을 지정해 줄 수가 있기다. 실제로 반응형 사이트를 제작할 때는 프리픽스를 붙여서 사용하는데, 그 이유는 그냥 특성 이름만 쓰는 경우는 대부분 효율적이지 못하기 때문이다. 

예를 들어 대부분의 반응형 사이트는 width 특성을 이용하는데, 접두사 없이 width: 00px이라고 하게 선언하면 정확히 뷰포트의 크기가 00px에서만 적용되기 때문에 굉장히 제한적으로 적용이 된다. 이런식으로 사이즈가 다른 많은 기기들을 대응하다가는 이 미디어 쿼리가 굉장히 많이 늘어나게 되기 때문에 min, max같은 프리픽스를 이용해서 구간을 설정하게 되면 훨씬 간결하게 반응형 사이트를 제작할 수 있다.

이 프리픽스는 숫자의 형태로 들어가는 특성에는 모두 사용이 가능하다.이런 프리픽스가 붙지 못하는 특성이 있는데 orientation, grid 그리고 scan 이 세가지에는 프리픽스를 붙일 수 없다.그 이유는 이 세가지 특성은 값으로 특정 키워드가 들어가기 때문이다. 

width는 길이에 유효한 단위면 px이든 cm이든 상관없다.orientation은 키워드가 들어간다.뷰포트의 길이가 세로로 긴 형태이면 portrait라는 키워드가 들어가고 가로로 긴 형태이면 landscape 키워드가 들어가게 된다.

#### 2.2 예제 코드

위에서 정의한 Syntax 따라 유효한 미디어 쿼리 예제 코드를 살펴보고 어떻게 해석이 되는지 같이 보자.

**`@media screen {... }`**  : 미디어 타입이 screen일 경우에 이 미디어 쿼리가 참으로 평가되면서 뒤에 나오는 스타일 규칙이 적용된다.

**`@media screen and (min-width: 768px) { ... }`**  : 미디어 타입이 screen이고 width가 768px 이상이면 참이 되어 적용되어진다. 두 개 중 하나라도 만족하지 않으면 거짓이 되어 뒤에 스타일 규칙이 적용이 되지 않는다. 

**`@media (min-width: 768px) { ... }`**  :`@media` 하고 미디어 타입이 없이 바로 표현식이 나온 형태이다.  이 경우도 유효한 구문이다.   미디어 타입이 명시되어지지 않으면 이 미디어 타입에는 all 이렇게 해석이 된다.  미디어 타입에 관계없이 width가 768px이상이면 참이 된다.

**`@media (min-width: 768px) and (max-width: 1024px) { ... }`**  : and는 연결된 모든 표현식이 참이면 적용된다. and 키워드로 연결된 표현식 중에 하나라도 거짓으로 평가되면 이 뒤의 스타일 규칙을 적용되지 않는다.

**`@media (color-index)`**  :특성 이름만 나온 형태 (값이 생략)인데, 미디어 장치가 color-index의 기능을 지원하면 참이 되어 적용된다.

**`@media screen and (min-width: 768px), screen and (orientation: portrait),...`**  : 쉼표로 연결된 미디어 쿼리 중 하나라도 참으로 평가되면 뒤의 스타일 규칙이 적용된다. and 키워드와 반대라고 생각하면 된다.

**`@media not screen and (min-width: 768px)`** <br>
​	: not과 only 키워드 둘 중에 하나가 들어갈 수 있다. only키워드는 예전에 미디어 쿼리를 지원하지 못하는 브라우저 때문에 있는 하위 호환성때문에 존재하는 키워드이기 때문에 지금    은 only키워드를 쓰나 안 쓰나 아무런 변화가 없다. <br>
​	: not 키워드는 하나의 media_query 전체를 부정하는 키워드이다. (가장 마지막에 해석)<br>
​	: (not screen) and (min-width: 768px) 잘못된 해석<br>
​	: not (screen and (min-width: 768px)) 올바른 해석<br>
​	: **`@media not screen and (min-width: 768px), print`** - 첫 번째 미디어 쿼리(not screen and (min-width: 768px)에만 not 키워드가 적용되며, 두 번째 미디어 쿼리(print)에는 영향이 없다.

#### 2.3 미디어 쿼리 선언 방법

미디어 쿼리를 선언하는 방법은 총 3가지가 있는데 `@media`를 이용한 방법을 가장 많이 사용하며 나머지 2가지 방법은 거의 쓰이지 않다.

**👉 `@media`**<br>
​	: `@media screen and(color)`<br>
​	: CSS 파일 내부에 또는 `<style>` 태그 내부에 사용 가능히다.

**👉 `<link media="">`**<br>
	: `<link rel="stylesheet" media="screen and (color)" herf="examplr.css">`<br>
 	: `<link>` 태그의 media 속성에 미디어 쿼리를 선언한다.<br>
 	: 미디어 쿼리가 참이면 뒤에 css 파일 규칙이 적용된다.<br>
​	 : 거짓으로 평가가 되어도 다운을 받게 된다.

 **👉 `@import`**<br>
 	: `@import orl(example.css) screen and(color);`<br>
 	: CSS 파일 내부에 또는 `<style>` 태그 내부에 사용가능하다.<br>
 	: `@import`문 뒤에 css 파일의 경로를 적고 한 칸 뛰고 미디어 쿼리를 선언하면 된다.