---
layout: post
title: '[HTML & CSS] TIL 2. HTML 태그(1)'
date: 2021-01-06 20:20:44 +0900
subtitle: 'HTML 태그'
category: PROGRAMING_STUDY
tags: HtmlCss
comments: true
toc: true
---

> 1. 제목, 단락 등과 같은 문서의 기본적인 요소를 나타내는 태그들을 설명하시오.
> 2. 텍스트를 꾸며주는 태그를 나열하시오.
>3. 앵커요소에서 반드시 가지고 있어야 하는 속성을 말하시오.
> 5. 링크를 새 창에 표시하고 싶으면 어떤 속성을 써야 하는가?
>6. 의미가 없는 컨테이너 요소는 존재하는 이유는 뭘까요?
> 6. 리스트 요소를 나열하고 그 특징을 설명하시오.
> 7. 이미지 요소의 속성을 나열하고 특징을 설명하시오.

<br>

[boostcourse](https://www.boostcourse.org/)의 **[웹 UI 개발](https://www.boostcourse.org/web344)** 강의를 듣고 정리한 필기입니다. 😀 
{: .notice--warning}

<br>


태그의 갯수는 약 130여 개가 존재한다. 이 많은 태그를 모두 설명하고 공부할 수 없기떄문에 많이 사용되는 강의 위주로 정리될 것이다. [태그관련 통계 사이트](https://www.advancedwebranking.com/html/#overview)를 보면 실제로 대다수의 웹페이지는 대략 25개 정도의 서로 다른 태그가 사용된다고 한다. 

<br>

***

# 1. 제목과 단락 요소

### 1.1 제목(Heading ) 태그 : `h1`~`h6`

Heading 태그는 문서내에서 제목을 표현할 때 사용하는 태그이다. 태그이름은 줄여서 `<h>`로 나타낸다. 제목의 레벨에 따라서 `<h1>` ~ `<h6>`까지 있다. 

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL2/2021-01-06-HC-TIL2-1.png)

숫자가 작을 수록 글자가 커지고, 숫자가 커질 수록 글자 크기는 작아진다. 

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL2/2021-01-06-HC-TIL2-2.png)

이 태그들을 한 줄에 쓰더라도 자동으로 줄 바꿈이 되어 첫 번째 그림과 결과 같은 완전히 같다.

그리고 `<h>` 태그는 HTML5 이후부터 속성이 없다. HTML5 이전에는 align 속성이 있어 정렬할 수 있었지만, 이제는 `<h>` 태그의 내용은 정렬할 수 없다. 없어진 이유는 CSS에 똑같은 의미가 있는 `text-align`이 있어 없어진 것으로 생각해도 된다.

### 1.2 단락(Paragraph) 태그 : `p`

단락 태그는 단락에 해당하는 영어 Paragraph를 둘여서 `p`로 쓴다. 

<center> <h5>
    p 태그를 사용하지 않은 것
    </h5></center>

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL2/2021-01-06-HC-TIL2-3.png)

<center> <h5>
    p 태그를 사용한 것
    </h5></center>

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL2/2021-01-06-HC-TIL2-4.png)

브라우저 상에는 별다른 변화는 없지만, 단락이 두개, 세개가 되면 단락 간의 간격(개행)이 넓어지는 것을 확인할 수 있다. 뿐만아니라 HTML 문서, 내부적으로 보면 의미에 맞게 잘 짜여진 마크업 구조라는 것을 볼 수 있다. 이는 개발자끼리 코드를 읽을 때 중요하다. 모든 내용을 다 읽을 수 없으니 태그를 보고 어떤 목적으로 쓰여진 내용인지를 파악할 수 있기 때문이다.


### 1.3 개행 (Linebreak 태그) : `br`

`<p>` 태그를 사용하여 단락을 구분하면 자연스럽게 개행이 된다. 그렇다면 `<p>` 안에서 임의로 개행을 하려면 어떻게 해야할까? `<br>` 태그를 사용하면 된다.  `<br>` 태그는 닫는 태그와 내용이 존재하지 않는 빈 태그이다. 개행하고자 하는 곳에서 `<br>`  태그를 선언하면 개행이된다. 

<center> <h5>
    br 태그를 사용안했을 때
    </h5></center>

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL2/2021-01-06-HC-TIL2-4.png)

