---
title: 'Big O 표기법'
date: 2022-01-22 16:19:00
category: 'algorithm'
draft: false
---

## Big O 표기법

### 코드의 타이밍

- 정해진 체계를 통해 코드의 효율성 정도를 표현하는 표기법

```js
// Add1.js
function addUpTo(n) {
  let total = 0
  for (let i = 1; i <= n; i++) {
    total += i
  }
  return total
}

console.log(addUpto(6)) // 21;
console.log(addUpto(3)) // 6;
console.log(addUpto(100)) // 5050;
```

```js
// Add2.js
function addUpTo(n) {
  return (n * (n + 1)) / 2
}

console.log(addUpTo(6)) // 21
```

- 정도가 더 낫다는 의미

  - 속도 => 내장 시간 측정 함수 이용

  ```js
  let t1 = performance.now()
  addUpTo(1000000000)
  let t2 = performance.now()
  console.log(`Time Elapsed: ${(t2 - t1) / 1000} seconds.`)
  ```

  - 메모리 사용
  - 가독성

- 시간의 문제
  - 다른 기계는 다른 측정 시간을 기록한다.
  - 같은 기계여도 다른 측정 시간을 기록한다.
  - 간단한 알고리즘의 경우, 속도의 차이가 분명하지 않다.

### 연산 카운팅

- 동작의 횟수를 측정한다. ( 시간, 기계에 부여받지 않고 측정할 수 있게됨. )

```js
// Add2.js
// 3번의 동작
// 1 multipleication, 1 addition, 1 division...
function addUpTo(n) {
  return (n * (n + 1)) / 2
}

// Add1.js
// 2 assignment
// <= n comparisions
// += : n additions, n assignments,
// ++ : n additions and n assignments
function addUpTo(n) {
  let total = 0
  for (let i = 1; i <= n; i++) {
    total += i
  }
  return total
}
```

### [시간 복잡도 시각화](https://rithmschool.github.io/function-timer-demo/)

### 빅오 공식

- 빅오 : 애매한 측량을 정형화한 방법
- N이 증가함에 따라 컴퓨터가 수행해야 하는 단순 동작의 수가 상수로 수렴하는 f(n)보다 작은 값이 된다면 알고리즘이 대문자O(빅오)라고 한다.
- 일차함수, 정비례함수, 이차함수 ...등등

```js
// Always 3 operations
// O(1)
function addUpTo(n) {
  return (n * (n + 1)) / 2
}

// O(n)
function addUpTo(n) {
  let total = 0
  for (let i = 1; i <= n; i++) {
    total += i
  }
  return total
}
```

```js
// O(n)
function countUpandDown(n) {
  console.log('Going Up')
  // O(n)
  for (let i = 0; i < n; i++) {
    console.log(i)
  }
  console.log('At the Top!\nGoing Down...')
  // O(n)
  for (let j = n - 1; j >= 0; j--) {
    console.log(j)
  }
  console.log('Back down. Bye!')
}
```

- 중첩 루프 (n차 함수)

```js
// O(n^2)
function printAllPairs(n) {
  // O(n)
  for (var i = 0; i < n; i++) {
    // O(n)
    for (var j = 0; j < n; j++) {
      console.log(i, j)
    }
  }
}
```

### 빅오 표현식 단순화

1. O(2n) x / O(n) o
2. O(500) x / O(1) o
3. O(13n^2) x / O(n^2)

4. O(n + 10) x / O(n)
5. O(1000n + 50) x / O(n)
6. O(n^2 + 5n + 8) x / O(n^2 + n)

- 숫자를 더하거나 뺴는 식은 일정하다.
- 변수에 대한 동작을도 일정하다.
- 인덱스를 사용하여 배열에 있는 요소에 접근하는 것은 일정하다.
- 루프 안에서 발생하는 일의 복잡도를 곱한 것을 의미한다.

#### ex

```js
// O(n)
function logAtLeast5(n) {
  for (var i = 1; i <= Math.max(5, n); i++) {
    console.log(i)
  }
}

// 루프의 횟수는 5로 제한되어 있어,
// O(1)이 된다.
function logAtMost5(n) {
  for (var i = 1; i <= Math.min(5, n); i++) {
    console.log(i)
  }
}
```

### Quiz

```js
// 1. O(n + 10) => O(n)
// 2. O(100 * n) => O(n)
// 3. O(25) => O(1)
// 4. O(n^2 + n^3) => O(n^3)
// 5. O(n + n + n + n) => O(n)
// 6. 시간 복잡도 구하기
// O(n)
function logUpTo(n) {
  for (var i = 1; i <= n; i++) {
    console.log(i)
  }
}

// O(1)
function logAtMost10(n) {
  for (var i = 1; i <= Math.min(n, 10); i++) {
    console.log(i)
  }
}

// O(n)
function logAtLeast10(n) {
  for (var i = 1; i <= Math.max(n, 10); i++) {
    console.log(i)
  }
}

// O(n)
function onlyElementsAtEvenIndex(array) {
  var newArray = Array(Math.ceil(array.length / 2))
  for (var i = 0; i < array.length; i++) {
    if (i % 2 === 0) {
      newArray[i / 2] = array[i]
    }
  }
  return newArray
}

// O(n^2)
function subtotals(array) {
  var subtotalArray = Array(array.length)
  for (var i = 0; i < array.length; i++) {
    var subtotal = 0
    for (var j = 0; j <= i; j++) {
      subtotal += array[j]
    }
    subtotalArray[i] = subtotal
  }
  return subtotalArray
}
```

### 공간 복잡도

- 차지하는 메모리의 크기에 대함
- 입력값을 제외한 알고리즘 수행에 관련한 공간에 대해 다룸.
- 기본형 타입은 모두 일정한 공간을 가진다.
- String은 가변형이다.
- 배열, 객체같은 참조형 타입 역시 가변형이다.

```js
// O(1)
function sum(arr) {
  let total = 0 // 1 number
  for (let i = 0; i < arr.length; i++) {
    // 1 number
    total += arr[i] // 공간을 이미 차지하고 있으므로 x
  }
  return total
}

// O(n)
function double(arr) {
  let newArr = []
  for (let i = 0; i < arr.length; i++) {
    newArr.push(2 * arr[i])
  }
  return newArr // n numbers
}
```

### Quiz

```js
// 1. 공간복잡도 구하기
// O(1)
function logUpTo(n) {
  for (var i = 1; i <= n; i++) {
    console.log(i)
  }
}

// O(1)
function logAtMost10(n) {
  for (var i = 1; i <= Math.min(n, 10); i++) {
    console.log(i)
  }
}

// O(1)
function logAtMost10(n) {
  for (var i = 1; i <= Math.min(n, 10); i++) {
    console.log(i)
  }
}

// O(n)
function onlyElementsAtEvenIndex(array) {
  var newArray = Array(Math.ceil(array.length / 2))
  for (var i = 0; i < array.length; i++) {
    if (i % 2 === 0) {
      newArray[i / 2] = array[i]
    }
  }
  return newArray
}

// O(n) ??
function subtotals(array) {
  var subtotalArray = Array(array.length)
  for (var i = 0; i < array.length; i++) {
    var subtotal = 0
    for (var j = 0; j <= i; j++) {
      subtotal += array[j]
    }
    subtotalArray[i] = subtotal
  }
  return subtotalArray
}
```

### 로그 (Log)

- 로그 : 지수를 반대로 한 것
- log2(value) = exponent // log2(8) = 3
- 빅오에서의 log === log2
- 로그 시간 복잡도가 가장 효율적임.
