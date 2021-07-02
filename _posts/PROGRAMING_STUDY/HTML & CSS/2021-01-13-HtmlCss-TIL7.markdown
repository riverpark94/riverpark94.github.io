---
layout: post
title: '[HTML & CSS] TIL 7. 단위, 배경, 박스모델'
date: 2021-01-13 22:03:44 +0900
subtitle: '단위, 배경, 박스모델'
category: PROGRAMING_STUDY
tags: HtmlCss
comments: true
toc: true
---

> 1. 구체성의 정의와 알아야하는 이유는 무엇인가?
> 2. 인라인 스타일의 구체성과 import의 구체성을 알아본다.
> 3. 전체선택자로 스타일을 적용하고, 특정 요소에 id 선택자를 이용해 스타일을 적용했을 때, 특정 요소의 자손의 스타일은 어떻게 적용되는가.
> 4. 캐스케이딩의 규칙을 쓰시오.

<br>

[boostcourse](https://www.boostcourse.org/)의 **[웹 UI 개발](https://www.boostcourse.org/web344)** 강의를 듣고 정리한 필기입니다. 😀 
{: .notice--warning}

<br>

# 1. 정의와 구문

CSS 속성은 매우 다양하고 그 종류가 계속 추가되고 있다. 기존의 속성명이 변경되기도하고, 어떤 속성은 빠지기도하고, 새로운 속성이 추가되기도 한다. 이러한 변화 때문에 서적이나 강의를 통해서 속성을 파악하는 것은 어려운 일이다. 그래서 실무자들이 가장 많이 참고하는 사이트 두 곳( [w3schools,](https://www.w3schools.com/) [MDN](https://developer.mozilla.org/ko/))을 참고하면 추가되고, 삭제, 혹은 변경 되는 CSS 속성을 확인할 수 있다.

CSS Reference를 통해 확인 가능한 사항은 다음과 같다.

- **정의** : 해당 속성이 어떤 변화를 일으키고 어떻게 동작하는지 파악할 수 있다.
- 기본 값 
  - 상속 여부 
- 애니메이션 가능 여부 
  - 사용 가능한 CSS버전
  
- **문법**: 해당 속성값을 어떤 식으로 나열하여 사용하는지를 파악할 수 있다.

- **속성 값** : 해당 속성이 인식하여 적용할 수 있는 값의 형태나, 키워드 등을 파악할 수 있다.
- **Initial** : 초기값, 즉 속성의 기본값으로 정의 (ie에서 지원하지 않음)
  
- **Inherit** : 부모 요소의 해당 속성 값을 적용 (상속 가능할 요소일 경우) 즉, 상속이 불가능한 속성일 경우에는 적용 되지 않습니다.
  
- **지원 범위** : 해당 속성이 정의에 맞게 동작 가능한 CSS 버전, 브라우저별 버전을 확인할 수 있다.

  - 어떤 브라우저의 어떤 버전이냐에 따라 같은 값이어도 다르게 렌더링 될 수 있으므로, 현재 프로젝트의 사용자 제공 지원 범위를 잘 확인하고 적용해야 한다.

- **예제** : 문법과 속성값을 바탕으로 실제로 속성을 동작하는 예제 코드를 확인할 수 있다.

- **참고 사항** : 해당 속성에 대해 특이사항이나 버그에 대해서 확인할 수 있다.

<br>

# 2. 속성

### 2.1 단위

단위에는 크게 **절대 길이 단위**와 **상대 길이 단위**로 구분되어진다. (*참고 : CSS에서 0 값에 대해서는 단위를 따로 적지 않는다.  ex. 0px = 0% = 0em = 0pt... =>  " 0 "*)

####   2.1.1 절대 길이(`px`, `pt`)

절대 길이는 고정된 크기 단위로 다른 요소의 크기에 영향을 받지 않는다. 브라우저의 너비나 길이에도 말이다. 

- **px** ( 1px = 1/96th of 1 inch )

  절대 길이는 다른 요소에 영향을 받지 않으지만, 장치의 <u>해상도에 따라 상대적</u>이다. 여러 환경에서 디자인을 같게 표현하고 브라우저 호환성에 유리한 구조로 되어 있어서, 디자인 의도가 많이 반영된 웹사이트의 경우 픽셀의 단위를 사용하는 것을 권장한다.

- **pt** ( 1pt - 1/72 of 1 inch )

  컴퓨터가 없던 시절부터 쓰던 단위이다. 인쇄물이나 MS 워드 프로그램에서 사용되는 가장 작은 표준 인쇄 단위이다. 웹 화면에 인쇄용 문서를 위한 스타일을 적용할 때 유용하게 사용할 수 있다. 그러나 사용하는 기기의 해상도에 따라 차이가 있어 W3C에서도 pt는 웹개발시 권장하는 단위가 아니다. 

####   2.1.2 상대 길이(`px`, `pt`)

상대 길이는 다른 요소의 크기나 폰트 크기, 브라우저 등의 크기에 따라 상대적으로 값이 변한다. 

- **%** : 부모의 값에 대한 백분율로 환산한 크기를 갖게 된다.
- **em** : font-size를 기준으로 값을 환산하고, 소수점 3자리까지 표현 가능하다.
  - em은 선언한 해당 폰트의 대문자 M의 너비를 기준으로 하는 상대적 단위이다.
  - 1em은 현재 지정된 폰트 크기와 같고, 2em은 현재 폰트 크기의 두 배를 의미한다.
- **rem** : root의 font-size를 기준으로 값을 환산한다.
- **vwn** : viewport의 width값을 기준으로 1%의 값으로 계산된다.

### 2.2 색상

#### 2.2.1 Color 속성

색상 값을 적용할 때 사용하는 속성이다.

```css
h1 { color : red; }
```

#### 2.2.2 색상 지정 방식

- **컬러 키워드**

  css 자체에서 사용 가능한 문자 식별자이다. red, blue, black 등과 값이 미리 정의되어있는 키워드를 이용해 색상을 표현할 수 있다. (*참고 : transparent는 투명을 나타내는 키워드*)

  ![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL7/2021-01-13-HC-TIL7-1.png)

- **16 진법**(ex. #RRGGBB)

  6자리의 16진수 (0-9, A-F)는 각각 두 자리씩 씩 세 가지 색상을 나타낸다.

  ![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL7/2021-01-13-HC-TIL7-2.png)

- **16 진법**(ex. #RGB)

  6자리의 16진수에서 각각의 두 자리가 같은 값을 가지면 3자리로 축약하여 사용할 수 있다.

  ![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL7/2021-01-13-HC-TIL7-3.png)

- **RGB( )**

  RGB 값은 rgb(R, G, B)의 형태로 각 변수 값(R 적색, G 녹색, B 청색)의 강도를 정의한다.
  0~255의 정수로 된 값을 지정할 수 있으며, 0 → 255는 검정 → 흰색으로 값의 변화를 나타낸다.

- **RGBA( )**

  RGBA 값은 기존 RGB에서 A값이 추가된 형태이다.
  rgb(R, G, B, A)의 형태로 각 변수는(R 적색, G 녹색, B 청색, A 투명도)의 강도를 정의한다.
  A 값은 0 ~ 1 사이의 값을 지정할 수 있으며, 0.5와 같이 소수점으로 표기합니다.
  0 → 1은 투명 → 불투명으로 값의 변화를 나타낸다. 예를 들어, rgba( 0, 0, 0, 0)는 투명한 색상을 가지게 된다.

### 2.3 background

이 속성은 요소의 배경에 대한 것이다. 색상부터 반복 여부 등 여러 하위요소가 존재한다.

- **background-color** : 배경색을 정하는 것으로 설정하지 않으면 transparent (투명)이라는 값이 지정된다. 
- **background-image** : 이것은 이미지 경로를 지정합니다. 절대경로, 상대경로 모두 사용이 가능하다.  background-color에 색상이 적용된 상태에서 background-image로 사용된 이미지에 투명한 부분이 있다면, 그 부분에 background-color 색상이 노출된다.
- **background-repeat** : 이미지의 반복 여부를 지정하는 속성이다. 
  - **repeat** : x, y축 으로 모두 반복한다. 
  - **repeat-x** : x 축 방향으로만 반복한다. 
  - **repeat-y** : y 축 방향으로만 반복한다.
  - **no-repeat** : 이미지를 반복하지 않는다.
- **background-position** : 기본값은 0%이고, 0% 요소에서 배경 이미지 위치를 지정하는 속성이다. X축, Y축으로부터의 위치를 지정할 수 있다. %, px, top, left 등등의 키워드를 사용할 수 있다.
- **background-attachment** : 기본값은 scroll이다. 스크롤에 따른 배경 이미지의 움직임 여부를 지정하는 속성이다.
  - **scroll** : 배경 이미지는 요소 자체를 기준으로 고정되어 있으며 내용과 함께 스크롤 되지 않는다.
  - **local** : 배경 이미지는 요소의 내용을 기준으로 고정되어 있으며 내용과 함께 스크롤 된다. 
  - **fixed** : 배경 이미지는 뷰포트를 기준으로 고정되어 있으며 스크롤에 영향을 받지 않는다.

### 2.4 boxmodel

모든 요소는 사각형의 박스 형태로 만들어진다. 박스는 총 4가지의 세분된 영역으로 구분되어있다. CSS를 이요해 이 상자의 크기, 위치 및 속성(색상, 배경, 테두리 크기 등)을 변경할 수 있다.

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL7/2021-01-13-HC-TIL7-4.png)

- **Content 영역** : 요소의 실제 내용으로 포함하는 영역이다. 

  ![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL7/2021-01-13-HC-TIL7-5.png)

- **Border 영역** : Content 영역을 감싸는 테두리 선을 말한다.

  ![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL7/2021-01-13-HC-TIL7-6.png)

- **Padding 영역** : content 영역이 배경, 색 또는 이미지가 있을 때 패딩 영역까지 영향을 미친다.

  ![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL7/2021-01-13-HC-TIL7-7.png)

- **Margin 영역** : 주변 요소와의 여백(간격)을 margin을 이용해 지정할 수 있는 영역이다.

  ![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL7/2021-01-13-HC-TIL7-8.png)

### 2.5 border

border 속성은 요소의 테두리에 관련된 속성을 지정할 때 사용한다.

- **border-width** : 기본값은 medium 이며, 선의 굵기를 지정하는 속성이다. `border-top-width`, `border-bottom-width`, `border-right-width`, `border-left-width`를 이용해 상하좌우 선의 굵기를 다르게 표현할 수 있다. 
  - 키워드로는 `thin`, `medium`, `thick`이 있다.

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL7/2021-01-13-HC-TIL7-9.png)

```css
  /* 키워드 값 */
border-width: thin;
border-width: medium;
border-width: thick;

/* <length> 값 */
border-width: 4px;
border-width: 1.2rem;

/* 세로방향 | 가로방향 */
border-width: 2px 1.5em;

/* 위 | 가로방향 | 아래 */
border-width: 1px 2em 1.5cm;

/* 위 | 오른쪽 | 아래 | 왼쪽 */
border-width: 1px 2em 0 4rem;

/* 전역 키워드 */
border-width: inherit;
border-width: initial;
border-width: unset;
```

- **border-style** : 기본값은 none으로 선의 모양을 지정하는 속성이다. `border-top-style`, `border-bottom-style`, `border-right-style`, `border-left-style`을 이용하여 상하좌우 선의 모양을 다르게 표현할 수 있다.

  - **none** : border를 표시 하지 않는다. 

     ![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL7/2021-01-13-HC-TIL7-10.png)

  - **dotted** : border를 점선 모양으로 나타낸다.  

     ![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL7/2021-01-13-HC-TIL7-11.png)

  - **inset** 

    ![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL7/2021-01-13-HC-TIL7-12.png)

  - **solid** : border를 실선 모양으로 나타낸다.  

    ![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL7/2021-01-13-HC-TIL7-13.png)

  - **double** : border를 이중 실선 모양으로 나타낸다. !

    ![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL7/2021-01-13-HC-TIL7-14.png)

  - border-style은 두가지를 복합적으로 사용할 수도 있다. 

```css
/* 위 | 가로방향 | 아래 */
border-style: hidden double dashed;
```

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL7/2021-01-13-HC-TIL7-15.png)

```css
/* 위 | 오른쪽 | 아래 | 왼쪽 */
border-style: dashed groove dotted solid;
```

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL7/2021-01-13-HC-TIL7-16.png)

- **border- color** : 기본 값 : currentColor 선의 색상을 지정하는 속성이다. `border-top-color`, `border-bottom-color`, `border-right-color`, `border-left-color`를 이용하여 상하좌우 선의 색상을 다르게 표현할 수 있다.

- **border 축약** : 아래와 같은 하위 속성을 쓰지 않아도 여러가지 적용이 가능하다. 

```css
  /* 스타일 */
border: solid;

/* 너비 | 스타일 */
border: 2px dotted;

/* 스타일 | 색 */
border: outset #f33;

/* 너비 | 스타일 | 색 */
border: medium dashed green;

/* 전역 값 */
border: inherit;
border: initial;
border: unset;
```

### 2.6 pandding & margin

두 속성 모두 박스 모델에서 보았던 것이다. 여기서는 각각 요소의 세부 속성값을 적용하는 것을 중심으로 한다.

#### 2.6.1 padding

- **속성값** : 기본값은 0이다. 
- **length** 고정값으로 지정한다. (ex. px, em ....)
  - **percent** 요소의 width에 상대적인 크기를 지정한다.
  - **padding-top** content 영역의 위쪽 여백을 지정한다.
  - **padding-right** content 영역의 오른쪽 여백을 지정한다.
  - **padding-bottom** content 영역의 아래쪽 여백을 지정한다.
  - **padding-left** content 영역의 왼쪽 여백을 지정한다.
  
- **문법**

```css
/* top | right | bottom | left */
padding: 5px 1em 0 2em;

/* Global values */
padding: inherit;
padding: initial;
padding: unset;
```

- **축약**

```css
/* 좌우 해딩값이 같을 때 */
padding: 20px 30px 40px;      /*  ( = 20px 30px 40px 30px; ) */

/* 좌우 패딩과 마찬가지로 상하의 패딩 값이 같을 때 */
padding : 20px 30px;          /*  ( = 20px 30px 20px; ) */

/* 상하좌우 패딩 값이 모두 같을 때 */
padding : 20px 20px;          /*  ( = 20px, 20px, 20px, 20px ) */
padding : 20px;               /*  ( = 20px, 20px, 20px, 20px ) */
```

#### 2.6.2 margin

margin은 다른 요소오의 간격을 만들 수 있다. 이는 pandding과 사용하는 방법이 매우 유사하지만 다른 점이 있다.

- **속성값** : 기본값은 0이다.
  - **length** : 고정값으로 지정한다. (ex. px, em...)
  - **percent** : 요소의 width에 상대적인 크기를 지정한다.
  - **auto** : 브라우저에 의해 계산된 값이 적용된다.

- **하위요소** 
  - **margin-top** : 위쪽 여백을 지정한다.
  - **margin-right** : 오른쪽 여백을 지정한다.
  - **margin-bottom** : 아래쪽 여백을 지정한다.
  - **margin-left** : 왼쪽 여백을 지정한다.

- **문법**
  - **margin auto** : 브라우저가 적절한 여백 크기를 선택. 예를 들어 요소를 중앙 정렬하고 싶을 때 사용할 수 있다.

```css
/* 네 면 모두 적용 */
margin: 1em;
margin: -3px;

/* 세로방향 | 가로방향 */
margin: 5% auto;

/* 위 | 가로방향 | 아래 */
margin: 1em auto 2em;

/* 위 | 오른쪽 | 아래 | 왼쪽 */
margin: 2px 1em 0 auto;

/* margin auto를 활용해 수평 중앙 정렬을 할 수 있다. */
margin-left: auto;
margin-right: auto;
```

- **margin collapse(마진 병합)** 
  
  마진 병합은 인접한 두 개 이상의 수직 방향 박스의 마진이 하나로 합쳐지는 것을 의미한다. 마진 병합은 다음 세가지의 경우에 일어난다.
  
  - **두 요소가 상하로 인접한 경우** : 위 요소의 하단 마진과 아래 요소의 상단 마진의 병합이 일어난다.
  
  - **부모 요소와 첫 번째 자식 요소 또는 마지막 자식 요소**
  
    - 부모 요소의 **상단 마진**과 첫 번째 자식 요소의 **상단 마진** 병합이 일어난다.
  
    -  부모 요소의 **하단 마진**과 마지막 자식 요소의 **하단 마진** 병합이 일어난다.
  
  - **내용이 없는 빈 요소의 경우** : 해당 요소의 상단 마진과 하단 마진의 병합이 일어난다.

  
  마진 병합은 수직 방향으로만 이루어지며, 좌우에 대해서는 일어나지 않는다. 마진이 반드시 맞닿아야 발생하기 때문에 2,3번째의 경우 패딩 및 보더가 없어야 한다.
### 2.7 width 와 height

#### 2.7.1 width 

이는 content 영역의 가로 크기를 정의하는 데 사용하는 속성이다. 크기를 고정값처럼 지정하는 것 같지만, 요소나 종류, 특징에 따라 다르게 동작한다. 이 속성은 인라인 레벨 요소를 제외한 모든 요소에 적용된다. 

기본값은 역시나 0이다. 속성값으로는 총 세가지가 있다. 

- **속성값**
  - **auto** : 브라우저에 의해 자동으로 계산하여 적용한다.
  - **length** : 고정값으로 지정한다. (ex. px, em ... )
  - **percent** : 부모 요소의 width에 상대적인 크기를 지정한다.

width은 auto 가 아닌 값을 지정하면, margin 영역을 제외한 모든 영역에 영향을 준다. 이게 무슨 이야기냐면, 아래 코드를 실행하면 총 가로 크기는 160px이다.

```css
.box {
  width: 100px;
  padding: 20px;
  border: 10px solid black;
}
```

#### 2.7.2 height

이는 content 영역의 세로 크기를 정의하는 데 사용하는 속성이다. height와 마찬가지로 정확히는 content 영역의 높이를 지정한다. % 값을 가질 때를 제외하고는 height의 동작와 같게 동작한다.

기본값은 역시나 0이다. 속성값으로는 총 세가지가 있다. 

- **속성값**
  - **auto** : 브라우저에 의해 자동으로 계산하여 적용한다.
  - **length** : 고정값으로 지정한다. (ex. px, em ... )
  - **percent** : 부모 요소의 height에 상대적인 크기를 지정한다.

height는 content 영역의 높이를 제어할 때 사용하는데, 역시나 auto가 아닌 특정값을 지정하면, width 속성과 마찬가지로 margin 영역을 제외한 모든 영역에 영향을 준다. 

아래의 세로 값은 총 150px이다.

```css
.box {
  width: 100px;
  height: 100px;
  padding: 10px;
  border: 15px solid black;
}
```