<center> <h5>
    br 태그를 사용했을 때
    </h5></center>

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL2/2021-01-06-HC-TIL2-5.png)

<br>

***

# 2. 텍스트를 꾸며주는 요소

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL2/2021-01-06-HC-TIL2-6.png)

- `<b>` : bold 태그. 글자를 굵게 표현하는 태그
- `<i>` : italic 태그. 기우림꼴을 표현하는 태그
- `<u>` : underline 태그. 밑줄을 표현하는 태그
- `<s>` : strike 태그. 글자의 중간선을 표현하는 태그. (예전에 존재했던 strike 태그와는 다른 태그로, strike 태그는 폐기되어 더는 사용할 수 없습니다.)

<br>

***

# 3. 앵커(anchor) 요소

HTML에서 HT(Hyper Text)는 링크를 의미한다. 앵커 태그(`<a>`)는 이런 링크를 생성하는 태그로, 앵커 태그를 이용하여 다른 페이지로 이동하거나, 현재 페이지 내에서 특정 위치로 초점을 이동시킬 수 있다. 

###   3.1 `href` 속성  

```html
<a href="http://www.naver.com/">네이버</a>
```

`<a>`에는 반드시 가지고 있어야 하는 속성이 있는데, 바로 url을 값으로 입력 받는 `href`라는 속성이다. `href`는 hypertext reference의 약자이다.

###   3.2 `target` 속성

```html
<a href="http://www.naver.com/" target="_blank">네이버</a>
```

`target`이라는 속성은 리소스를 표시할 장소를 나타내는 속성이며, `href`완 달리 선택적으로 사용이 가능하다. 속성값으로는 `_self`, `_blank`, `_parent`, `_top` 이 있다.

- `_self` : 현재 화면에 표시하는 속성으로, `target` 속성이 생략되면 기본적으로 셋팅되는 값이다.
- `_blank` : 새창에 표시하는 속성
- `_parent` : 프레임이라는 특정 조건에서만 동작하는 속성
- `_top`  : 프레임이라는 특정 조건에서만 동작하는 속성

###   3.3 **기타 속성**

`<a>` 태그의 다른 속성들은 [MDN `<a>`태그 글](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a)을 참고하기를 바란다.

###   3.4 **내부링크**

가끔 웹페이지를 가보면 "맨위로 가기 버튼"이 있을 것이다. 이것은 어떻게 작동을 할까? 여러가지 방법이 있겠다만은 `<a>` 태그를 통해서도 가능하다. 

`<a>` 태그는 꼭 외부 페이지로만 이동하는 것은 아니다. `href` 속성값에 `#`을 쓰고 그 뒤에 페이지 내에서 이동하고자 하는 요소의 `id`를 속성 값에 적으면 된다.

```html
<a href="#some-element-id">회사 소개로 이동하기</a>

<h1 id="some-element-id">회사 소개</h1>
```

<br>

***

# 4. 의미가 없는 컨테이너 요소

###   4.1 의미가 없는 컨테이너 요소

의미가 없는 컨테이너 요소란, **태그 자체에 아무 의미가 없**으며, 단순히 요소들을 묶기 위해 사용되는 태그이다. HTML은 정보를 ***문서***로 전달하기 위해 개발된 것이다. 최근에는 글보다는 시각적으로 정보를 표현하는 방식으로 발전했다. **시각적으로 정보**를 전달하는 방법에는 다양한 방법이 있기 때문에 태그들로 표현하기에는 부족한 순간이 있다. 그때 사용하는 것이 의미가 없는 컨테이너 요소이다. 가장 대표적으로 많이 쓰이는 태그는 `<div>`, `<span>`이다.

###   4.2 `<div>`태그와 `<span>`태그

```html
<div>div 태그는 한 줄을 차지합니다</div>
<div>division 2</div>
<span>span 태그는 컨텐츠 크기만큼 공간을 차지합니다</span>
<span>span 2</span>
<span>span 3</span>
<div>division 3</div>
```

`<div>` 태그는 한 줄을 차지하는 반면(블록 레벨 태그), `<span>` 태그는 콘텐츠 크기만큼의 공간을 차지(인라인 레벨)한다. 에디터를 이용해서 html 파일을 만든 후 콘솔 창으로 보면 구조를 한눈에 파악할 수 있다.

