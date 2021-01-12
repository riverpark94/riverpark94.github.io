---
layout: post
title: '[HTML & CSS] TIL 3. HTML 태그(2)'
date: 2021-01-07 18:57:44 +0900
subtitle: 'HTML 태그'
categories: DEVLOG
tags: HtmlCss
comments: true
toc: true
---

> 1. `<table>`의 기본 구조를 설명하세요.
>
> 2. 폼 요소에 해당하는 태그를 나열하시오.
>
> 3. `<input>`에서 사용하는 속성을 나열하고 설명하시오.

<br>

[boostcourse](https://www.boostcourse.org/)의 **[웹 UI 개발](https://www.boostcourse.org/web344)** 강의를 듣고 정리한 필기입니다. 😀 
{: .notice--warning}

<br>

태그의 갯수는 약 130여 개가 존재한다. 이 많은 태그를 모두 설명하고 공부할 수 없기떄문에 많이 사용되는 강의 위주로 정리될 것이다. [태그관련 통계 사이트](https://www.advancedwebranking.com/html/#overview)를 보면 실제로 대다수의 웹페이지는 대략 25개 정도의 서로 다른 태그가 사용된다고 한다. 

<br>

# 1. 테이블 요소

테이블 표는 테이터를 표로 나타낼때 사용되는 태그로 `<table>` 이와 같은 형태로 쓰인다.

### 1.1 표의 구성요소

아래에는 표가 있다. 표에는 내용이 들어가는 칸이 있는데, 이것을 셀이라고 표현하고, 가로방향을 row(행), 세로방향을 column(열)이라고 한다.

|      |      |      |
| ---- | ---- | ---- |
|      |      |      |
|      |      |      |
|      |      |      |


- `<table>` : 표를 나타내는 태그
- `<tr>` : 행을 나타내는 태그
- `<th>` : 제목 셀을 나타내는 태그
- `<td>` : 셀을 나타내는 태그

 `<table>` 태그는 하나 이상의 `<tr>`로 이루어져 있다. `<tr>`은 `<th>`와 `<td>`를 자식으로 갖게 된다. 4X4표를 만들려면 코드를 어떻게 작성해야할까.

```html
<table>
    <tr>
        <td>1</td>
        <td>2</td>
        <td>3</td>
        <td>4</td>
    </tr>
    <tr>
        <td>5</td>
        <td>6</td>
        <td>7</td>
        <td>8</td>
    </tr>
    <tr>
        <td>9</td>
        <td>10</td>
        <td>11</td>
        <td>12</td>
    </tr>
    <tr>
        <td>13</td>
        <td>14</td>
        <td>15</td>
        <td>16</td>
    </tr>
</table>
```

 1부터 16을 써서, 4X4 표를 나타내는 코드이다. 위 코드에 대한 결과 같은 아래 그림과 같다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-1.png)

우리에게 익숙한 표랑 달리 테두리가 없어서 어색해 보일 수 있다. 브라우저에서 제공하는 테이블은 테두리가 없는 것이 기본이기 때문이다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-2.png)

위의 표처럼 셀이 테두리를 가지기 뒤해선, css 코드를 `<head>`안에 테두리를 주고싶은 태그에 ` { border: 1px solid; }` 속성을 입력해야한다.

```html
<head>
  <style>
    th, td { border: 1px solid; }
  </style>
</head>

<body>
   <table>
      <tr>
          <td>1</td>
          <td>2</td>
          <td>3</td>
          <td>4</td>
      </tr>
      <tr>
          <td>5</td>
          <td>6</td>
          <td>7</td>
          <td>8</td>
      </tr>
      <tr>
          <td>9</td>
          <td>10</td>
          <td>11</td>
          <td>12</td>
      </tr>
      <tr>
          <td>13</td>
          <td>14</td>
          <td>15</td>
          <td>16</td>
      </tr>
  </table>
</body>
```

 입력해주면 아래와 같은 표가 된다.



### 1.2 표의 구조와 관련된 태그

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-3.png)

표에는 테두리 선만 있는게 아니라, 표 제목도 있고, 열 제목도 존재한다. 그러한 표의 구조를 표현하기 위한 태그는 다음과 같다.

