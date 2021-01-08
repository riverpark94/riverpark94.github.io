---
layout: post
title: '[HTML & CSS] TIL 4.콘텐츠모델, 시멘틱마크업, 블록 & 인라인'
date: 2021-01-08 18:57:44 +0900
subtitle: 'HTML 태그'
categories: DEVLOG
tags: HtmlCss
comments: true!
sitemap :
toc: true
changefreq : daily
---

> 1. HTML5에서 요소의 종류를 정의하는 규칙을 나열하고 설명하시오.
> 2. 제목, 단락 등과 같은 문서의 기본적인 요소를 나타내는 태그들을 설명하시오.
>
> 2. 텍스트를 꾸며주는 태그를 나열하시오.
>
> 3. 태그는 중첩이 가능한가요? 가능하다면, 모든 태그가 중첩이 가능한가요?
> 5. 중첩이 불가능한 태그가 있다면, 그 태그에 대해서 서술하시오.
>6. html의 기본 구조를 설명하세요.

<br>

[boostcourse](https://www.boostcourse.org//)의 **[웹 UI 개발](https://www.boostcourse.org/web344)** 강의를 듣고 정리한 필기입니다. 😀 
{: .notice--warning}

<br>

# 1. 콘텐츠모델(Content Models)

HTML5에는 요소들이 가지고 있는 성격에 따라 요소의 종류를 정의하는 규칙들이 있다. 이런 규칙들을 그룹화한 것이 콘텐츠 모델이다. 콘텐츠 모델의 종류로는 **<u>Metadata Content, Flow Content, Sectioning Content, Heading Content, Phrasing Content, Embedded Content, Interacitve Content</u>**, 이렇게 7개 이다. 

![title](/assets/img/DEVLOG/HTML & CSS/TIL4/2021-01-08-HC-TIL4-1.png)

위의 다이어그램이 콘텐츠 모델들의 관계를 잘 나타내 주고 있다. 각각의 HTML 요소는 하나 또는 여러 개의 콘텐츠모델에 속하게 된다. 비슷한 성격의 요소들끼리 그룹화되어있다. 우리가 지금까지 배운 테그들도 이 콘텐츠 모델에 속한다. 그럼 각, 콘텐츠 모델에 해당하는 태그가 무엇이 있는지 살펴보도록 한다.

### 1.1 Metadata Content

Metadata Content는 콘텐츠의 style(표현), scirpt(동작)를 설정하거나 다른 문서와의 관계 등의 정보를 포함하는 요소라고 정의한다. 특징은 이 태그 대부분이 `<head>` 태그 내에 들어간다는 것이다.

​	▶ `<meta>`,`<title>`,  `<style>`, `<script>`, `<base>`, `<link>`,  `<noscript>`, `<title>` 

![title](/assets/img/DEVLOG/HTML & CSS/TIL4/2021-01-08-HC-TIL4-2.png) 

### 1.2 Flow Content

Flow Content는 아래 다이어그램에서 보듯이 대부분의 요소가 해당된다.우리가 배웠던 태그들 모두가 여기에 해당된다. 앞으로 나올 Content들도 모두 Flow Content에 해당한다. 문서내에 자연스러운 흐름에 의해서 대체되는 요소들이다. 일부 Metadata Content 태그들만을 제외하고는 전부 Flow Content에 해당한다.

​	▶ `<a>`, `<abbr>`, `<address>`, `<article>`, `<aside>`, `<audio>`, `<b>`, `<bdo>`, `<blockquote>`, `<br>`, `<button>`, `<canvas>`, `<cite>`, `<code>`, `<datalist>`, `<del>`, `<details>`, `<dfn>`, `<div>`, `<dl>`, `<em>`, `<embed>`, `<fieldset>`, `<figure>`, `<footer>`, `<form>`, `<h1>` ~ `<h6>`, `<header>`, `<hgroup>`, `<hr>`, `<i>`, `<iframe>`, `<img>`, `<input>`, `<ins>`, `<kbd>`, `<keygen>`, `<label>`, `<map>`, `<mark>`, `<math>`, `<menu>`, `<meter>`, `<nav>`, `<noscript>`, `<object>`, `<ol>`, `<output>`, `<p>`, `<pre>`, `<progress>`, `<q>`, `<ruby>`, `<samp>`, `<script>`, `<section>`, `<select>`, `<small>`, `<span>`, `<strong>`, `<sub>`, `<sup>`, `<svg>`, `<table>`, `<textarea>`, `<time>`, `<ul>`, `<var>`, `<video>`, `<wbr>`

몇가지 요소들은 특정 조건이 충족되는 경우에만 해당된다.

- `<area>`:   `<map>`의 하위 항목인 경우

- `<link>` :  `itemprop` 속성이 있는 경우

- `<meta>` :  `itemprop` 속성이 있는 경우 

- `<style>` : `scoped` 속성이 있는 경우

![title](/assets/img/DEVLOG/HTML & CSS/TIL4/2021-01-08-HC-TIL4-3.png)

### 1.3 Sectioning Content

Sectioning Content는 문서의 구조, 특히 아웃라인과 관련된 요소들이 들어간다.  여기에 해당하는 태그 모두 HTML 5에서 부터 새로 생긴 태그들이 Sectioning Content에 해당한다.

​	▶ `<article>`, `<aside>`, `<nav>`, `<section>`등 

![title](/assets/img/DEVLOG/HTML & CSS/TIL4/2021-01-08-HC-TIL4-4.png) 

### 1.4 Heading Content

Heading Content는 Section의 헤더를 정의하는 요소이다.

​	▶ `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, `<h6>` 

![title](/assets/img/DEVLOG/HTML & CSS/TIL4/2021-01-08-HC-TIL4-5.png)

### 1.5 Phrasing Content

Phrasing Content는 문서의 텍스트 또는 텍스트를 꾸며주는 문단 내부 레벨로 사용되는 요소이다. 많은 태그가 여기에 해당된다. `<area>`는   `<map>`의 하위 항목인 경우에만 해당한다.

​	▶ `<abbr>`, `<audio>`, `<b>`, `<bdo>`, `<br>`, `<button>`, `<canvas>`, `<cite>`, `<code>`, `<datalist>`, `<dfn>`, `<em>`, `<embed>`, `<i>`, `<iframe>`, `<img>`, `<input>`, `<kbd>`, `<keygen>`, `<label>`,  `<mark>`, `<math>`, `<meter>`, `<noscript>`, `<object>`, `<output>`, `<progress>`, `<q>`, `<ruby>`, `<samp>`, `<script>`, `<select>`, `<small>`, `<span>`, `<strong>`, `<sub>`, `<sup>`, `<svg>`, `<textarea>`, `<time>`, `<var>`, `<video>`, `<wb>`

몇가지는 특정 조건이 충족되는 경우에만 해당된다.

- `<a>`:  phrasing content에만 포함된 경우
- `<del>`:  phrasing content에만 포함된 경우
- `<ins>`:  phrasing content에만 포함된 경우 
- `<map>` : phrasing content에만 포함된 경우
- `<area>`:   `<map>`의 하위 항목인 경우
- `<link>` :  `itemprop` 속성이 있는 경우
- `<meta>` :  `itemprop` 속성이 있는 경우

![title](/assets/img/DEVLOG/HTML & CSS/TIL4/2021-01-08-HC-TIL4-6.png)

 

### 1.6 Embedded Content


Embedded Content는 외부 콘텐츠를 표현하는 요소이다. `<audio>`, `<video>`, `<img>`와 같은 멀티 미디어 요소들이 여기에 해당한다. 다이어 그램에서 확인할 수 있듯이 Embedded Content는 모두 Phrasing Content이라고도 할 수 있다.

​	▶ `<audio>`, `<canvas>`, `<embed>`, `<iframe>`, `<img>`, `<math>`, `<object>`, `<svg>`, `<video>`

![title](/assets/img/DEVLOG/HTML & CSS/TIL4/2021-01-08-HC-TIL4-7.png)

### 1.7 Interacitve Content 

Interacitve Content은 사용자와 상호작용하는 요소들이 여기에 해당한다. 대표적으로 Form 요소들이 여기에 들어간다. 

​	▶ `<a>`, `<button>`, `<details>`, `<embed>`, `<iframe>`, `<keygen>`, `<label>`, `<select>`, `<textarea>`

몇가지는 특정 조건이 충족되는 경우에만 해당된다.

- `<audio>`:  `contrlols` 속성이 있는 경우

- `<video>`:  `controls` 속성이 있는 경우

- `<img>`:  `usemap` 속성이 있는 경우

- `<object>`:  `usemap` 속성이 있는 경우

- `<input>`:  `type` 속성이 숨겨진 상태가 아닌 경우

- `<menu>`:  `type` 속성이 도구 모음 상태인 경우

![title](/assets/img/DEVLOG/HTML & CSS/TIL4/2021-01-08-HC-TIL4-8.png)

<br>

***

# 2. 시멘틱마크업

웹을 시멘틱 웹, 또는 마크업 분야로만 한정 지으면 시멘틱 마크업이라는 말을 자주 들을 것이다. 시멘틱(Semantic)이라는 말은 "의미론적인"이라는 뜻을 가지고 있다. 시멘틱 마크업을 직관적으로 해석을 하면 의미론적인 마크업이라고 해야 할 것이다. 시멘틱 마크업은 종종 POSH(Plain Old Semantic HTML)라고도 불리기도 한다.

시멘틱은 한마디로 이야기하면 컴퓨터 (브라우저)가 잘 이해할 수 있는 코드를 이야기한다. 코드를 설명하기 전, 프로그래밍 언어는 사람과 기계와의 정해진 약속이며 HTML도 마찬가지이다. 예를 들어 문단을 작성할 때는 `` 를 사용하자.라고 약속된 것으로 생각하면 된다. 그러면 그 약속이라는 것은 무엇일까? 기본적으로 마크업을 할 때는 **¹ 의미에 맞는 요소를 사용**해야 하며, **² 문서를 작성할 때는 구조화를 잘해야** 한다. 그렇게 정해진 코드를 작성하면 **³인간과 기계 모두 이해하기 쉬운 코드**가 될 것이며, 이것 또한, 하나의 큰 목표이다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL4/2021-01-08-HC-TIL4-9.png)

위 코드를 보면 왼쪽( `<b>`, `<i>`, `<u>`, `<s>`)은 우리가 배운 코드이고, 오른쪽(`<strong>`, `<em>`, `<ins>`, `<del>`)은 배우지 않은 것이다. 왼쪽과 오른쪽은 데칼코마니를 한 것처럼 출력모양은 같지만, 그렇다고 의미까지 같은 것은 아니다.

`<b>` 는 글자를 굵게 만들어주는 것을 제외하면 다른 의미는 없다. 반면, `<strog>`은 애초에 글자를 굵게 해달라는 의미는 없지만, 중요한 부분을 강조해달라는 의미이기 때문에 브라우저가 기본 스타일을 굵게 표현한 것뿐이다. 출력되는 것이 같은데 왜 `<b>`와 `<strong>`태그를 분리할까? 그 이유는 컴퓨터에게 단순히 글자만 굵은 부분과 중요한 부분을 구분해주기 위함이다. 또, 다른 개발자가 코드를 열어봤을 때도 중요한 부분인지 아닌지 구분이 가능하다. 나머지 태그도 마찬가지라고 보면 된다. 여기서 **오른쪽(`<strong>`, `<em>`, `<ins>`, `<del>`)이 시멘틱 마크업**이라고 한다. 더 많은 시멘틱 요소는 [Semantics MDN](https://developer.mozilla.org/en-US/docs/Glossary/Semantics) 에서 확인할 수 있다.

<br>

***

# 3. 블록 레벨 &인라인 레벨

오늘 배웠던 컨텐츠 모델이전에 블록 레벨(Block Level)요소와 인라인 레벨(Inline Level) 요소로 구분을 했었다. 지금도 블록 레벨, 인라인 레벨로 많이 구분을 한다. 이유는 차이가 시각적으로 명확하기 때문이다.

### 3.1 블록 레벨 요소

이 요소는 기본적으로 부모 요소의 영역을 가로로 다 채워서 표현이 되고, 양옆으로 다른 요소가 배치되지 않도록 박스를 생성한다. 대표적으로   `<div>`, `<h1>` ~ `<h6>`, `<p>`, `<ul>`, `<li>`, `<table>` 이 있다. 

예외로   `<h1>` ~ `<h6>`(headings) 요소와 `<p>` 요소는 블록 레벨 요소지만, 내부 요소로 Phrasing Content만 허용한다.

 ![title](/assets/img/DEVLOG/HTML & CSS/TIL4/2021-01-08-HC-TIL4-10.png)

### 3.2 인라인 레벨 요소

인라인 레벨 요소는 하나의 라인 안에 자신의 내용만큼 박스를 만드는 요소이다. 라인의 흐름을 끊지 않고 요소 앞 뒤로도 줄바꿈이 되지 않아 다른 인라인 요소들이 자리할 수 있다. 대표적으로 `<span>`, `<i>`, `<img>`, `<em>`, `<strong>`, `<a>`가 있다.

 **인라인 레벨 요소는 블록레벨 요소의 자식으로 분류**되기 때문에 자손으로 인라인 레벨은 자식으로 블록레벨 요소를 가질 수 없다.  예외적으로 `<a>`는 인라인 레벨 요소지만 자손으로 블록 레벨 요소를 가질 수 있다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL4/2021-01-08-HC-TIL4-11.png)