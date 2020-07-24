---
layout: post
title: "JavaScript 정리 - 2"
author: "Martyhoon"
study : true
type : "javaScript"
text : true
order : 2
---

<br>

<p style="font-size : 10px; color : #e9e9e9" > 아래 글은 공부하고 기억하기 위해 남겨놓는 글이다 </p>

### &#128310; DOM(Document Object Model - HTML요소들의 구조화된 표현) 

&nbsp;&nbsp;<span style ="border-bottom : 3px soild #be4e7f8; box-shadow : inset 0 -4px 0 #b4e7f8;">JavaScript가 나의 html에 있는 모든 요소를 가지고 올 때 사용하는 프로그래밍 인터페이스이다. </span> JS는 DOM을 통해 HTML의 요소들에 접근하여 객체로 바꾸어 사용한다. 그 반대도 가능하다. DOM은 HTML의 요소들의 구조화된 표현을 제공하여 그들이 문서 구조, 스타일, 내용 등을 변경할 수 있게 돕는다. `tree`형식의 자료구조를 가지고 있다. 

#### DOM의 구조 

* method를 가지고 있는 Object
* 구조화된 nodes 와 property

HTML에서 DOM의 최상위 노드는 Document이다. DOM은 이러한 노드들을 정의하고, 그들 사이의 관계를 설명해 주는 역할을 한다.

![DOM](/study/2020-JS-summary2/img/DOM.png)

```js
//JS에서 이런식으로 DOM을 조작한다.

const title = document.getElementById("title");
title.innerHTML = "New Titile";

```

<br>
