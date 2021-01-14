---
layout: post
title: '[JS] Toy1. rockPaperScissors'
date: 2020-09-11 22:27:44 +0900
subtitle: 'rockPaperScissors'
categories: CODING_TEST
tags: Codestates
comments: true!
---

> 가위바위보 게임은 2인 이상의 사람이 동시에 '가위, 바위, 보'를 외치고 동시에 가위, 바위 또는 보 중에서 한 가지를 의미하는 손 모양을 내밀어 승부를 결정짓는 게임이다. 세 판의 가위바위보 게임을 할 경우, 한 사람은 세 번의 선택(예. 가위, 가위, 보)을 할 수 있습니다. 세 번의 선택으로 가능한 모든 경우의 수를 구하는 함수를 작성합니다.

<br>

[Codestates](https://codestates.com/)의 **[소프트웨어 엔지니어링](https://codestates.com/course/software-engineering)** 커리큘럼에서 제공되는 문제입니다. 😀 
{: .notice--warning}

<br>

# 1. Example

**Your output should look something like:**

- 2차원 배열(`arr[i]`)을 리턴해야 합니다.
- `arr[i]`는 전체 경우의 수 중 한 가지 경우(총 세 번의 선택)를 의미하는 배열입니다.
- `arr[i]`는 `'rock'`, `'paper'`, `'scissors'` 중 한 가지 이상을 요소로 갖는 배열입니다.
- `arr[i].length`는 3입니다.

```js
let output = rockPaperScissors();

console.log(output);
/*
    [
      ["rock", "rock", "rock"],
      ["rock", "rock", "paper"],
      ["rock", "rock", "scissors"],
      ["rock", "paper", "rock"],
      // ...etc ...
    ]
  */
```

**주의 사항:**

- 최종적으로 리턴되는 배열의 순서는 가중치 적용 정렬(Weighted Sort)을 따릅니다.
- 중요도는 `'rock'`, `'paper'`, `'scissors'` 순으로 높습니다.
- 쉽게 생각해 올림픽 순위 결정 방식을 참고하면 됩니다.
- 금메달(`'rock'`)이 은메달(`'paper'`)보다 우선하고, 은메달(`'paper'`)이 동메달(`'scissors'`)보다 우선합니다.

**Advanced:**

- 가위바위보 게임의 수를 나타내는 양의 정수 rounds가 주어질 경우, 해당 rounds 동안 선택할 수 있는 모든 경우의 수를 리턴하도록 함수를 작성해 보세요.

```js
let output = rockPaperScissors(5);

console.log(output);
/*
    [
      ["rock", "rock", "rock", "rock", "rock"],
      ["rock", "rock", , "rock", "rock", "paper"],
      ["rock", "rock", , "rock", "rock", "scissors"],
      ["rock", "rock", "rock", "paper", "rock"],
      ["rock", "rock", "rock", "paper", "paper"],
      ["rock", "rock", "rock", "paper", "scissors"],
      ["rock", "rock", "rock", "scissors", "rock"],
      // ...etc ...
    ]
  */
```



<br>

***

# 2. Pseudocode

```js
const rockPaperScissors = function () {
  // TODO: 여기에 코드를 작성합니다.
};
```
### 2020-09-11 (10:29~11:30)

  1. rock, paper, scissors 가 들어가있는 array를 선언한다.

  2. return 할 빈 array를 선언한다.

  3. for문을 이용해 (1)을 한바퀴씩 돈다. 
     
       3.1. 가위바위보 결과를 입력한 빈 array를 선언한다.
       
       3.2. 
   
   4. 


<br>

***

## 3. My solution

### 2020-10-19 (10:29~11:30)

```js
let rockPaperScissors = function () {
  // TODO: 여기에 코드를 작성합니다.
  let rps = ['rock', 'paper', 'scissors']
  let result = [];

  for (let i = 0; i < rps.length; i++) {
    let resultRpsArr = [];
    resultRpsArr.push(rps[i])
    for (let j = 0; j < rps.length; j++) {
      resultRpsArr.push(rps[j])
      for (let x = 0; x < rps.length; x++) {
        debugger;
        let c = [];
        resultRpsArr.push(rps[x])
        for(let y = 0; y < resultRpsArr.length; y++){
            c.push(resultRpsArr[y]);
        }
        result.push(c)
        c = [];
        resultRpsArr.pop()
      }
      resultRpsArr.pop()
    }
    resultRpsArr.pop()
  }
  return result
};

```

<br>

***

## 4. Reference Code

```js

```

<br>

***

# 마치며

### 2020-09-11 (10:29~11:30)

Advanced는 통과하지 못했지만, 세 번의 선택으로 가능한 모든 경우의 수를 구하는 함수를 작성하긴했다. for 문과 push를 같이 쓰면 어떻게 출력되는지 까먹었어서 거기서 시간을 한참 잡아먹었다. 반복되는 부분이 있으니 시간 날때, 재귀를 쓰는 쪽으로 해봐야겠다.
