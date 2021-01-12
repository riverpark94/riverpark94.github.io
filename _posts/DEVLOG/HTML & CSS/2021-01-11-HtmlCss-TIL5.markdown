---
layout: post
title: '[HTML & CSS] TIL 5. CSS 이해하기(1)'
date: 2021-01-11 18:57:44 +0900
subtitle: 'CSS'
categories: DEVLOG
tags: HtmlCss
comments: true!
toc: true
---

> 1. CSS의 구문과 적용 방식에 대한 이해.
> 2. 선택자의 종류
>

<br>

[boostcourse](https://www.boostcourse.org//)의 **[웹 UI 개발](https://www.boostcourse.org/web344)** 강의를 듣고 정리한 필기입니다. 😀 
{: .notice--warning}

<br>


# 1. CSS란

웹사이트를 만들 때 자주 사용되는 태그는 열 손가락으로 꼽을 수 있을 것이다. 그런데도 각각의 사이트는 저마다 개성을 가지고 있다. 이렇게 사이트에 개성을 줄 수 있는 것이 바로 CSS이다.

CSS는 Cascading Style Sheets의 약자이다. Style Sheets라는 말처럼 저번 주에 배웠던 마크업 언어(HTML)를 꾸며주는 역할을 한다. 여기에서 알 수 있는 것은 CSS와 HTML은 독립된 언어지만, 마크업 문서가 존재하지 않으면 CSS는 무용지물이나 마찬가지라는 것이다. 이러한 특징 때문에 CSS는 HTML과 묶어서 이야기하는 경우도 많다.

CSS는 HTML처럼 많은 속성과 그에 해당하는 값의 집합으로 이루어져있다. 다음 그림은 해당 블로그이 CSS 중 하나이다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL5/2021-01-11-HC-TIL5-1.png)

### 1.1 문법

CSS 문법에는 **선택자(selector), 속성(property), 값(value), 선언(delclaration), 선언부(delclaration block), 규칙(rule set)** 여섯가지의 특징이 있다. 여기서 **선언부(delclaration block)는 중괄혼에 묶여있는 속성과 값들을 말하고, 규칙(rule set)은 선언부(delclaration block) + 선택자(selector)를 말한다.** 그리고 속성과 값은 한 쌍으로 항상 같이 다니며, 속성과 속성값 사이에는 개행을 해주면 안된다. 여기서 선택자는 태그 이름, id 값, class 값 세가지로 이루어진다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL5/2021-01-11-HC-TIL5-2.png)

- 선택자(selector) - ".markdown-body pre"
- 속성(property) - "word-wrap"
- 값(value) - "normal"
- 선언(declaration) - "word-wrap: normal"
- 선언부(declaration block) - "{ word-wrap: normal; }"
- 규칙(rule set) - ".markdown-body pre { word-wrap: normal; }"

한국은 CSS의 Property와 HTML의 Attribute 를 모두 속성으로 해석한다. 이 두가지는 전혀 다른 것이다.
### 1.2 주석

```css
/* 이것은 주석입니다. */
/* 
  주석은
  개행도
  가능합니다.
*/
```
### 1.3 CSS 적용

css 를 HTML 문서와 연결하는 방법에는 4가지가 있다.

#### 1.3.1 Inline

해당 요소에 직접 스타일 속성을 이용해 선언하는 방법이다. 요소에 직접 입력하기 때문에  선택자 없이 선언부 내용을 스타일 속성의 값으로 넣어주면된다.

```html
<h1 style="color: red; font-style: italic">Hello world</h1>
```

#### 1.3.2 Internal

문서에 `<style>`을 활용한 방법이다. `<style>`은 마크업 문서의 `<head>` 부분에 들어가며, `<style>`안에 스타일 속성의 값을 넣어주면 된다.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Page title</title>
    <style>
      h1 {  /* 스타일은 h1 태그인 Hello world에만 적용된다. */
        color: red;
        font-style: italic;
      }
    </style>
  </head>
  <body>
    <h1>Hello world</h1> 
    <div>Contents here
      <span>Here too!<span>
    </div>
  </body>
</html>
```

#### 1.3.3 External

방법은 HTML 파일과 CSS 파일을 따로 작성하여 `<link>`를 이용해 적용하는 방법이다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL5/2021-01-11-HC-TIL5-3.png)

<center> <h5>
    index.html
    </h5></center>

```html
<!DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" type="text/css" href="indexStyle.css" />
  </head>
  <body>
    <h1>Hello world</h1>
    <div> hi </div>
  </body>
