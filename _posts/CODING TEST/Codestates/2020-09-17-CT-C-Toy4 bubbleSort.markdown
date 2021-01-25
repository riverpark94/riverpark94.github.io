---
layout: post
title: '[JS] Toy4. bubbleSort'
date: 2020-09-17 22:27:44 +0900
subtitle: 'bubbleSort'
categories: CODING_TEST
tags: Codestates
comments: true!
---

> 정수를 요소로 갖는 배열을 입력받아 오름차순으로 정렬하여 리턴해야 합니다. 버블 정렬(bubble sort)은 여러 정렬 알고리즘(삽입 정렬, 퀵 정렬, 병합 정렬, 기수 정렬 등) 중 가장 기본적인 알고리즘입니다.
>
> 버블 정렬 알고리즘은 아래와 같습니다.
>
> 1. 첫 번째 요소가 두 번째 요소보다 크면, 두 요소의 위치를 바꿉니다. (swap)
> 2. 두 번째 요소와 세 번째 요소보다 크면, 두 요소의 위치를 바꿉니다. (swap)
> 3. 1, 2를 마지막까지 반복합니다. (마지막에서 두 번째 요소와 마지막 요소를 비교)
> 4. 1~3의 과정을 한 번 거치게 되면, 가장 큰 요소가 배열의 마지막으로 밀려납니다.
> 5. 1~3의 과정을 첫 요소부터 다시 반복합니다.
> 6. 5를 통해 두 번째로 큰 요소가 배열의 마지막 바로 두 번째로 밀려납니다.
> 7. 1~3의 과정을 총 n번(배열의 크기) 반복합니다.
>
> 이 모습이 마치 '거품이 밀려 올라가는 것과 같은 모습'과 같아서 bubble sort라고 부릅니다.

<br>

[Codestates](https://codestates.com/)의 **[소프트웨어 엔지니어링](https://codestates.com/course/software-engineering)** 커리큘럼에서 제공되는 문제입니다. 😀 
{: .notice--warning}

<br>

# 1. Example

### Your output should look something like :

- **input**
  -  `number` 타입을 요소로 갖는 배열
  -  `arr[i]`는 정수
  -  `arr[i]`의 길이는 1,000 이하
  
- **output ** 

  - `number` 타입을 요소로 갖는 배열을 리턴해야 합니다.
  - 배열의 요소는 오름차순으로 정렬되어야 합니다.
  - `arr[i] <= arr[j]` (`i < j`)

- **주의사항** 
  - 위에서 설명한 알고리즘을 구현해야 합니다.
  - `arr.sort` 사용은 금지됩니다.
  - 입력으로 주어진 배열은 중첩되지 않은 1차원 배열입니다.

```js
let output = bubbleSort([2, 1, 3]);
console.log(output); // --> [1, 2, 3]
```

### Advanced  :

- 아래의 힌트를 바탕으로 (최선의 경우) 수행 시간을 단축할 수 있도록 코드를 수정해보세요.
- 위에서 설명된 알고리즘 1~3의 과정 중 어떤 요소도 위치가 바뀌지 않은 경우, 배열이 정렬된 상태라는 것을 알 수 있습니다.

<br>

***

# 2. Pseudocode

```js
const bubbleSort = function (arr) {
  // TODO: 여기에 코드를 작성합니다.
};
```
1. arr를 배열의 길이만큼 반복해야하기 때문에 for문을 사용

   1.1 언제나 첫번째부터 비교를 시작해야하기 때문에 숫자 0을 할당하는 변수를 선언

   1.2 중첩 for문 시작

   ​	1.2.1 i번째가 i +1 보다 크면

   ​	1.2.2 변수 하나를 선언하여 i번째 값을 할당

   ​	1.2.3 i번째에 i+1번째의 값을 할당

   ​	1.2.3 i+1 번째에는 (2.3)를 할당

<br>

***

# 3. My solution

```js
let bubbleSort = function (arr) {
  /**
   * 1. arr를 배열의 길이만큼 반복해야하기 때문에 for문을 사용
   *  1.1 언제나 첫번째부터 비교를 시작해야하기 때문에 숫자 0을 할당하는 변수를 선언
   *  1.2 중첩 for문 시작
   *    1.2.1 i번째가 i +1 보다 크면
   *    1.2.2 변수 하나를 선언하여 i번째 값을 할당
   *    1.2.3 i번째에 i+1번째의 값을 할당
   *    1.2.3 i+1 번째에는 (2.3)를 할당
   */

  for (let i = 0; i < arr.length; i++) {
    let n = 0
    for (n; n < arr.length-1-i; n++) { // 큰수부터 정렬이 되기 때문에 이미 정렬한 인덱스까지 확인할 필요 없음.
      if (arr[n] > arr[n+1]) {
        let swapEl = arr[n]
        arr[n] = arr[n+1]
        arr[n+1] = swapEl
      }
    }
  }

  return arr;
};

```

<br>

***

## 4. Reference Code

```js
const swap = function (idx1, idx2, arr) {
  // 두 변수를 바꾸는 방법

  // 1) 임시 변수를 활용한 방법
  // let temp = arr[idx1];
  // arr[idx1] = arr[idx2];
  // arr[idx2] = temp;

  // 2) Destructuring assignment를 활용한 방법
  // arr이 reference type이라 가능
  [arr[idx1], arr[idx2]] = [arr[idx2], arr[idx1]];

  // 3) XOR 연산을 활용한 방법
  // arr이 reference type이라 가능
  // arr[idx1] ^= arr[idx2];
  // arr[idx2] ^= arr[idx1];
  // arr[idx1] ^= arr[idx2];
};

// naive solution
// let bubbleSort = function (arr) {
//   let N = arr.length;

//   for (let i = 0; i < N - 1; i++) {
//     // 매 반복(iteration)마다 i번째로 큰 수가 마지막에서 i번째 위치하게 된다.
//     // 이미 정렬된 요소는 고려할 필요가 없으므로, 'j < N - 1 - i'만 비교하면 된다.
//     for (let j = 0; j < N - 1 - i; j++) {
//       if (arr[j] > arr[j + 1]) {
//         swap(j, j + 1, arr);
//       }
//     }
//   }

//   return arr;
// };

// optimized solution
let bubbleSort = function (arr) {
  let N = arr.length;

  for (let i = 0; i < N; i++) {
    // swap 횟수를 기록한다.
    // 어떤 요소도 swap되지 않은 경우, 배열은 정렬된 상태이다.
    let swaps = 0;

    // 매 반복(iteration)마다 i번째로 큰 수가 마지막에서 i번째 위치하게 된다.
    // 이미 정렬된 요소는 고려할 필요가 없으므로, 'j < N - 1 - i'만 비교하면 된다.
    for (let j = 0; j < N - 1 - i; j++) {
      if (arr[j] > arr[j + 1]) {
        swaps++;
        swap(j, j + 1, arr);
      }
    }

    if (swaps === 0) {
      break;
    }
  }

  return arr;
};
```

<br>

***

# 마치며

**풀은 시간** : 20시 20분 ~ 21시 26분 (총 56분)

Advanced에 해당하는 것을 제외하면 전부 통과했다. (11/12)  

reduce로도 풀어보고 forEach로도 풀었는데 30분의 시간을 소요할 때까지 사간초과 오류가 계속 나서 한참을 헤맸다. (끝내 안쓰느는 노트에 그려가면서 했다.) 그래도 약속한 시간 안으로 통과해서 다행이라고 생각한다. 내일 좀 시간이 남으면 어드벤드를 어떻게 통과할지 고민해봐야겠다.