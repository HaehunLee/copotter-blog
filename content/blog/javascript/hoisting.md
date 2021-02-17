---
title: '호이스팅(Hosting) 과 var, let, const'
date: 2021-02-18 00:24:00
category: 'javascript'
draft: false
---

```
* ES5까지는 변수와 상수 등의 타입을 var를 통해서 관리해왔고,
  ES6에서 let, const가 생겼다.
```

# 1. 재선언, 재할당

var는 재선언, 재할당이 모두 가능하다.

```js
var text = 'javascript'
console.log(text) // javascript

var text = 'js'
console.log(text) // js

text = 'javascript js'
console.log(text) // javascript js
```

코드양이 상당할 때, 이러한 var의 특징은 버그 발생 시,
발견을 하는데 큰 방해가 될 수 있다.

이러한 문제점을 보완하기 위해 const, let이 추가되었다.

```js
let text
console.log(text) // undefined

text = 'javascript'
console.log(text) // javascript

let text = 'js'
console.log(text)
// Uncaught SyntaxError: Identifier 'text' has already been declared
```

let은 재할당은 가능하지만, 재선언은 불가능한 변수 타입이다.

<br/>

```js
const text = 'javascript'
console.log(text) // 'javascript'

text = 'js'
console.log(text)
//Uncaught TypeError: Assignment to constant variable.

const text = 'javascript2'
console.log(text)
// Uncaught SyntaxError: Identifier 'text' has already been declared
```

const는 재선언, 재할당이 모두 불가능한 상수 타입이다.

<br/>
<br/>
<br/>

# 2. 호이스팅 (Hoisting)

```
* 변수나 함수의 선언문 등을 해당 스코프의 선두로 옮긴 것처럼 동작하는 특성을 의미한다.

* var는 Function-scoped이므로, 함수 내부의 최상단까지만 호이스팅 된다.

* let, const는 Block-scoped이므로, 블록 단위로 호이스팅이 이루어 진다.
```

```js
var outer = 'out'

function func() {
  console.log(outer) // undefined

  var outer = 'in'
  console.log(outer) // in

  var inner = 'from function'
}
func()

console.log(inner)
// Uncaught ReferenceError: inner is not defined
```

위 코드의 호이스팅이 되는 과정을 코드로 다시 작성해보자면,

```js
function func() {
  var outer

  console.log(outer) // undefined

  outer = 'in'
  console.log(outer) // in
}
func()
```

위에서 보듯, outer라는 변수는 func함수 선언문 최상단으로 호이스팅되어 선언이 되어 있는 채로, 함수가 시작된다.

inner 변수는, var가 Function-Scoped이기 때문에 func함수 내에서만 호이스팅 되므로, 바깥에서는 ReferenceError 일어나게 된다.

위와 같은 원리로 아래 코드와도 같은 현상도 발생될 수 있다.

```js
console.log(a)
// Uncaught ReferenceError: a is not defined

console.log(b) // undefined
var b
```

변수가 생성이 될 때, 선언 > 초기화 > 할당 순서로 생성이 되는데, Scope에 변수가 등록되고, 선언 후, 변수를 undefinefd로 초기화하게 된다. 그 과정에서 var의 Scope 특성과 변수 선언할 때, 선언과 초기화가 동시에 이루어지기 때문에 위와 같은 현상이 나타나게 된다.

<br/>
<br/>
<br/>

## 3. 정리

ES6 문법을 사용하고 있을 때에는 var 보다 const, let을 지향하도록 하고,<br/>
<br/>
재할당이 필요없는 상수의 경우 const를,<br/>
재할당이 필요한 경우 let을 사용하는 것이 좋다.
