---
title: 'Big O 표기법'
date: 2022-01-22 16:19:00
category: 'algorithm'
draft: false
---

## Big O 표기법

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
