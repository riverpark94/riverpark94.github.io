---
layout: post
title: '[JS] Toy5. tiling'
date: 2020-09-18 22:27:44 +0900
subtitle: 'tiling'
categories: CODING_TEST
tags: Codestates
comments: true!
---

> 세로 길이 2, 가로 길이 n인 2 x n 보드가 있습니다. 2 x 1 크기의 타일을 가지고 이 보드를 채우는 모든 경우의 수를 리턴해야 합니다.

<br>

[Codestates](https://codestates.com/)의 **[소프트웨어 엔지니어링](https://codestates.com/course/software-engineering)** 커리큘럼에서 제공되는 문제입니다. 😀 
{: .notice--warning}

<br>

# 1. Example

### Your output should look something like :

- **input**
  -  `number` 타입의 1 이상의 자연수
  
- **output ** 
- `number` 타입을 리턴해야 합니다.
  
- **주의사항** 
  - 타일을 가로, 세로 어느 방향으로 놓아도 상관없습니다. (입출력 예시 참고)

```js
let output = tiling(2);
console.log(output); // --> 2

output = tiling(4);
console.log(output); // --> 5
/* 
2 x 4 보드에 타일을 놓는 방법은 5가지
각 타일을 a, b, c, d로 구분

2 | a b c d
1 | a b c d 
------------

2 | a a c c
1 | b b d d 
------------

2 | a b c c
1 | a b d d 
------------

2 | a a c d
1 | b b c d 
------------

2 | a b b d
1 | a c c d 
------------
*/
```

### Advanced  :

- 타일링 문제를 해결하는 효율적인 알고리즘(`O(N)`)이 존재합니다. 반드시 직접 문제를 해결하시면서 입력의 크기에 따라 어떻게 달라지는지 혹은 어떻게 반복되는지 관찰하시기 바랍니다.

<br>

***

# 2. Pseudocode

```js
let tiling = function (n) {
  // TODO: 여기에 코드를 작성합니다.
};
```
 2 x 1 크기의 타일을 가지고 이 보드를 채우는 모든 경우의 수를 리턴

​	  => 아래 좌 우 위에 자기와 같은 모양을 블럭이 와야함. 

​	  => 백트랙킹을 사용해야겠다. 

1. 경수의 수를 입력 할 count라는 0이 할당된 변수를 선언

2. 2*n 매트릭스를 만들기

   2.1 길이가 2인 빈 배열을 선언let matrix = new Array(2)

   2.2 길이가 n인 배열을 만드는 함수 선언

   ​		2.2.1 let arr = []

   ​		2.2.2 for (let i = 0; i < n < i ++) {arr.push(i)}

   2.3 matrix[0] = (2.2) 함수 실행

   2.4 matrix[1] = [2.2) 함수 실행

3. 2X1의 타일인지를 확인 할 함수를 선언

   3.1 arr[0]

   ​		3.1.1 arr[0][0]인덱스인지를 확인 : arr[0][1]. arr[1][0] 과 같아야함

   ​		3.1.2 arr[0][n]인덱스인지를 확인 : arr[n-1][n]. arr[1][n] 과 같아야함

   ​		3.1.3 그 외 : i 번째 인덱스 : arr[0][i+1], arr[0][i-1], arr[1][i] 와 같아야함

   3.2 arr[1]

   ​		3.3.1 arr[1][0]인덱스인지를 확인 : arr[1][1]와 같아야함

   ​		3.1.2 arr[1][n]인덱스인지를 확인 : arr[n-1][n]와 같아야함

   ​		3.1.3 그 외 : i 번째 인덱스 : arr[1][i+1], arr[1][i-1]와 같아야함.

4. ... 우와 1도 모르겠다...

<br>

***

# 3. Reference Code

```js
// naive solution: O(2^N)
// 2 x 4 보드에 타일을 놓는 방법은 5가지다.
// 각 타일을 a, b, c, d로 구분한다.
// 아직 타일이 놓이지 않는 부분은 -로 표기한다.
// 타일을 놓는 방법은 가장 왼쪽부터 세로로 놓거나 가로로 놓는 것으로 시작한다.
// 1) 세로로 놓는 법
//   2 | a - - -
//   1 | a - - -
//   ------------
// 2) 가로로 놓는 법
// 타일을 가로로 놓게 되면, 그 바로 아래에는 가로로 놓을 수 밖에 없다.
//   2 | a a - -
//   1 | b b - -
//   ------------
// 이때, 타일이 아직 놓이지 않은 부분은 사실 크기만 다를뿐 같은 종류의 문제라는 것을 알 수 있다.
// 즉, 2 x 4 보드에 타일을 놓는 방법은 아래 두 가지 방법을 더한 결과와 같다.
//  1) 2 x 3 보드에 타일을 놓는 방법
//  2) 2 x 2 보드에 타일을 놓는 방법
// 따라서 2 x n 타일 문제는 아래와 같이 재귀적으로 정의할 수 있다.
// 주의: 재귀적 정의에는 항상 기초(base), 즉 더 이상 재귀적으로 정의할 수 없는(쪼갤 수 없는) 문제를 별도로 정의해야 한다.
// let tiling = function (n) {
//   if (n <= 2) return n;
//   return tiling(n - 1) + tiling(n - 2);
// };

// dynamic with memoization: O(N)
let tiling = function (n) {
  // 인덱스를 직관적으로 관리하기 위해
  // 앞 부분을 의미없는 데이터(dummy)로 채운다.
  const memo = [0, 1, 2];

  // 재귀를 위한 보조 함수(auxiliary function)을 선언)
  const aux = (size) => {
    // 이미 해결한 문제는 풀지 않는다.
    if (memo[size] !== undefined) return memo[size];
    if (size <= 2) return memo[n];
    memo[size] = aux(size - 1) + aux(size - 2);
    return memo[size];
  };
  return aux(n);
};

// dynamic with tabulation: O(N)
// tabulation은 데이터를 테이블에 정리하면서 bottom-up 방식으로 해결하는 기법을 말합니다.
// let tiling = function (n) {
//   const memo = [0, 1, 2];
//   if (n <= 2) return memo[n];
//   for (let size = 3; size <= n; size++) {
//     memo[size] = memo[size - 1] + memo[size - 2];
//   }
//   return memo[n];
// };

// dynamic with slicing window: O(N)
// slicing window은 필요한 최소한의 데이터만을 활용하는 것을 말합니다.
// 크기 n의 문제에 대한 해결을 위해 필요한 데이터는 오직 2개뿐이라는 사실을 이용합니다.
// let tiling = function (n) {
//   let fst = 1,
//     snd = 2;
//   if (n <= 2) return n;
//   for (let size = 3; size <= n; size++) {
//     // 앞의 두 수를 더해 다음 수를 구할 수 있다.
//     const next = fst + snd;
//     // 다음 문제로 넘어가기 위해 필요한 2개의 데이터의 순서를 정리한다.
//     fst = snd;
//     snd = next;
//   }
//   return snd;
// };
```

<br>

***

# 마치며

**풀은 시간** : 13시 25분 ~ 14시 11분 (총 46분)

30분 가까이 고민하다가 도저히 답이 안나와서 중간에 레퍼런스를 보았다. 고민하는데에 시간을 온전히 쓰기 보다는 남은 14분은 레퍼런스를 연구하기 위해서 였는데... NQUEEN와 비슷하다고 생각해서 접근했는데 레퍼런스는 내가 생각한 것과 완전히 다른 형태라 많이 당황스러웠다. 아무래도 처음부터 가닥을 잘못 잡은 듯 싶은데... 이거 풀이를 이해할 수나 있을까 ㅠㅠ 문제부터 다시 접근을 해봐야겠다.ㄴ