</html>
```

<center> <h5>
    index.html에 적용된 indexStyle.css
    </h5></center>
```css
h1 { color: red }
```

#### 1.3.4 Import

CSS 파일 내에 다른 CSS 파일을 불러오는 방식이다.

```css
@import url("css/style.css");
```


<br>

# 2. 선택자

완성도 있는 디자인을 위해서는 내가 원하는 디자인을 선택할 수 있어야 한다. 그렇기 때문에 CSS에서는 중요하다.

### 2.1 요소 선택자

요소 선택자는 태그 선택자라고도 불리며, CSS 선택자 중에 가장 기본이 되는 것이다. 요소 선택자는 **선택자 부분에 태그 이름이 들어간다.** 이렇게 태그를 선택자로 두개 되면, 마크업 문서 내의 해당하는 태그들에 선언한 스타일이 적용되게 된다.

```css
h1 { color: yellow; }
h2 { color: yellow; }
h3 { color: yellow; }
h4 { color: yellow; }
h5 { color: yellow; }
h6 { color: yellow; }
```

위의 코드를 보면 선언된 스타일이 모두 동일하다. 이럴 경우, 그룹화가 가능한데 `,(콤마)`를 이요해서 가능하다.

```css
h1, h2, h3, h4, h5, h6 { color: yellow; }
```

또,`*(별표, asterisk)`를 이용하여 한번의 선언 만으로 문서내의 모든 요소에 스타일 규칙을 적용할 수도 있다. 이를 전채 선택자라고 하며, 매우 편리하지만 성능이 좋지 않아 사용을 지양한다. 

```css
* { color: yellow; }
```

선택자 뿐만 아니라 선언들도 그룹화가 가능하다.  이때 언선들 사이에 `;(세미콜론)`으로 구분을 해줘야한다.

```css
h1 { 
    color: yellow; 
    font-size: 2em; 
    background-color: gray; 
}
```

선택자와 선언을 동시에 그룹화 하는 것도 가능하다.


```css
h1, h2, h3, 
h4, h5, h6 { 
    color: yellow; 
    font-size: 2em; 
    background-color: gray; 
}
```

### 2.2 class 선택자와 id 선택자

태그의 특정 내용에만 스타일을 입히려고 할때는 어떻게 해야할까? 요소 선택자를 사용하면 마크업 문서 내의 해당하는 모든 태그(요소)에 스타일이 적용되기 때문에 불가능하다.

예를 들어 아래 코드에서 HTML을 붉게 칠하고자 할때, `<dt>`와 `<span>`에 `color : red`라는 스타일을 선언해버리면, HTML 뿐만 아니라 CSS까지 빨간 글씨가 될 것이다. 이때 사용하는 것이 clss 선택자와 id 선택자 이다.

```html
<dl>
    <dt>HTML</dt>
    <dd><span>HTML</span>은 문서의 구조를 나타냅니다.</dd>
    <dt>CSS</dt>
    <dd><span>CSS</span>는 문서의 표현을 나타냅니다.</dd>
</dl>
```

#### 2.2.1 class 선택자

```html
<dl>
    <dt class = "HTML">HTML</dt>
    <dd><span class = "HTML">HTML</span>은 문서의 구조를 나타냅니다.</dd>
    <dt>CSS</dt>
    <dd><span>CSS</span>는 문서의 표현을 나타냅니다.</dd>
</dl>
```

class 선택자를 적용하기 위해서는 위의 코드처럼 태그 안에 `class`라는 속성을 입력해주어야 한다. 이렇게 `class` 를 속성을 선언해주면, 아래처럼 해당 `class`를 선택해 스타일을 적용할 수 있다.

```css
.HTML { color: yellow; }
```

**다중 class**라는 것도 존재한다. class는 여러 개의 값을 넣을 수 있다. 아래의 코드처럼 공백을 이용해 속성값을 입력해주면 `<dt> HTML </dt>` 에는 class가 두개가 존재한다.

```html
<dl>
    <dt class = "HTML title">HTML</dt>
    <dd><span class = "HTML">HTML</span>은 문서의 구조를 나타냅니다.</dd>
    <dt>CSS</dt>
    <dd><span>CSS</span>는 문서의 표현을 나타냅니다.</dd>
</dl>
```

아래의 css 코드 처럼 스타일을 입력하면 `<dt> HTML </dt>` 에는 노란색에 30px의 글짜로 출력이 되는 것이도, `<span>HTML</span>`는 글자색만 노란색으로 출력된다.

```css
.HTML { color: yellow; }
.title { font-size: 30px; }
```

#### 2.2.2 id 선택자

id 선택자는 class 선택자와 매우 비슷하다. 아래의 두 코드로 역시  `<dt> HTML </dt>` 에는 노란색에 30px의 글짜로 출력이 되는 것이도, `<span>HTML</span>`는 글자색만 노란색으로 출력된다.

```html
<dl>
    <dt class = "HTML" id = "title">HTML</dt>
    <dd><span class = "HTML">HTML</span>은 문서의 구조를 나타냅니다.</dd>
    <dt>CSS</dt>
    <dd><span>CSS</span>는 문서의 표현을 나타냅니다.</dd>
