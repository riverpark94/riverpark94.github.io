---
layout: post
title: '[HTML & CSS] TIL 8. 폰트, 텍스트'
date: 2021-01-14 22:07:44 +0900
subtitle: '폰트, 텍스트'
category: PROGRAMING_STUDY
tags: HtmlCss
comments: true
toc: true
---

<br>

[boostcourse](https://www.boostcourse.org/)의 **[웹 UI 개발](https://www.boostcourse.org/web344)** 강의를 듣고 정리한 필기입니다. 😀 
{: .notice--warning}

<br>

# 속성

### 1. `typography`

타이포 그래피의 구조는 다음과 같다. 텍스트는 우리가 인식하고 있는 것과는 달리 굉장히 복잡한 구조를 가지고 있다. 

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL8/2021-01-14-HC-TIL8-1.png)

- **em** 폰트의 전체 높이를 의미합니다.

- **ex** ( = x-height ) 해당 폰트의 영문 소문자 x의 높이를 의미합니다.

- **Baseline** 소문자 x를 기준으로 하단의 라인을 의미합니다.

- **Descender** 소문자에서 baseline 아래로 쳐지는 영역을 의미합니다. 서체에 따라 descender의 길이가 다릅니다. ( g, j, p, q, y )

-  **Ascender** 소문자 x의 상단 라인 위로 넘어가는 영역을 의미합니다. ( b, d, h, l )

문자열을 확인할 때는 Baseline을 확인하는 게 굉장히 중요하다. Baseline을 기준으로 ex, 높이를 알 수 있고, 그 안의 여백(Descender 영역과 Ascender 영역)이 어느 정도인지 알고 있으면 좋기 때문이다. 

### 2. `font-family`

font-family는 **상속**되기 때문에 대표 폰트를 선언하고, 특정 폰트가 필요한 부분에 재 정의해 사용한다. 다만, font-family 구문을 사용하면서 주의해야 할 것이 있다.

font-family 속성을 선언할 때는 font-family name과 generic-family name를 같이 선언한다. SYNTAX 배울 때 `|`은 "OR(또는)"을 의미하지만, font-family은 generic-family를 같이 써줘야 한다. family-name과 generic-family의 의미는 다음과 같다.

```
family-name | generic-family ( | initial | inherit );
```

- **family-name** : 사용할 폰트의 이름을 나타내며 `,(콤마)`로 구분하여 여러 개 선언 할 수 있다. 먼저 선언된 순서대로 우선순위가 결정된다.  **이름 중간에 공백이 있거나, 한글일 경우 홑따옴표로 묶어서 선언**합니다.

