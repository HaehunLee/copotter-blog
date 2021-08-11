---
title: '비교 연산자'
date: 2021-08-11 21:09:04
category: 'javascript'
draft: false
---

# 1. 불린형 반환

- true 반환일 때, 참/긍정/사실 을 의미.
- false 반환일 때, 거짓/부정/사실이 아님을 의미.

```js
console.log(1 == 2) // true
console.log(1 > 2) // false
console.log(1 != 2) // true
```

- 불린형 반환 결과를 변수에 저장

```js
const isRight = 1 < 2

console.log(isRight) // true
```

<br/>
<br/>

# 2. 문자열을 비교할 때는, `유니코드순`으로 비교 한다.

    - 비교 우선 순위 <br/>
    첫 글자 비교 => 첫 글자가 같을 시, 두 번째 글자 비교
    => 같을 시 => 마지막 글자까지 반복 => 글자가 같고, 문자열의 길이도 같을 시 true로 판단. => 길이가 다르다면, 긴 쪽이 더 큰 값으로 결론.

    - (대소문자에서는 대문자가 더 크다고 판단.)

```js
console.log('B' > 'A') // true
console.log('abc' > 'aba') // true
console.log('abcd' > 'abc') // true
console.log('A' > 'a') // true
```

<br/>
<br/>

# 3. 다른 타입 비교

    숫자형으로 바꿔서 비교를 한다.
    불린값은 true => 1, fasle => 0 으로 바뀐다.

```js
console.log('9' > 8) // true
console.log('05' == 5) // true
console.log(false == 0) // true
```

<br/>
<br/>

# 4. 일치 연산자

- 동등 연산자(==)는 형(타입)을 구분하지 못한다.

```js
console.log(1 == true) // true
```

- 일치 연산자(===)는 동등 연산자에 형 비교까지 엄격하게 처리한다.

```js
console.log(1 === true) //  false
```

- 부등 연산자(!=)와 불일치 연산자(!==)도 같은 격이다.

```js
console.log(1 != true) // false
console.log(1 !== true) // true
```

- 특수한 형들의 비교

```js
console.log(null == undefined) // true
console.log(null === undefined) // false

// 동등 연산자와 비교 연산자의 동작 방식이 상이하여,
// null은 비교 연산자에서는 숫자형인 0으로 변환되어 비교된다.
console.log(null == 0) // false
console.log(null >= 0) // true
```

<br/>
<br/>

---

- 이러한 동등 연산자, 비교 연산자의 상이함으로, 실제 개발하는 로직에서는,
  동등 연산자보다는 일치 연산자를 사용하여 엄격하게 비교를 하는 편이다.