</dl>
```

```css
.HTML { color: yellow; }
.title { font-size: 30px; }
```

#### 2.2.3 class와 id의 차이점

- **id**
  - 사용 기호 : `#(해시)`
  - 문서 내에서 딱 한번만 사용한다. (유일)
- **class**
  - 사용기호 :  `.(온점)`
  - 문서 내에서 여러번 사용 가능하다.

### 2.3 속성 선택자

[요소선택자]()와 [class 선택자, id 선택자]()는 각각 태그, class, id 하나의 선택자만을 사용해서 요소를 선택했다. 사실, 선택자는 종류에 상관없이 여러가지 선택자들을 조합할 수 있다.

```css
/* 요소와 class의 조합 */
p.bar { ... }
.bar p { ... }

/* 다중 class */
.foo.bar { ... }

/* id와 class의 조합 */
#foo.bar { ... }
```

#### 2.3.1 단순 속성값으로 선택

속성 선택자는 대괄호를 이용해서 선언하며 대괄호 안에 속성 이름이 들어간다. (`태그[태그 속 속성] { 스타일 내용 }`)

`dt[class]`는 `<dt>`이면서 `class`속성이 있는 요소에 `color: silver `규칙이 적용된다. `span[class][id]`는 `<span>`이면서 `class`속성과 `id` 있는 요소에 `color: silver `규칙이 적용된다.

```css
dt[class] { color: silver; }
span[class][id] { text-decoration: underline; }
```

위 코드를 실행하면 `<dt class = "HTML title">HTML</dt>`는 글씨 색이 은색으로 출력될 것이고, `<span class = "HTML" id = "explanation">은 문서의 구조를 나타냅니다.</span>`는 밑줄이 그어진 채로 출력될 것이다.

```html
<dt class = "HTML title">HTML</dt>
    <dd><span class = "HTML">HTML</span>
        <span class = "HTML" id = "explanation">은 문서의 구조를 나타냅니다.</span>
	</dd>
```

#### 2.3.2 정확한 속성값으로 선택

정확한 속성값으로 선택은 `선택자[속성=값] { 스타일 내용 }` 이런 형태로 적용할 수 있다.

`dt[class = "title"]`는 `<dt>`이면서 `class`속성의 값이 `title`인 요소에는 `color: silver `규칙이 적용된다. `span[class][id]`는 `<span>`이면서 `id` 의 값이 `explanation`인 요소엔  `color: silver `규칙이 적용된다.

```css
dt[class = "title"] { color: silver; }
span[id = "explanation"] { text-decoration: underline; }
```

`<dt class = "HTML title">HTML</dt>`는  은색으로 칠해진 글자로 출력되고, `<span class = "HTML" id = "explanation">은 문서의 구조를 나타냅니다.</span>`는 밑줄이 그어진 채로 출력될 것이다.

```html
<dt class = "HTML title">HTML</dt>
    <dd><span class = "HTML">HTML</span>
        <span class = "HTML" id = "explanation">은 문서의 구조를 나타냅니다.</span>
	</dd>
```

정확한 속성값은 아래와 같은 형태로도 쓸 수 있다.

```css
.title dt { color: silver; }
#explanation span { text-decoration: underline; }
```

#### 2.3.3 부분 속성값으로 선택

부분 속성값으로 선택은 속성이름과 속성값 사이에 사용되는 기호에 따라 동작이 다르다.

- **[class~="bar"]** : class 속성의 값이 공백으로 구분한 "bar" 단어가 포함되는 요소 선택
- **[class^="bar"]** : class 속성의 값이 "bar"로 시작하는 요소 선택
- **[class$="bar"]** : class 속성의 값이 "bar"로 끝나는 요소 선택
- **[class*="bar"]** : class 속성의 값이 "bar" 문자가 포함되는 요소 선택

```html
<dt class = "HTML title">HTML</dt>
<dt class = "HTML explanation">HTML</dt>
<dt class = "HTMLtitle explanation">HTML</dt>
```


```css
p[class~="HTML"] { font-style: italic; } /* 1, 2번째 요소 */
p[class^="HTML"] { font-style: italic; } /* 1, 3번째 요소 */
p[class$="HTML"] { font-style: italic; } /* 2번째 요소 */
p[class*="HTML"] { font-style: italic; } /* 1, 2, 3번째 요소 */
```