- **generic-family**: family-name으로 지정된 글꼴을 사용할 수 없을 경우를 대비해, 브라우저가 대체할 수 있는 폰트이다. font-family 속성의 맨 마지막에 선언해야 하며, 키워드이기 때문에 따옴표 등의 인용부호로 묶지 않는 것이 원칙이다. 그리고  **자식요소에 font-family 속성을 재선언하면 부모에 generic-family가 선언되어있어도 다시 선언해주어야 한다.** 이런 generic-family의 서체들이 있다. (이것은 [MDN](https://developer.mozilla.org/ko/docs/Web/CSS/font-family#%EA%B0%92)을 확인하자.)

```CSS
          /* ... family-name  | generic-family ( | initial | inherit ) */
font-family: Helvetica, Dotum, '돋움', Apple SD Gothic Neo, sans-serif; 
```

위 코드를 보면 가장 먼저 Helventica를 사용하고, 이를 사용할 수 없을 때, Dotum을 사용한다. 만약, "ABC 가나다 123"이라는 글자가 있다면, Helventica은 한글을 지원하지 않기때문에 "ABC"와 "123"은 Helventica로 표현 되고, "가나다"는 Dotum으로 표현된다.

또, Dotum과 "돋움"을 한번에 선언한 이유는 한글을 지원하지 않는 디바이스 때문이다. 한글을 지원하지 않는 디바지스에서는 한글 폰트를 불러올 수 없으므로 영문명으로도 선언해줘야 한다. 그리고 마지막에는 반듯드시 generic-family를 선언해주면, 시스템 폰트 내에서 사용자가 의도한 스타일과 유사한 서체로 적용되기 때문이다. 

Apple SD Gothic Neo 같은 경우 IOS계열에서 기본 글꼴이다. 그런데 이 기본 글꼴은 애플사의 버전에 따라 어떻게 달라질지 모른다. 이런 일을 대비하기 위해 관련 성속을 선언하는 경우가 있다.

### 3. `line-height`

장문 글을 볼 때, 가독성을 위해 글 사이의 간격을 띄운다. 내가 tistory 블로그를 쓰다가 github로 옮겨온 이유기도하다. tistory는 행간 (글 사이의 간격)을 조정하기가 매우 어려웠기 때문이다. line-height 속성은 이런 행간을 조정할 수 있다. 정확히 말하면, line-height는 영어 뜻 그대로 줄의 높이를 의미하고, 이것을 이용해서 행간을 조정할 수 있다.

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL8/2021-01-14-HC-TIL8-2.png)

행간을 제어할 때 사용하는 속성이라 해서 줄간격으로 오해할 수 있다. 줄 간격으로 생각해 오해하기 쉬울 수가 있다. 줄 바꿈이 되었을 때, 윗줄의 텍스트 하단과 아랫줄의 텍스트 상단까지의 간격이라고 생각할 수 있다. 하지만 line-height로 제어되는 부분을 line-box한다. 이는 [타이포그래피 구조]()에서 배웠던 `em 박스 + 상하단의 여백`을 의미한다. 

line-height는 기본적으로 브라우저의 기본 속성을 따르지만, 아래의 속성값을 설정해 내가 원하는 행간을 만들 수 있다.

```
normal | number | length | percentage | initial | inherit ;
```

- **normal** : 기본값이다. 폰트에 따라 브라우저에 따라 다르지만, 보통 1.2로 할당되어있다.
- **number** : font-size를 기준으로 설정한 숫자만큼 배율.
- **length** : px, em 등의 고정 수치.(px로 입력할 때는 브라우저마다 다르기 때문에 기준 브라우저를 꼭 확인하고 행간을 입력해야 한다.)
- **percentage(%)**:  font-size를 기준으로 설정한 퍼센트만큼 배율.

```css
/* Keyword value */
line-height: normal;

/* Unitless values: use this number multiplied
by the element's font size */
line-height: 3.5;

/* <length> values */
line-height: 3em;

/* <percentage> values */
line-height: 34%;

```

여기서 주의할 점은, line-height의 값으로 number로 선언할 때와 %로 선언할 때의 차이이다. 두 값 모두 font-size를 기준으로 동작하기 때문에 같거나 거의 비슷할 거라고 오해할 수도 있다. 하지만 두 값은 line-height가 자식요소로 상속되었을 때의 계산 방식이 다르다.

- **number** 부모 요소의 숫자 값이 그대로 상속된다. 즉, 자식 요소에서도 또 한 번 자식 요소의 font-size를 기준으로 계산된 값을 가진다.

- **percentage(%)** 부모 요소에서 %값이 그대로 상속되는 것이 아니고, %에 의해 이미 계산된 px값이 상속된다.

예시 코드를 보면 이해가 빠르다. 

```css
body { font-size: 20px; line-height: 2; }       /* line-height = 40px; */
body { font-size: 20px; line-height: 200%; }    /* line-height = 40px; */
```

두 경우 모두 `<body>`에 40px라는 행간이 적용된다. 하지만 자식요소에 미치는 다르다. 아래를 코드를 확인해보자. 

```css
body { font-size: 20px; line-height: 2; }    /* line-height = 40px; */
p { font-size: 10px; }                       /* line-height = 20px; */

body { font-size: 20px; line-height: 200%; }    /* line-height = 40px; */
p { font-size: 10px; }                          /* line-height = 40px; */
```

이처럼, number은 부모 엘리먼트(태그)에서 계산된 값 대신 **비율**을 상속받고, %는 계산된 값을 그대로 상속받게된다. 글자 크기마다 행간 비유이 달라야 가독성이 편하겠죠? 때문에, %나 px와 같이 단위가 있는 값이 아닌, 단위가 없는 값을 사용하는 것이 좋다.

### 4. `font-size`

마크업 문서에서는 font-size는 가독성이나 명확한 구문을 표한할때 매우매우매우 중요한 속성이다. (본 블로그의 폰트 사이즈도 얼마나 많이 변경했는지 모를 일이다;) 기본값은 medium이다만... 이런 x-small 같은 경우 브라우저마다 값이 다르기 때문에 사용을 피하곤한다. 모든 브라우저에서 동일한 값을 제공해야하기 때문에 상대적인 것보다는 px나 em과 같은 더 명확한 고정 값을 많이 사용한다. (**요즘은 방응형을 위해 다른 단위를 사용하기도 한다.**)

```
absolute-size | relative-size | length| percentage | initial | inherit ;
```

- **absolute size** : medium(기본 값), xx-small, x-small, small, large, x-large, xx-large
- **relative-size** : smaller, larger
- **length** : px, em, rem 등 고정 수치로 지정.
  - **em** :  부모 요소의 font-size에 em 값을 곱한 크기 
  - **rem** : 루트의 font-size에 rem 값을 곱한 크기
- **percentage(%)** : 부모 요소의 font-size 기준의 퍼센트로 지정.

### 5. `font-weight`

이 속성은 글씨를 굵기를 표현하는 것이다.

```
 normal | bold | bolder | lighter | number | initial | inherit ;
```

- **normal** : 기본 값 (400)
- **bold** : 굵게 표현(700)
- **bolder** : 부모 요소 보다 두껍게 표현
- **lighter** : 부모 요소 보다 얇게 표현
- **number** : 100, 200, 300, 400, 500, 600, 700, 800, 900 (클수록 더 두껍게 표현)

실무에서는 목차 처럼 부모 요소에 영향을 받아야 하는 요소를 제외하곤 bolder와 lighter보다 normal과 bold를 더 많이 사용한다고 한다. `font-weight`는 폰트 자체에서 굵기를 지원해야 표현할 수 있다. 따라, 폰트에 따라 굵기에 변화가 없을 수도 있다.

- **normal과 bold만 지원하는 폰트일 경우** 
  - **normal** : 100~500
  - **bold** : 600~900

폰트가 다양해지면서 굵기 자체를 폰트 이름으로 가지고 있는 경우도 있고, 디바이스 별로 다르게 표현될 수도 있다.

### 6. `font-style`

글꼴의 스타일, 기울임 또는 이텔릭체를 표현하는 속성이다.

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL8/2021-01-14-HC-TIL8-3.png)

