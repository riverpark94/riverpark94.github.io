---
layout: post
title: '[JS] Toy2. fibonacci'
date: 2020-09-14 22:27:44 +0900
subtitle: 'fibonacci'
categories: CODING_TEST
tags: Codestates
comments: true!
---

> 아래와 같이 정의된 피보나치 수열 중 n번째 항의 수를 리턴해야 합니다.
>
> - 0번째 피보나치 수는 0이고, 1번째 피보나치 수는 1입니다. 그 다음 2번째 피보나치 수부터는 바로 직전의 두 피보나치 수의 합으로 정의합니다.
> - 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, ...

<br>

[Codestates](https://codestates.com/)의 **[소프트웨어 엔지니어링](https://codestates.com/course/software-engineering)** 커리큘럼에서 제공되는 문제입니다. 😀 
{: .notice--warning}

<br>

# 1. Example

### Your output should look something like :

- **input**

  -  (인자 1 : n)
  - `number` 타입의 n (n은 0 이상의 정수)

- **output ** 

  - `number` 타입을 리턴해야합니다.

- **주의사항** 
  - **재귀함수를 이용해** 구현해야 합니다.
  - 반복문(`for`, `while`) 사용은 금지됩니다.
  - 함수 `fibonacci`가 반드시 재귀함수일 필요는 없습니다.

```js
let output = fibonacci(0);
console.log(output); // --> 0

output = fibonacci(1);
console.log(output); // --> 1

output = fibonacci(5);
console.log(output); // --> 5

output = fibonacci(9);
console.log(output); // --> 34
```

### Advanced  :

- 피보나치 수열을 구하는 효율적인 알고리즘(`O(N)`)이 존재합니다. 재귀함수의 호출을 직접 관찰하여 비효율이 있는지 확인해 보시기 바랍니다.

<br>

***

# 2. Pseudocode

```js
function fibonacci(n) {
  // TODO: 여기에 코드를 작성합니다.
}

```
   1. return 값은 n번째 인덱스 값.

   2. fibonacci n의 모든 수가 들어갈 배열을 선언 : fibonacciValues = [0, 1]

             2.1. 0~1번 째 인덱스는 항상 고정이며, 이것이 존재해야 2번째 인덱스부터 값을 구할 수 있다고 판단.

   3. n이 0이면, 0을 리턴, 1이면 1을 리턴하게 예외처리를 해줌.

   4. 재귀함수 : fibonacciRecursion

       4.1 매개변수는 i와 n을 인덱스 값을 입력해야하게끔 설계 

       4.2 if문을 통해  i가 n과 같은 값인지를 판단

       4.3 if(i === n), 

       ​			return fibonacciValues[fibonacciValues.length -1]

       4.4 if (i !== n), 

       ​			let fibonacciIndexValues = fibonacciValues[i-2] + fibonacciValues [i -1]

       ​			fibonacciValues[i] = fibonacciIndexValues 

       ​			fibonacciRecursion(i+1, n)

5. 재귀함수 실행 : fibonacciRecursion(2,n)

<br>

***

# 3. My solution

```js
function fibonacci(n) {
  let fibonacciValues = [0, 1]

  function fibonacciRecursion (i , n) {
    if (i > n) {
      return fibonacciValues[fibonacciValues.length -1]
    }
    else {
      let fibonacciIndexValues = fibonacciValues[i-2] + fibonacciValues[i -1]
      fibonacciValues[i] = fibonacciIndexValues 
      fibonacciRecursion(i+1, n)
    } 
  }

  if(n <= 1) {
    return fibonacciValues[n]
  }
  else {
    fibonacciRecursion(2,n)
    return fibonacciValues[fibonacciValues.length -1]
  }
}
```

<br>

***

## 4. Reference Code

```js
// naive solution: O(2^N)
// let fibonacci = function (n) {
//   if (n <= 1) return n;
//   return fibonacci(n - 1) + fibonacci(n - 2);
// };

// dynamic with meoization: O(N)
// 이미 해결한 문제의 정답을 따로 기록해두고,
// 다시 해결하지 않는 기법
// fibo(10)
// = fibo(9) + fibo(8)
// = fibo(8) + fibo(7) + fibo(7) + fibo(6)
// 여기까지만 보아도 동일한 문제가 중복으로 계산되는 것을 알 수 있다.
let fibonacci = function (n) {
  const memo = [0, 1];
  const aux = (n) => {
    // 이미 해결한 적이 있으면, 메모해둔 정답을 리턴한다.
    if (memo[n] !== undefined) return memo[n];
    // 새롭게 풀어야하는 경우, 문제를 풀고 메모해둔다.
    memo[n] = aux(n - 1) + aux(n - 2);
    return memo[n];
  };
  return aux(n);
};
```

<br>

***

# 마치며

**풀은 시간** : 11시 30분 ~ 12시 25분 (총 55분)

[[JS] Toy1. rockPaperScissors](https://riverpark94.github.io/coding_test/2020/09/11/CT-C-Toy1-rockPaperScissors/)관 달리 전체 통과를 했다. 사실 for과 while을 사용하지 말라고 해서 20분정도를 고민하느라 허비했는데, 그래도 1시간이라는 제한된 시간 안에 전부 풀었다. 

다만, 레퍼런스를 보니 너무 짧아서,,, 자괴감이... 오늘 개발공부를 하다가 지루할때 레퍼런스 해석을 해보려고 노력해봐야겠다.