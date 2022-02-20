---
title: '배열과 오브젝트의 성능 평가'
date: 2022-02-16 23:18
category: 'algorithm'
draft: false
---

## 배열과 오브젝트의 성능 평가

---

### 객체의 빅오

- 객체는 정렬이 필요하지 않고, 빠른 접근, 입력과 제거를 원할 때 사용하면 좋다.

* 접근 시간이 모두 상수 시간이다. ( 탐색만 선형 시간 )

  ```js
  입력: O(1)
  제거: O(1)
  검색: O(N)
  접근: O(1)
  ```

  ```js
  // 입력, 제거, 접근 모두 도달하는 상수시간이 같기 때문에 걸리는 시간이 같다.

  // key들 간에 아무런 연관을 주지 않는다, 순서에 관여할 수 없다.

  // 객체는 특정 값을 찾으려면 모든 key값들을 잠재적으로 검색해야 하기 때문에 선형 시간이 된다.

  Object.keys : O(N) // 키가 늘어날수록 시간이 늘어남.
  Object.values : O(N) // 엘리먼트가 늘어날수록 시간이 늘어남.
  Object.entries : O(N) // 키, 엘리먼트가 늘어날수록 시간이 늘어남.
  hasOwnProperty : O(1) // 속성이 있는지 없는지만 알려주므로, 상수 시간.

  let instructor = {
    firstName : 'Kelly',
    isInstructor: true,
    favoriteNumbers: [1,2,3,4]
  }

  Object.keys(instructor) // ['firstName', 'isInstructor', 'favoriteNumbers']

  Object.entries(instructor)
  // [
  //  [
  //      "firstName",
  //      "Kelly"
  //  ],
  //  [
  //      "isInstructor",
  //      true
  //  ],
  //  [
  //      "favoriteNumbers",
  //      [
  //          1,
  //          2,
  //          3,
  //          4
  //      ]
  //  ]
  //]

  instructor.hasOwnProperty('firstName') // true
  ```

( 객체가 빠른 이유, 원리는 추후 해쉬 테이블과 맵이 나오는 섹션에서 다룰 예정! )

---

### 배열 안의 데이터에 접근이 느린 이유

- 주로 정렬이 필요한 데이터를 위해 배열을 사용함.

```js
  입력 : It depends...
  제거 :  It depends...
  /*
  * 입력은 어디에 입력하느냐에 따라 다르다.
  * 배열의 맨뒤에 추가하는 경우 (push) 상수시간
  * 배열의 맨앞에 추가(제거)하는 경우 뒤의 모든 인덱스들이 새로 업데이트 되기 때문에 O(N)이다.
  * push, pop가 shift,unshift 보다 빠름.
  */
  검색 : O(N) // 배열의 길이가 길어질 수록 길어짐.
  접근 : O(1) // N개가 있어도 배열의 접근은 특정 인덱스를 찾아가는 항상 상수 시간이다.
```

---

### 빅오 배열 메소드

```js
push : O(1) // 맨뒤에 추가만 하면되므로
pop : O(1)

shift : O(N) // 모든 인덱스를 다시 정해줘야 하므로
unshift : O(N)
concat : O(N) // O(N+M)
slice : O(N) // 복사하는 엘리먼트의 갯수만큼
splice : O(N) // O(N)
sort : O(N * logN) // O(N)보다 크다. ( 추후 깊게 다룰 예정 )
forEach/map/filter/reduce/etc. : O(N) // 엘리먼트마다 한 작업씩..
```