- `<caption>`: 표의 제목을 나타내는 태그
- `<thead>`: 제목 행을 그룹화하는 태그
- `<tfoot>`: 바닥 행을 그룹화하는 태그(`<tfoot>`라는 태그는 HTML의 버전에 따라 위치가 변동되지만, 가장 최근 버전(HTML 5.2)에서는 `<tbody>`뒤에 있어야 맞다.)
- `<tbody>`: 본문 행을 그룹화하는 태그

```html
<head>
  <style>
    th, td { border: 1px solid; }
</style>
  
</head>

<body>
   <table>
    <caption>Monthly Savings</caption>
    <thead>
        <tr>
            <th>Month</th>
            <th>Savings</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>January</td>
            <td>$100</td>
        </tr>
        <tr>
            <td>February</td>
            <td>$80</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Sum</td>
            <td>$180</td>
        </tr>
    </tfoot>
  </table>
</body>
```

### 1.3 셀 병합 : `colspan`, `rowspan`

표를 보다보면 행병합, 열병합이 되어있는 것을 볼 수 있다. 

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-4.png)

셀 병합에서는 태그가 아니라 속성을 이용하게 된다.

- `colspan`: 셀을 가로 방향으로 병합하는 속성
- `rowspan`: 셀을 세로 방향으로 병합하는 속성

```html
<head>
  <style>
    th, td { border: 1px solid; }
</style>
  
</head>

<body>
   <table>
    <caption>Monthly Savings</caption>
    <thead>
        <tr>
            <th>Month</th>
            <th>Savings</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>January</td>
            <td>$100</td>
        </tr>
        <tr>
            <td>February</td>
            <td rowspan = "2">$80</td>
        </tr>
        <tr>
            <td>February</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan = "2">Sum</td>
        </tr>
    </tfoot>
  </table>
</body>
```

### 1.4 기타 관련 속성 

- `<colgroup>` : 테이블에서 서식 지정을 위해 하나 이상의 열을 그룹으로 묶을 때 사용. `<rowgroup>`은 존재하지 않음
- `<col>` : <colgroup>의 자식 태그로  열에 속하는 칸에 공통된 의미를 부여할 때 사용(css 등으로 해당 항목 강조 및 활용)
- `scope` 속성
  - 복잡한 표의 경우 `<th>`, `<tr>` 요소의 구분을 통하여 행과 열의 범위 지정
  - `scope="col"`을 선언함으로써, 해당 칸이 열의 맨 위에 위치함을 설명
  - `scope="row"`를 추가하면 해당 칸이 행의 맨 앞에 위치함을 설명
- `header` 속성 
  - 복잡한 표의 경우 `<th>`, `<tr>` 요소의 구분을 통하여 접근성을 용이하기 위한 범주화
  - `header`를 통한 카테고리화 작업 + `id`를 통한 고유 식별자 구분을 통해 표의 각 칸을 연관된 헤더 칸과 직접 연결하여 설명

<br>

***

# 2. 폼 요소

폼 요소는 사용자가 서버에게 데이터를 전달할 때 사용된다. 이해가 어렵다면 로그인 창에서 아이디와 비밀번호를 입력하는 것을 떠올리면 개념 이해가 쉽다. 아이디와 비밀번호는 사용자의 정보 즉, 데이터이기 때문이다. 이외에도 검색창 등을 떠올리면 된다. 우리는 입력 폼 태그로는 `<input>`, `<textarea>` 등 다양하고, 그 속성에는 `radio` , `chackBox` 가 있다.

### 2.1 `<input>` 태그

`<input>`태그는 화면에 텍스트 박스를 띄우고, 그 박스에는 사용자 서버에 전달하고자 하는 내용을 입력 할 수 있다. `<input>`은 내용이 없는 빈 태그이며 필수 속성인 `type`을 통해 여러 종류의 입력 양식을 화면에 출력한다. `type`에는 여러가지 속성 값이 존재한다.

#### 2.1.1 `type` 속성값 1 : `text`

주로 아이디, 이름, 주소, 전화번호 등 단순한 텍스트를 입력할 때 사용한다. `text`에는 `placeholder`이라는 속성이 존재하는데, 이것은 사용자가 입력하기 전 미리 화면에 노출되는 값이다. 

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-5.png)

```html
<div> ID
    <input type="text" placeholder="ID를 입력하세요.">
</div>
```

#### 2.1.2 `type` 속성값 2 : `password` 