![title](/assets/img/JS-TIL/TIL7/2020-05-20-JS-TIL7-4.png){: .center}

`<div>` 태그는 전체 한 줄을 차지하는 것을 볼 수 있다.

![title](/assets/img/JS-TIL/TIL7/2020-05-20-JS-TIL7-5.png){: .center}

`<div>` 태그보다 `<span>` 태그는 그 컨텐츠의 크기만큼 차지한다. 

이처럼 `<div>` 태그와 `<span>` 태그의 큰 차이점은 한 줄을 먹느냐 안 먹느냐의 차이다. 물론 CSS를 이용해서 span 태그건, `<div>` 태그건 한 줄을 차지하게끔 만들 수 있고, 아니게 만들 수 있다. 자유롭게 스타일링 할 수 있지만, 기본값은  `<div>` 태그는 한 줄이고, `<span>` 태그는 콘텐츠 크기이다. 

<br>

***

# 5. 리스트 요소

리스트는 일련된 항목들이 나열된 것을 의미한다. 

###   5.1 `<li>`

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL2/2021-01-06-HC-TIL2-7.png)

 `<li>`는 list의 줄임말이다. 

###   5.2 `<ul>`

 `<ul>`는 unordered list의 줄임말이다.  

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL2/2021-01-06-HC-TIL2-7.png)

순서가 없는 리스트를 표현할 때 사용하기 때문에, `<ul>`로 감싸면 위처럼 머리 기호에 'ㆍ'이 붙는다.

###   5.3 `<ol>`

 `<ol>`는 ordered list의 줄임말이다.  

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL2/2021-01-06-HC-TIL2-8.png)

순서가 있는 리스트를 표현할 때 사용하기 때문에, `<ol>`로 감싸면 위처럼 머리 기호에 넘버링이 붙는다.

###   5.4 `<dl>`

 `<dl>`는 definition/description list의 줄임말이다.  용어와 그에 대한 정의를 표현할 때 사용한다.  'ㆍ'와 넘버링이 붙는 `<ul>`과 `<ol>`와는 구조가 조금 다르다. `<ul>`과 `<ol>`는 항목을 단순히 나열하는 구조지만, `<dl>`은 용어와 설명이 하나의 세트로 항목을 이루고 하나 이상의 항목으로 리스트가 이루어지는 구조이다.

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL2/2021-01-06-HC-TIL2-9.png)

- <dt> : 용어를 나타내는 태그

- <dd> : 용어에 대한 정의 또는 설명을 나타내는 태그

용어 하나에 여러 정의가 들어갈때, `<dd>`를 한 개 이상 쓰는 것이 가능하다.

<br>

***

# 6. 이미지 요소

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL2/2021-01-06-HC-TIL2-10.png)

`<img>` 태그는 사진을 삽입하고 싶을때 사용하며 닫는 태그가 존재하지 않는다.

###   6.1 `src` 속성

`src`는 필수 속성으로 이미지의 경로(url)을 나타내는 속성이다.

###   6.2 `alt` 속성

![title](/assets/img/PROGRAMING STUDY/HTML & CSS/TIL2/2021-01-06-HC-TIL2-11.png)

`alt`는 이미지의 대체 텍스트를 나타내는 속성이다. `src`속성에 있는 url을 수정하고 나면 이미지가 읽히지 않고 대신 `alt` 속성의 값인 'title'이 화면에 출력된다. 이것은 웹 접근성 측면에서 중요한 속성이며 `src` 속성과 더불어 필수 속성이다.

###   6.3 `width`/`height` 속성

이미지의 가로/세로 크기를 나타내는 속성이다. 값의 단위는 px, % 등 원하는 단위로 계산되며, 단위가 없으면 자동으로 픽셀 단위로 계산된다. `width`/`height` 속성이 없으면 이미지는 원본 크기대로 노출되며, 둘 중 하나만 선언하면 나머지 한 속성은 선언한 속성의 크기에 맞춰서 자동으로 비율에 맞게 변경된다. 반면, 두 속성 모두 선언하면 이미지의 비율과 무관하게 크기가 변한다.

###   6.4 상대경로와 절대경로

- **상대경로** : 현재 웹 페이지를 기준으로 상대적으로 이미지의 위치를 나타내는 경로이다.

- **절대경로** : 실제 그 이미지가 위치한 곳의 전체 경로이다.

