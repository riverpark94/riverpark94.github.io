---
layout: post
title: '[JS] Toy3. isSubsetOf'
date: 2020-09-15 22:27:44 +0900
subtitle: 'fibonacci'
categories: CODING_TEST
tags: Codestates
comments: true!
---

> 두 개의 배열(`base`, `sample`)을 입력받아 `sample`이 `base`의 부분집합인지 여부를 리턴해야 합니다

<br>

[Codestates](https://codestates.com/)의 **[소프트웨어 엔지니어링](https://codestates.com/course/software-engineering)** 커리큘럼에서 제공되는 문제입니다. 😀 
{: .notice--warning}

<br>

# 1. Example

### Your output should look something like :

- **input**
  -  인자 1 : base
     -  `number` 타입을 요소로 갖는 임의의 배열
     -  `base.length`는 100 이하
  -  인자 2 : sample
     - `number` 타입을 요소로 갖는 임의의 배열
     -  `sample.length`는 100 이하

- **output ** 

  - `boolean` 타입을 리턴해야 합니다.

- **주의사항** 
  - `base`, `sample` 내에 중복되는 요소는 없다고 가정합니다.

```js
let base = [1, 2, 3, 4, 5];
let sample = [1, 3];
let output = isSubsetOf(base, sample);
console.log(output); // --> true

sample = [6, 7];
output = isSubsetOf(base, sample);
console.log(output); // --> false

base = [10, 99, 123, 7];
sample = [11, 100, 99, 123];
output = isSubsetOf(base, sample);
console.log(output); // --> false
```

### Advanced  :

- 시간 복잡도를 개선하여, Advanced 테스트 케이스(`base`, `sample`의 길이가 70,000 이상)를 통과해 보세요.

<br>

***

# 2. Pseudocode

```js
const isSubsetOf = function (base, sample) {
  // TODO: 여기에 코드를 작성합니다.
};
```
1.  result라는 변수에 0을 할당함

2. sample을 for문을 통해서 인자를 하나씩 확인한다.

3. 중첩 for문을 통해서 base 인자를 하나씩 확인한다.

4. 2와 3을 비교해서 같으면 result 값을 ++ 해준다.

5. result와 sample.length+1 한 값이 같으면 true값을 아니면 false값을 출력해준다.

<br>

***

# 3. My solution

```js
const isSubsetOf = function (base, sample) {
  // TODO: 여기에 코드를 작성합니다.
  let result = 0;
  
  base.sort((a, b) => a - b);
  sample.sort((a, b) => a - b);
  
  for (let i = 0; i < sample.length; i++) {
    for (let j = 0; j < base.length; j++) {
      if (sample[i] === base[j]) {
        result++;
      }
    }
  }

  if (result === sample.length + 1){
    return true;
  } else {
    return false;
  }
};

```

<br>

***

## 4. Reference Code

```js
const isSubsetOf = function (base, sample) {
  // naive solution: O(M * N)
  // return sample.every((item) => base.includes(item));

  // 각 배열을 정렬: O(N * logN), O(M * logM)
  // N >= M 이므로, O(N * logN)
  base.sort((a, b) => a - b);
  sample.sort((a, b) => a - b);

  const findItemInSortedArr = (item, arr, from) => {
    for (let i = from; i < arr.length; i++) {
      if (item === arr[i]) return i;
      else if (item < arr[i]) return -1;
    }
    return -1;
  };

  let baseIdx = 0;
  for (let i = 0; i < sample.length; i++) {
    baseIdx = findItemInSortedArr(sample[i], base, baseIdx);
    if (baseIdx === -1) return false;
  }
  return true;
};
```

<br>

***

# 마치며

**풀은 시간** : 14시 10분 ~ 14시 44분 (총 31분)

두개의 매개변수를 정렬 후 실행해도 시간 초과라는 결과 출력, 다른 방법을 생각해보고자 했으나, 

개도 안걸리는 여름감기 때문에 머리가 제대로 돌아가지 않는다. 

당장 레퍼런스를 봤을때는 중첩 for을 한 것과의 차이는 보이지 않으나, 내일 다시 시간복잡도를 생각하면서 공부해봐야겠다.