패스워드 같이 공개할 수 없는 내용을 입할 때는 속성 값을 `password`으로 해주면 된다. 아래의 예시에는 두 입력창에는 같은 값을 입력했지만 `type = password`로 되어있는 입력창은 ***로 나타난다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-6.png)

```html
<div> ID
    <input type="text" placeholder="ID를 입력하세요.">
</div>
<div> password
    <input type="password`">
</div>
```

#### 2.1.3 `type` 속성값 3 : `checkbox`

checkbox는 ID 기억하기, 저장 유지하기 등에 사용된다. 물론 아직 이 기능은 안 되지만 form은 만들 수 있다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-7.png)

```html
<div> ID
    <input type="text" placeholder="ID를 입력하세요.">
</div>
<div> password
    <input type="password">
</div>
<div> 
    <input type="checkbox" name="ID save">
  다음에 돌아올 때 ID 기억하기
</div>
```

#### 2.1.4 `type` 속성값 4 : `radio` 

버튼과 체크박스의 차이는 체크 박스는 복수 선택이 가능하지만, 라디오 버튼은 불가능하다는 것이다. 그룹 설정이 가능하다. 쉽게 이야기해서 라디오 버튼은 그룹 설정이 가능하고, 체크 박스는 자유롭게 여러 개를 선택할 수 있다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-8.png)

```html
<input type="radio" name="gender"> 남자
<input type="radio" name="gender"> 여자
```

#### 2.1.5 `type` 속성값 5  : `checked`와 `name ` 속성 

이것은 `checkbox`와 `radio` 에만 있는 속성이다.

- `checked` 속성 : 값이 별도로 존재하지 않는 boolean 속성이다. 속성을 명시하지 않으면 속성값이 자동으로 false 값을 가지게 되며, 명시하면 자동으로 true 값을 가지게 된다. `checked`가 있으면 출력시 체크가 되어있고, 없으면 체크가 되어있다.

- `name ` 속성 : 라디오 버튼과 체크박스를 그룹화시켜주는 속성이다. name의 값이 같은 태그 끼리 그룹으로 묶인다. 
<center> <h5>
    name 속성이 다를 때 
    </h5></center>

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-9.png)

```html
<input type="radio" name="male"> 남자
<input type="radio" name="female"> 여자
```
<center> <h5>
    name 속성이 같을 때 
    </h5></center>

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-8.png)

```html
<input type="radio" name="gender"> 남자
<input type="radio" name="gender"> 여자
```

#### 2.1.6 `type` 속성값 6  :`file`

서버에 파일을 올릴 때 사용한다. CSS와 브라우저에 따라 출력되는 형태는 다를 수도 있지만, 모두 같은 역할을 한다. 

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-10.png)

```html
<input type="file">
```

#### 2.1.7 `type` 속성값 7  :`submit`|`reset`|`image`|`button`

`submit`|`reset`|`image`|`button`는 모두 클릭 버튼을 만드는 것이다.

- `submit` : form의 값을 전송하는 버튼
- `reset` : form의 값을 초기화하는 버튼
- `image` : 이미지를 삽입할 수 있는 버튼 (`submit`과 동작이 동일함), `src`와 `alt` 속성이 필수 속성이며 이미지 태그와 같이  `width`/`height` 속성을 적용할 수 있다.
- `button` : 아무 기능이 없는 버튼

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-11.png)

```html
<form action="./test.html">
    메시지: <input type="text" name="message"><br>
    <input type="submit">
    <input type="reset">
    <input type="image" src="http://placehold.it/50x50?text=click" alt="click" width="50" height="50">
    <input type="button" value="버튼">
</form>
```

### 2.2 `<select>` 태그

우리가 생년월일에서 생년을 선택할 때 사용하는 콤보박스이다. 몇 개의 선택지를 리스트 형태로 노출하고 그중 하나를 선택할 수 있게 하는 태그이다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-12.png)

```html
<div> 
  <select>
      <option>2020</option>
      <option>2019</option>
      <option>2018</option>
  </select>
  년
</div>
```

- `multiple` : 이 속성은 사용자가 두 개 이상의 옵션을 동시에 선택할 수 있음을 명시한다. 불리언(boolean) 속성이다. 속성을 명시하지 않으면 속성값이 자동으로 false 값을 가지게 되며, 명시하면 자동으로 true 값을 가지게 된다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-13.png)

```html
<div> 
  <select multiple>
      <option>2020</option>
      <option>2019</option>
      <option>2018</option>
  </select>
  년