```
 normal | italic | oblique | initial | inherit;
```

- **normal** : font-family 내에 분류된 기본 값

- **italic** : italic 스타일.

- **oblique** : oblique 스타일. italic과는 달리 기울기에대한 각도를 지정할 수 있다.

  - **font-weight oblique <각도>;** : 유효한 값은 -90~90이며, 기본값은 14도이다.양수 값은 글의 끝 부분이 기울어지고, 음수값은 시작부분이 기울여진다. (CSS Fonts Module Level 4 지원하는 브라우저에서만 사용이 가능하다.)

대부분의 브라우저에선 italic 스타일과 oblique 스타일을 똑같은 형태로 표현하고 있다.

### 7. `font-variant`

`font-variant`속성은 문자 변환을 의미한다. 이 속성은 소문자를 대문자로 변환한다.  다만, 변환한 값은 실제 대문자 사이즈보다 더 작은 사이즈로 나타난다. 

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL8/2021-01-14-HC-TIL8-4.png)

```
normal | small-caps | initial | inherit ;
````

- **normal** : 기본 값
- **small-caps** : 소문자를 작은 대문자로 변형한다.


### 8. `font`

`font`속성은 축약 속성으로 `font-style`, `font-variant`, `font-weight`, `font-size`, `line-height`, `font-family`  속성들을  넣을 수 있다. 다만, 선언 순서는 꼭 지켜야 한다는 제약이 있다. 그리고, 축약 속성은 규칙이 많고 가독성이 좋지 않아서 선호하는 속성은 아니다.  그래도 사용하는 사람이 있으니, font로 선언된 속성을 보고 어떤 값들이 적용되어 있는지 해석할 수 있어야 한다. 순서는 다음과 같다.

```
font-style, font-variant, font-weight, font-size/line-height, font-family | initial | inherit;
```

이 축약형을 사용할 때는 다음 세가지 사항을 유의 해야한다. 

- `font-size`와 `font-family`는 반드시 선언해야 하는 필수 속성이다.
- 빠진 속성이 있다면 기본 값으로 지정된다.
- 각 속성의 선언 순서를 지켜야 한다.

### 9. `webfont`

실무에서 폰트 관련해서 주로 사용되는 명칭은 **시스템폰트**, **이미지폰트**, **웹폰트**가 있다. 

- **시스템폰트** : font-family로 선언한 글꼴이 사용자 시스템에 기본으로 설치 되어 있어 사용할 수 있는 경우.

- **이미지폰트** : 특정 글꼴을 사용하는 것이 아니라, 글자를 표현함에 있어서 시각적인 요소를 넣고 싶을 때 글꼴 대신 이미지를 사용하는 경우를 말한다.(*정확히 이야기하면 이미 폰트는 이미지이다. *) 

- **웹폰트(@FONT-FACE)** : 아예 다른 글꼴을 서버에 저장해서 제공하거나, 혹은 웹 경로를 가지고 와서 `import` 해서 제공하는 폰트를 의미한다. 혹은 사용자가 로컬 환경에 글꼴을 다운 받아 적용하는 것도 이에 해당한다. 

```css
@font-face {
    font-family: webNanumGothic; /* 사용자 지정 웹 폰트명 */
    src: url(NanumGothic.eot); /* 적용 될 웹 폰트의 경로 */
    font-weight: bold; /* 필요에 따라 지정 */
    font-style: italic; /* 필요에 따라 지정 */
}

