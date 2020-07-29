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

특정한 화면 요소에서 이벤트가 발생했을 때 <span style ="border-bottom : 3px soild #be4e7f8; box-shadow : inset 0 -4px 0 #b4e7f8;">해당 이벤트가 더 상위의 화면 요소들로 전달되어 가는 특성</span>
<br><Br>
예를 들면 아래와 같다. 

```html
  <div class="big"> Big!
    <div class="middle"> Middle!
      <div class="small"> Small!
        </div>
    </div>
  </div>
```

```js
const divs = document.querySelectorAll('div');

divs.forEach(function(div) {
	div.addEventListener('click', e =>{
    console.log(event.currentTarget.className);
  });
});
```
위와 같이 코드를 작성하고 `<div class="small"></div>`을 누르게 되면 아래와 같은 결과가 나온다.

![Result](/study/2020-JS-Event/img/resultBubble.png)

 <br>
보시다 시피 `small`-> `middle` -> `big` 으로 이벤트가 전달되는 것을 알 수 있다. 대부분의 이벤트는 버블링이 된다. 만약 상위 요소에 이벤트가 등록이 되어있지 않다면 확인할 수 없다. 이러한 버블링을 제한하려면 `event.stopPropagtaion()`을 사용하면 된다. 주의할 점은 꼭 필요한 상황이 아니면 쓰지 말자! 

```js
  function logEvent(event) {
	event.stopPropagation();
    }
```


### &#128310; Event Capture

특정한 화면 요소에서 이벤트가 발생했을 때 <span style ="border-bottom : 3px soild #be4e7f8; box-shadow : inset 0 -4px 0 #b4e7f8;">버블링과는 반대로 해당 이벤트가 전달되어 가는 특성</span>

```html

  <div class="big"> Big!
    <div class="middle"> Middle!
      <div class="small"> Small!
        </div>
    </div>
  </div>

```

```js
const divs = document.querySelectorAll('div');
divs.forEach(function(div) {
	div.addEventListener('click', logEvent, {
		capture: true // default 값은 fals
	});
});

function logEvent(event) {
	console.log(event.currentTarget.className);
}
```

위와 같이 코드를 작성하고 `<div class="small"></div>`을 누르게 되면 아래와 같은 결과가 나온다.

![Result2](/study/2020-JS-Event/img/resultCapture.png)
<br>

`big`-> `middle` -> `small` 으로 이벤트가 전달되는 것을 알 수 있다. 여기서도 만약 원하는 이벤트만 신경쓰고 싶다면 `event.stopPropagtaion()`을 사용하면 된다.

### &#128310; Event Target

`event.target`은 이벤트가 발생했을 때 가장 안쪽 요소를 의미한다. 위에서는 우리가 실제로 클릭한 `<div class="small"></div>` 가 target이 될 것이다. 하지만 여기서 주의할 점은 `event.target` 과 `event.currentTarget(=this)`은 다르다는 것이다. `this`는 현재 요소로, 현재 실행 중인 핸들러가 할당된 요소를 참조한다. (이벤트가 바인딩된 요소를 반환)

```html
   <div class="big"> Big!
    <h1 class="middle"> Middle!
      <p class="small"> Small!
        </p>
    </h1>
  </div>
```

```js
const divs = document.querySelector('div');

divs.addEventListener('click', logEvent);

function logEvent(event) {
	console.log("target = " + event.target.tagName + ", this=" + this.tagName)
}
```
여기서 `<p>`태그를 누르면 `event.target.tagName : p` 이고  `this.tagName : div`가 된다.



### &#128310; Event Delegation

Vanilla JS로 웹 앱을 구현할 때 자주 사용하게 되는 코딩 패턴이다. 이벤트 위임은 <span style ="border-bottom : 3px soild #be4e7f8; box-shadow : inset 0 -4px 0 #b4e7f8;">하위 요소에 각각 이벤트를 붙이지 않고 상위 요소에서 하위 요소의 이벤트를 제어하는 방식 </span>

```html
    <h1>To Do</h1>
    <ul class="itemList">
	<li>
		<input type="checkbox" id="item1">
		<label for="item1">밥 먹기</label>
	</li>
	<li>
		<input type="checkbox" id="item2">
		<label for="item2">놀기</label>
	</li>
</ul>

```
위와 같은 html 파일이 있고 아래와 같은 이벤트를 input 태그에 등록을 하였다고 가정했을 때

```js

//Event 1
var inputs = document.querySelectorAll('input');
 inputs.forEach(function(input) {
 	input.addEventListener('click', function() {
 		alert('clicked');
	});
});

```

여기서 새로운 `<li>`을 추가하고 눌러 보면 이벤트가 작동하지 않는다.

```js

// 새 리스트 아이템을 추가하는 코드
var itemList = document.querySelector('.itemList');

var li = document.createElement('li');
var input = document.createElement('input');
var label = document.createElement('label');
var labelText = document.createTextNode('새로운 할 일 추가');

input.setAttribute('type', 'checkbox');
input.setAttribute('id', 'item3');
label.setAttribute('for', 'item3');
label.appendChild(labelText);
li.appendChild(input);
li.appendChild(label);
itemList.appendChild(li);

```

왜냐하면 이미 이벤트 리스너를 추가하는 시점에 아이템은 2개이고 따라서 새롭게 추가된 리스트에는 이벤트 리스너가 적용되지 않는다. 그렇다면 이러한 문제를 해결하기 위해서는 어떻게 해야하는가? 이 때 사용하는 것이 `이벤트 위임`이다. 아래와 같이 변경하면 상위 태그인 `<ul>`에 이벤트를 달아놓고 하위에 있는 이벤트를 감지하게 한다.

```js
//앞서 이벤트 리스너를 다음과 같이 변경
var itemList = document.querySelector('.itemList');
itemList.addEventListener('click', function(event) {
	alert('clicked');
});
```