---
layout: post
title: '[HTML & CSS] TIL 6. CSS 이해하기(2)'
date: 2021-01-12 15:27:44 +0900
subtitle: 'CSS'
categories: DEVLOG
tags: HtmlCss
comments: true!
toc: trueㅈ
---

> 1. 구체성의 정의와 알아야하는 이유는 무엇인가?
> 2. 인라인 스타일의 구체성과 import의 구체성을 알아본다.
> 3. 전체선택자로 스타일을 적용하고, 특정 요소에 id 선택자를 이용해 스타일을 적용했을 때, 특정 요소의 자손의 스타일은 어떻게 적용되는가.
> 4. 캐스케이딩의 규칙을 쓰시오.
>

<br>

[boostcourse](https://www.boostcourse.org//)의 **[웹 UI 개발](https://www.boostcourse.org/web344)** 강의를 듣고 정리한 필기입니다. 😀 
{: .notice--warning}

<br>


# 1. 구체성(명시도)

선택자에는 어떤 규칙이 우선으로 적용되어야 하는지에 대한 규칙이 존재하고, 이것은 구체성이라고 부른다.  구채성은 선택자를 얼마나 명시적으로(구체적으로) 선언했느냐를 수치화한 것으로, 구체성의 값이 클수록 우선으로 적용된다. 

구체성은 **0, 0, 0, 0** 총 4개의 값으로 이루어져 있다. 값을 비교했을 때는 좌측에 있는 값부터 비교하며, 좌측 부분의 숫자가 클수록 구체성이 높다고 판단한다. **<u>구체성의 값이 높은 것 먼저 적용</u>**되기 때문에 이러한 구체성을 잘 알아야 스타일 규칙들을 정의할 때 실수를 하지 않는다.

-  **0, 1, 0, 0** : 선택자에 있는 모든 id 속성값

-  **0, 0, 1, 0** : 선택자에 있는 모든 class 속성값, 기타 속성, 가상 클래스

-  **0, 0, 0, 1** : 선택자에 있는 모든 요소, 가상 요소

-  **전체 선택자**는 0, 0, 0, 0을 가진다.

-  **조합자**는 구체성에 영향을 주지 않는다. (`>`, `+` 등)

```css
h1 { ... }  /* 0,0,0,1 */
body h1 { ... }  /* 0,0,0,2 */
.grape { ... }  /* 0,0,1,0 */
*.bright { ... }  /* 0,0,1,0 */
p.bright em.dark { ... }  /* 0,0,2,2 */
#page { ... }  /* 0,1,0,0 */
div#page { ... }  /* 0,1,0,1 */
```



### 1.1 인라인 스타일

아래의 코드를 보면 `id` 값이 tilte인  `<h1>`에 스타일이 두 번 선언되었다. `<head>`에 한번, 인라인 스타일 방식으로 한번. 이럴 경우 결과적으로는 "Hello world"에는 `color:blue`가 적용된다.   인라인 스타일의 구체성 값은 1, 0, 0, 0이며 규칙 중 가장 큰 구체성을 갖기 때문이다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      h1#title { color: red; }
    </style>
  </head>
  <body>
    <h1 id="title" style="color:blue">Hello world</h1>
    <div>Contents here
      <span>Here too!</span>
    </div>
  </body>
</html>
```

### 1.2 important

mportant 키워드는 별도의 구체성 값은 없지만, 모든 구체성을 무시하고 우선권갖는다. 때문에 아래 코드의 "Hello world"에는 `color:red`가 적용된다.  

```css
<!DOCTYPE html>
<html>
  <head>
    <style>
      h1#title { color: red !important; }
    </style>
  </head>
  <body>
    <h1 id="title" style="color:blue">Hello world</h1>
    <div>Contents here
      <span>Here too!</span>
    </div>
  </body>
</html>
```
<br>

# 2. 상속

상속은 말 그대로 부모가 가진 특성을 자식이 물려받는 개념이다. 즉, 특정요소의 자손까지 스타일이 적용된다는 것이다. 여기서 중요한것은 자식이 아니라 자손이다. 상속관계를 잘 이해하면 CSS의 생산성을 높일 수 있다.

### 2.1 상속되는 속성

아래 코드에서 `<em>`은 부모인 `<h1>`의 `color:gray`를 상속받는다. 상속은 자연스러워 보이지만,  박스 모델 속성(`margin`, `padding`, `background`, `border` 등)은 상속되지 않는다. 

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      h1 { color: gray; }
    </style>
  </head>
  <body>
    <h1>Hello <em>world</em></h1>
    <div>Contents here
      <span>Here too!</span>
    </div>
  </body>
</html>
```

### 2.1 상속되는 속성의 구체성

아래 코드는 `*(전체선택자)`를 이용해서 `color:red`를 적용했고, `id` 값이 title인 것(id 선택자)에게는 `color:gray`를 선언했다. 전체 선택자의 구체성은 0, 0, 0, 0이며, id 선택자의 구체성은 0, 1, 0, 1이기 때문에 `<h1 id = "title">`에는 `color:gray`를,  `<em>`에는  `color:red`가 적용된다. 그 이유는 상속된 속성은 아무런 구체성을 가지지 못하기 때문이다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      * { color: red; }
      h1#title { color: gray; }
    </style>
  </head>
  <body>
    <h1 id="title">Hello <em>world</em></h1>
    <div>Contents here
      <span>Here too!</span>
    </div>
  </body>
</html>
```

<br>

# 3. 캐스케이딩(cascading)

CSS가 어떠한 방식으로, 어떠한 규칙으로 문서에 적용 되는지를 정한 규칙이다. 위에서 배운 구체성도 케스케이딩 규칙의 하나이다. 

만약, 구체성이 같은 두 규칙이 동일한 요소에 적용된다면 어떻게 될까? `<h1>`은 `color: blue`가 적용된다. 

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      h1 { color: red; }
      h1 { color: blue; }
    </style>
  </head>
  <body>
    <h1>Hello world</h1>
    <div>Contents here
      <span>Here too!</span>
    </div>
  </body>
</html>
```

이유는 캐스케이딩이라는 영어 단어의 뜻과 연관이 되어있을 것이다. cascading은 폭포가 내려오는 모양처럼 ''단계적인''이라는 뜻을 가지고 있다. 구체성이 같은 규칙이 나오면 캐스케이딩의 규칙에 따라 움직인다.

- **규칙1** : 중요도와 출처

  **중요도**는 !important를 이야기하는데, 먼저 !important로 선언된 모든 규칙은, 선언되지 않은 규칙 보다 우선시한다.

  **출처**는 제작자와 사용자, 사용자 에이전트(user argent)로 구분하며 CSS 출처를 의미한다. **우선순의**는 다음과 같다.

    **1. 사용자 에이전트 스타일** : 사용자 !important CSS (거의 사용하지 않는다.)
    **2. 사용자 에이전트 스타일** : 제작자 !important CSS
    **3. 제작자 스타일** : 실제 사이트를 제작하는 개발자가 작성한 CSS
    **4. 사용자 스타일** : 일반 사용자가 자신이 직접 CSS를 만들어 적용한 것인데 지금은 잘 사용하지 않는다.
    **5. 사용자 에이전트 스타일** : 브라우저에서 기본적으로 제공하는 CSS

- **규칙2** : 구체성

- **규칙3** : 선언순서