body {
    font-family: webNanumGothic;
}
```
- **font-family(필수)** : 글꼴의 이름을 지정 
- **src(필수)** : 다운로드 받을 글꼴의 경로(URL) 
- **font-style(옵션)** : 글꼴의 스타일 지정, 기본 값은 normal 
- **font-weight(옵션)** : 글꼴의 굵기 지정, 기본 값은 normal



### 10. `vertical-align`와 `text-align`

CSS를 통해서 텍스트를 수직, 수평 정렬 할 수 있는데, **`vertical-align`는 수직 정렬을 할 수 있는 속성**이고, **`text-align`는 수평 정렬 속성**이다.

#### 10.1 `vertical-align`
. `vertical-align`는 **inline** 또는 **inline-block**에서만 적용할 수 있다. 즉, display 속성이 변하지 않는 block 요소에서는 적용할 수 없다.

```
 keyword | length | percent | initial | inherit ;
```
*앞서  `vertical-align` 속성을 설명할 때 나오는 baseline은 소문자 x를 기준으로한 글자의 하단 라인을 의미한다.*

- **keyword** : baseline(기본 값), sub, super, top, text-top, middle, bottom, text-bottom
  - **baseline(기본 값)** :
  - **sub** : 부모 아래 첨자 기준으로 정렬
  - **super** : 부모 위 첨자 기준으로 정렬 
  - **top** : 부모의 맨 위 위치
  - **text-top** : 부모 텍스트의 맨 위(Ascender 제외)
  - **middle** : 부모의 중앙에 위치
  - **bottom** : 부모의 맨 아래 위치
  - **text-bottom** :부모의 텍스트의 맨 아래(Descender 제외) 
- **length** : 요소를 지정한 길이만큼 올리거나 내림. px값 사용 시 baseline을 기준으로 이동하며, 음수 허용.
- **percent(%)** : 요소를 line-height를 기준으로 올리거나 내림. 음수 허용

#### 10.2 `text-align`

앞서 CSS를 통해서 텍스트를 수직, 수평 정렬 할 수 있다고 했다. `vertical-align`가 수직 정렬이라면, `text-align`는 수평 정렬에 사용된다. 이 속성 또한 block 요소에는 적용이되질 않는다.

```
 left | right | center | justify | initial | inherit ;
```

- **left** : 텍스트를 왼쪽으로 정렬
- **right** : 텍스트를 오른쪽으로 정렬
- **center** : 텍스트를 중앙으로 정렬
- **justify** : 텍스트를 라인 양쪽 끝으로 붙여서 정렬. (마지막 라인은 정렬 하지 않음)

`text-align`는 기본값은 문서의 읽는 방향에 따라 따라 다르다. 문서의 방향이 LTR(Left To Right)는 left, RTL(Right To Left) 일 경우에는 right가 기본값에 해당된다.

#### 10.2 block 요소의 정렬

`vertical-align`와 `text-align`는 block 요소에는 적용이 되지 않는다. 그렇다면 block 요소를 가운데 정렬을 할때는 어떻게 해야할까? [[HTML & CSS] TIL7의 박스 모델](https://riverpark94.github.io/PROGRAMING STUDY/2021/01/13/HtmlCss-TIL7/#24-boxmodel) 다룬 margin과 auto 값을 이용하면 된다. 

- **가운데 정렬** 
  - **인라인 요소** : text-align (center) 
  - **블럭 요소** :  margin (auto) 

### 11. `text-indent`

글을 읽다보면 새로운 문단의 시작에 들여쓰기를 많이 사용한다. 들여쓰기는 문단의 처음 시작점을 빈칸을 만들면서 가독성을 향상하는 효과가 있다. `text-indent` 속성은 문장의 첫 줄을 들여쓰기 할 수 있다. (*`text-indent`는 상속될 수 있다.*)

```
 length | percent | initial | inherit;
