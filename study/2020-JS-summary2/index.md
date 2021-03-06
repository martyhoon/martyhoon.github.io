---
layout: post
title: "JavaScript 정리 - 2"
author: "Martyhoon"
study : true
type : "javaScript"
text : true
date : "2020-07-20"
order : 2
---

<br>


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

### &#128310; JavaScript Event handling

JS에서 HTML의 요소에 접근할 때 document 안의 함수인 querySelector이나 getElement(...)을 사용한다.

```js

docuemnt.querySelector("#title"); //title이란 id를 가진 태그들을 찾고 싶다.
document.getElementById("title"); //위와 비슷한 기능을 한다.

```

JS에서 이벤트를 handling하는 방법은 아래와 같다.


```js

const title = document.querySelector("#title");

function handleClick(){
title.style.color = "blue";
}

title.addEventListener("click", handleClick); //handleClick이란 함수를 내가 필요한 시점에 호출
title.addEventListener("click", handleClick()); //handlClick이란 함수를 지금 바로 호출

```
위는 Click 이벤트 발생 시 title이란 id를 가진 태그의 글자 색깔을 blue로 바꿔준다. 하지만 여기서 주의해야할 것은 event를 받은 후 실행하는 함수의 끝에 `()`을 붙이면 안된다. 붙이게 된다면 사용자가 필요할 때가 아니라 바로 그 즉시 실행이 될 것이다.


#### 예제

js에서 `title.style.color ="blue";` 와 같이 css에 직접 관여하는 것은 그리 좋은 방식이 아니다. 아래는 미리 css에 바꿀 색깔을 정의해 두고 해당 class를 추가해주어 제목 색깔을 바꾸는 예제이다.

```js

const title = document.querySelector("#title");
const CLICKED_CLASS = "clicked";

//1번 코드
function handleClick(){
const hasClass = title.classList.contains(CLICKED_CLASS); //CLICKED_CLASS를 가지고 있는지?

    if(hasClass){
        title.classList.remove(CLICKED_CLASS);
    } else {
        title.classList.add(CLICKED_CLASS); //classList 는 className 추가 
    }
}

function init(){
    title.addEventListener("click", handleClicks);
}

init();
```

위와 같은 handleClick()부분은 아래와 같이 간단하게 변경할 수 있다.

```js
function handleClick(){
    title.classList.toggle( CLICKED_CLASS); //check해서 있으면 add 없으면 remove
}

```

JS의 evnet와 관련된 부분이나 명세들은 아래의 링크에서 볼 수 있다.

[JS MDN web docs of Event](https://developer.mozilla.org/ko/docs/Web/Events)