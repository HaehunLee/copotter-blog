---
title: 'HTML #2. HTML의 기초'
date: 2021-02-22 23:30:00
category: 'html'
draft: false
---

## HTML

- HyperText Markup Language

  > - HyperText : 문서의 링크를 클릭하면 연결된 다른 문서로 이동할 수 있는 기능을 제공하는 텍스트

  > - Markup : 문서의 어느 부분이 제목이고, 어느 부분이 본문이고, 어느 부분이 링크인지를 표시하기 위해서 특별한 기호(마크업)가 사용된다.

- 웹에서 웹 문서간에 빠르게 이동할 수 있는 문서를 만들 때 사용되는 언어가 HTML이다.

## Tag (태그)

- 태그는 '<'와 '>'로 구성된다.
  > ```<title> <body> <img> <table> <ul>```

- 태그는 이름의 소문자로 적는다.

- 태그는 여는 태그와 닫는 태그가 쌍으로 구성된다.
  > ```여는 태그 : <table> <body> <head>``` <br/>
  > ```닫는 태그 : </table> </body> </head>```

- 여는태그와 닫는 태그 사이에는 컨텐츠가 다른 태그가 포함될 수 있다.
  ```html
  <h1>html태그 연습 </h1>
	<p>
      html은 웹 문서를 만들 때 사용되는 언어이다.
      html은 프로그래밍 언어라고 부르기는 좀...
  </p>
	<p><span>1위</p>방탄소년단</span> << 틀린 문법
  ```

- 태그는 속성을 가질 수 있다.
	> ```속성은 속성명="속성값"으로 구성된다.```<br/>
	```html
  <img src="images/cat.jpg" width="300" height="200" alt="예쁜 고양이">
  ```

- 태그간의 포함관계를 정확하게 표현해야 된다.
  ```html
  <div>
      <p>태그안에 다른 태그가 포함될 때는 여는 태그와 닫는 태그의 쌍을 맞춰야 한다.</p>
  </div>
  ```


  ## html문서의 기본 구조

  ```html
  <!doctype html>
    <html>
      <head>
        <meta charset="utf-8" />
        <title>처음으로 작성하는 html 문서</title>
      </head>
      <body>
        <h1>문서의 제목을 포함한다.</h1>

        <p1>내용을 포함한다.</p>
      </body>
    </html>
  ```

  > ```<!doctype html>``` : 현재 문서가 html 작성규칙에 맞춰서 작성된 웹 문서임을 나타낸다.

  > ```<html> ~ </html>``` : 웹 문서의 시작과 끝을 나타낸다.

  > ```<head> ~ </head>``` : 웹브라우져가 웹 문서를 해석하는데 필요한 정보를 입력하는 부분이다.
  > 이 부분에 있는 정보는 실제 문서내용이 아니기 때문에 화면에 표시되지 않는다.

  > ```<body> ~ </body>``` : 실제로 웹 브라우져에 표시되는 내용을 포함한다.
  > 우리가 배우는 거의 대부분의 태그는 <body> 태그 안에 들어간다.

<br/>

  ```html
  <!doctype html>
    <html lang="ko">
      <head>
        <!--
            meta태그는 화면에 글자를 표시하는 문자 인코딩 방식을 지정한다.
            한글 문서인 경우 utf-8 인코딩방식을 사용한다.
            단축키 : ctrl + shift + /
          -->
        <meta charset="utf-8">
        <!--
            title태그는 문서의 제목을 포함한다.
            웹 브라우져의 제목 표시줄(탭)에 표시된다.
        -->
        <title>문서 제목</title>
      </head>
      <body>
        <!-- body태그에 포함된 내용은 실제 웹 브라우져에 표시된다. -->
        <h1>HTML 연습</h1>
        <p>HTML 연습시간에는 HTML의 주요 태그와
          각 태그의 속성을 공부해보도록 하겠습니다.</p>
      </body>
    </html>
  ```

## Fin.

기본적인 HTML의 기초 설명과, 기본 구조에 대해서 다뤄봤습니다.<br/>
다음 시간에는, HTML기본구조의 상세설명과 태그에 대해서 브라켓을 통해서 다뤄보도록 하겠습니다.