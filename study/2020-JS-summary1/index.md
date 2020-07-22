---
layout: post
title: "JavaScript 정리 -1"
author: "Martyhoon"
study : true
type : "javaScript"
text : true
order : 1
---

<br>

<p style="font-size : 10px; color : #e9e9e9" > 아래 글은 공부하고 기억하기 위해 남겨놓는 글이다 </p>

### Definition

웹에서 사용되는 프로그래밍 언어, 흔히 Front-End를 개발할 때 사용하는 언어이다. 현재는 웹이 빠르게 발전하면서 같이 빠르게 발전하고 있으며 해당 언어의 개발자들이 할 수 있는 일도 늘어나고 있는 추세이다.

### Variable(변수)

 * let
 * const
 * var

`var`은 function-scope이고 `const`와 `let`은 block-scope이다. `var` 제외한 둘의 차이점은 immutable의 여부이다. <br>
`let`은 변수 재할당이 가능하지만, <br>
`const`는 변수 재선언, 재할당이 모두 불가능하다. 하지만 객체나 배열의 원소의 추가나 삭제는 가능하다.

```js
const list = ["banana", "apple", "water"];
list.pop(); //water 삭제
list.push("pineapple"); //pineapple 삽입

console.log(list);
```

ES6 이후로는 일반적으로 `const`를 기본으로 사용하고 변경이 될 수 있는 변수는 `let`을 사용한다.




<br>
