---
title: '대화 상자 ( Alert, Confirm, Prompt )'
date: 2021-03-12 18:18:00
category: 'javascript'
draft: false
---

## 자바스크립트의 대화 상자 3가지
  - Alert, Confirm, Prompt
  - 모달 창의 뷰는 브라우저마다 상이함.



### 1. Alert
- 단순한 메세지 전달의 대화상자를 여는 함수로, 반환하는 값이 따로 없다.

  ```js
    alert( 'message!' );
  ```

  ![](./images/alert.png)

<br/>

### 2. Confirm
- 확인, 취소 버튼 클릭에 따라 true, false 값을 반환한다.

  ```js
    const result = confirm('message confirm!');

    // click confirm
    console.log(result) // true

    // click cancel
    console.log(result) // false
  ```

  ![](./images/confirm.png)

<br/>

### 3. Prompt
- 입력창이 들어가있는 형태로, 입력값을 반환한다. (기본값을 넣을 수 있음.)

  ```js
    const result = prompt('message confirm!', 'default value');

    // input value
    console.log(result) // default value

    // 취소를 클릭할 시, null을 반환함.
  ```

  ![](./images/prompt.png)

<br/>

###

---

- 브라우저 마다 상이한 뷰와, 기본적인 디자인에 제약사항으로<br/>
  현업에서는 팝업 디자인을 따로 제작해서 사용하는 편이다.