</div>
```

### 2.3 `<textarea>` 태그

이 태그는 특이하게 여는 태그와 닫는 태그를 꼭 넣어줘야 하며,  input 과는 달리 줄바꿈이 가능하다. 그리고 `rows`와 `cols` 속성을 이용해서 크기를 조정할 수 있다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-14.png)

```html
<textarea rows="5" cols="30"> </textarea>
```

### 2.4 `<button>` 태그

버튼을 만들 때 사용하며 `<input>`처럼 `type`속성이 존재하며, 속성값에는 `submit`, `reset`, `button` 3가지의 타입이 있다.

- `submit` : form의 값을 전송하는 버튼
- `reset` : form의 값을 초기화하는 버튼
- `button` : 아무 기능이 없는 버튼

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-15.png)

```html
<button type="submit">submit</button>
<button type="reset">reset</button>
<button type="button">button</button>
```

### 2.5 `<label>` 태그

`<label>`은 form 요소의 이름과 form 요소를 명시적으로 연결시켜주기 위해 사용한다. 모든 form 요소에 사용할 수 있으며, form 요소의 id 속성값과 `<label>`의 for 속성값을 같게 해줘야한다. 그래야 컴퓨터에서 `<label>`을 사용하면, 이를 클릭했을 때 해당 form 요소를 클릭한 것으로 이해하고 동작한다. `<label>`은 사용성, 접근성적인 측면으로 중요한 역할을 하므로 반드시 써주는 것이 좋다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-16.png)

```html
<label for="name">ID</label>: <input type="text" id="name"><br>

<label>
  <input type="checkbox" name="peas">
  ID 기억하기
</label> 
```

### 2.6 `<fieldset>`와 `<legend>` 태그

`<fieldset>`, `<legend>`는 form 요소를 구조화 하기 위해 필요한 태그이다.

- `<fieldset>` :  **폼 필드 세트(form FIELD SET)**를 표시한다. 폼 필드 세트는 폼 내에서 관련 컨트롤을 하나의 그룹으로 묶은 것을 말한다. 폼을 효과적으로 계층화시킬 수 있고, `<legend>`요소와 함께 사용해야한다.
- `form` 속성 : `form`속성은 해당 **`<fieldset>` 요소가 속해 있는 폼**을 지정한다. 속성을 지정하면 특정 `form`과 `<fieldset>`요소의 관계를 명시적으로 연결할 수 있다. 이렇게 연결하면 브라우저는 두 요소 사이의 상호작용이 좀 더 쉽게 이루어질 수 있도록 도울 수 있으며 `<fieldset>`요소가 `form`요소 밖에 있더라도 둘 사이의 관계를 유지할 수 있다. 특히 하나의 `<fieldset>`요소가 복수의 `form`요소와 관계를 맺어야 할 때 효과적인 속성이다.
- `<legend>` : `<legend>` 요소는 **`<fieldset>` 요소의 제목(LEGEND)**을 표시한다. `<fieldset>` 요소를 이용하여 여러 개의 컨트롤들을 묶었으면 이 묶음이 어떤 성격 또는 용도인지 알려줄 필요가 있으며, 이때 `<legend>` 요소를 사용한다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-17.png)

```html
<p> fieldset 태그</p> 
<fieldset form="user"> 
    <legend>legend 태그</legend> 
    ...
</fieldset>
```

### 2.7 `<form>` 태그

`<form>` 요소들을 감싸는 태그로 데이터를 묶어서 실제 서버로 전송해주는 역할을 하는 태그이다.만약 `<fieldset>`으로 구조화되어있다면 `<fieldset>`도 함께 감싸는 역할을 한다.

`<form>` 태그의 속성은 아래 두 개가 있다.

- `action`: 데이터를 처리하기 위한 서버의 주소
- `method`: 데이터를 전송하는 방식을 지정해주며, `get`/`post` 두개의 방식이 있다.

![title](/assets/img/DEVLOG/HTML & CSS/TIL3/2021-01-07-HC-TIL3-17.png)

```html
<form action="" method="">
	<p> fieldset 태그</p> 
	<fieldset form="user"> 
    	<legend>legend 태그</legend> 
    	...
	</fieldset>
</form>
```

