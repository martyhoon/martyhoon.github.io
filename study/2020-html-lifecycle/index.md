---
layout: post
title: "Lifecycle of an HTML page"
author: "Martyhoon"
study : true
type : "Web"
text : true
order : 5
---

<br>

<p style="font-size : 10px; color : #e9e9e9" > 아래 글은 공부하고 기억하기 위해 남겨놓는 글입니다.</p>

### &#128310; Intro

html 페이지의 lifecycle은 3개의 중요한 event를 가지고 있다.

* <span style ="border-bottom : 3px soild #be4e7f8; box-shadow : inset 0 -4px 0 #b4e7f8; font-weight: bold;"> DOMContentLoaded </span> : Browser에서 HTML이 완전히 로드되고 DOM tree가 만들어 질 때 발생하는 이벤트이다.
* <span style ="border-bottom : 3px soild #be4e7f8; box-shadow : inset 0 -4px 0 #b4e7f8;font-weight: bold;"> load </span> : 문서의 모든 콘텐츠(images,script,css, etc)가 로드된 후 발생하는 이벤트
* <span style ="border-bottom : 3px soild #be4e7f8; box-shadow : inset 0 -4px 0 #b4e7f8;font-weight: bold;"> beforeunload / unload </span> : 사용자가 페이지를 벗어날 때 일어나는 이벤트


### &#128310; DOMContentLoaded

위 이벤트는 onload 이벤트보다 먼저 발생한다. 즉, DOM tree가 완성되면 바로 발생하므로 빠른 실행속도가 필요할 때 적합하다. 다음은 DOMContentLoaded를 이벤트를 다루는 방법들이다.

```js
//vanilla js
window.addEventListener('DOMContentLoaded', function(){ 
    //실행될 코드 
 });

//jQuery
$(document).ready(function(){ 
    //실행될 코드 
});
```

### &#128310; load

위 이벤트는 문서의 모든 콘텐츠가 로드된 후 발생하는 이벤트이다. 이로 인해 불필요한 로딩시간이 추가될 수 있다. 동일한 문서에는 오직 `onload`는 하나만 존재해야 한다.

* 중복될 경우, 마지막 선언이 실행
* 외부 라이브러리에서 이미 선언된 경우 이를 찾아 하나로 합치는 과정 필요

```js
//방법 1
  window.onload = function() {
    alert('Page loaded'); 
  };

//방법 2 
  <body onload="실행될 코드">
```

### &#128310; beforeunload / unload

#### &#10162; beforeunload

사용자가 해당 페이지를 떠날 때 변경 사항을 저장했는지 확인하고 정말 나가기를 원하는지 물어볼 수 있는 이벤트 <br>
사용자가 페이지를 벗어나 탐색을 시작하거나 창을 닫으려고 한다면 beforeunload 핸들러가 추가 확인을 요청한다.

```js
window.onbeforeunload = function() {
  return "변경 사항을 저장하지 않았습니다. 정말 지금 나가시겠습니까?";
};
```


#### &#10162; unload

사용자가 해당 페이지를 떠났지만 통계 전송과 같은 일부 작업을 할 수 있다. 예를 들어 관련 팝업 창을 닫는 것과 같이 지연이 없는 작업을 할 수 있다. 주목할 만한 부분은 분석을 보내는 것이다. 페이지 사용 방식(마우스 클릭, 스크롤 등)에 대한 데이터를 수집한다고 가정할 때 우리는 사용자 우리를 떠날 때 `navigator.sendBeacon(url, data)` 메서드를 통해 백그라운드에서 데이터를 보낼 수 있다. 이 때 다른 페이지로의 전환은 지연되지 않는다. 페이지를 떠났지만 여전히 sendBeacon은 실행이 된다. 아래는 그 예시이다.

```js
let analyticsData = { /* 수집하는 object data */ };

window.addEventListener("unload", function() {
  navigator.sendBeacon("/analytics", JSON.stringify(analyticsData));
};
```

#### &#9997; Tip

일반적으로 스크립트를 문서의 마지막 </body> 이전에 삽입하면 굳이 이벤트를 이용하여 프로그래밍을 처리할 필요가 없다. 하지만 

* 문서의 <head> 영역에 스크립트가 삽입
* 외부의 파일에 정의 (ex) product.js ...etc

위의 2가지 경우 이벤트를 연결하여 문서의 로드시점에 맞게 처리해야 한다. 보통은 그래서 </body> 이전에 js 문서들을 load 시킨다.

##### ※ reference

* [javascript.info](https://javascript.info/onload-ondomcontentloaded) 
* [webdir](https://webdir.tistory.com/515)
