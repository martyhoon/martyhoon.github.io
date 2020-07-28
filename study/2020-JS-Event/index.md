---
layout: post
title: "Vanilla JS Event"
author: "Martyhoon"
study : true
type : "javaScript"
text : true
order : 3
---

<br>

<p style="font-size : 10px; color : #e9e9e9" > 아래 글은 공부하고 기억하기 위해 남겨놓는 글이다 </p>


&nbsp;&nbsp; 이번에는 Vanilla JS에서 Event를 어떻게 등록하고 감지하여 그 이벤트를 어떻게 다른 화면 요소에 전파하는지를 공부하여 정리하였다. Vanilla JS에서 이벤트를 전달하는 방식은 `Event Bubbling` , `Event Capture`, `Event Delegation`로 크게 3가지가 있다.

### &#128310; Vanilla JS에서 Event 사용법

&nbsp;&nbsp; Vanilla JS에서 Event를 등록하여 사용하는 방법은 아래와 같다.

```html
<button class ="btn">item button</button>
```

```js
const btn = document.querySelector(".btn");

btn.addEventListener("click" , event=>{
    console.log("doing something");
});
//addEventListener(A , B) -> A라는 event가 일어났을 때 B라는 함수를 실행한다.
```
### &#128310; Event Bubbling

...작성중

### &#128310; Event Capture

...작성중

### &#128310; Event Delegation

...작성중