```

- **length** 
  - 문단의 첫 줄에 대한 들여쓰기를 수행한다
  - 음수 값을 사용할 수 있으며, 음수 값 사용 시 왼쪽으로 이동한다.
  - px, em 등 고정 수치로 지정
- **percent ( % ) **
  - 텍스트를 포함하는 컨테이너 블록의 부모 요소의 width를 기준으로한다.
  
  - 부모 요소의 width를 퍼센트로 지정
  
  - 부모의 width를 기준으로 변환된 백분율 값으로 들여쓰기 한다.

아래 코드에서 `.box`의 `text-indent`값은 **20px**에 해당한다. (부모의 width인 200px에 10%를 곱한 값이다.)

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Page title</title>
    <style>
      .wrap { width: 200px; height: 100px; border: 5px solid red; } 
      .box { width: 300px; text-indent: 10%; border: 10px solid black; }
    </style>
  </head>
  <body>
  <div class="wrap">
    <div class="box">Text-Indent ~ !</div>
  </div>  
  </body>
</html>
```


### 12. `text-decoration`

`<a>`는 기본적으로 텍스트에 밑줄이 그어져있지만, 브라우저에 따라 `text-decoration`속성의 기본값이 다르기 때문에 단순히 밑줄을 그어주는게 아니라 다양한 형태로 출력될 수도 있다.  

```
text-decoration-line, text-decoration-color, text-decoration-style | initial | inherit;

```

- **text-decoration-line** : 꾸밈의 <u>종류</u>를 지정하는 속성, 두 속성을 중복으로 사용할 수 있다. 다만, `text-decoration`속성은 의존적이기 때문에 위치 조정이 불가능하다.
  - **non** : 텍스트 꾸밈을 생성하지 않음 ( 기본값 )
  - **underline** : 밑줄로 꾸밈을 설정
  - **overline** : 윗줄로 꾸밈을 설정
  - **line-through** : 중간을 지나는 줄로 꾸밈을 설정 => 취소선처럼 보인다.
  
- **text-decoration-color** : 꾸밈의 <u>색상</u>을 지정하는 속성으로, 기본값은 currentColor이다. 
- **text-decoration-style** : <u>선의 스타일</u>을 지정하는 속성
  - **solid** : 한줄 스타일 ( 기본 값 )
  - **double** : 이중선 스타일
  - **dotted** : 점선 스타일
  - **dashed** : 파선 스타일
  - **wavy** : 물결 스타일

### 13. 단어 관련 속성

CSS에는 font 관련한 텍스트관련 속성뿐만 아니라, **단어**에 대해서도 적용할 수 있다. 단어의 공백, 단어사이 간격, 줄바꿈이 되는 지점 등을 제어할 수 있다.

#### 13.1 `white-space` 속성

공백을 어떻게 처리할지에 대한 속성이다.

```
normal | nowrap | pre | pre-line | pre-wrap | initial | inherit;
```

- **normal** : 공백과 개행을 무시하고, 필요한 경우에 자동 줄바꿈 발생. 기본 값

- **nowrap** : 공백과 개행을 무시하고, 자동 줄바꿈이 일어나지 않음.

- **pre** : 공백과 개행을 표현하고, 자동 줄바꿈이 일어나지 않음.

- **pre-line** : 공백은 무시하고, 개행만 표현. 필요한 경우에 자동 줄바꿈 발생.

- **pre-wrap** : 개행은 무시하고, 공백만 표현. 필요한 경우 자동 줄바꿈 발생

#### 13.2 `letter-spacing` 속성

자간을 지정하는 속성이다.

```
normal | length | initial | inherit;
```

- **normal** : 기본 값

- **length** : 길이만큼 자간을 지정. 음수 허용

#### 13.3 `word-spacing` 속성

단어간의 간격을 지정하는 속성이다.

```
normal|length|initial|inherit;
```

- **normal** : 기본 값

- **length** : 길이만큼 단어 사이의 간격을 지정. 음수 허용

#### 13.4 `word-break` 속성

영어지문을 보면 가끔 끝에서 잘려나가는 단어들 사이에 `-(하이픈)`을 쓰는 경우가 있다. 이렇게 단어가 라인의 끝에 나올 경우 어떻게 처리할지 지정하는 속성이다. 

```
normal | break-all | keep-all | initial | inherit;
```

- **normal** : 기본 값. 중단점은 공백이나  `-(하이픈)`(CJK는 음절)

- **break-all** : 중단점은 음절. 모든 글자가 요소를 벗어나지 않고 개행

- **keep-all** : 중단점은 공백이나  `-(하이픈)`(CJK는 그 외 기호도 포함)

#### 13.5 `word-wrap` 속성

요소를 벗어난 단어의 줄바꿈을 지정하는 속성이다.

```
normal|break-word|initial|inherit;
```

- **normal** : 기본 값. 중단점에서 개행

- **break-word** : 모든 글자가 요소를 벗어나지 않고 강제로 개행

