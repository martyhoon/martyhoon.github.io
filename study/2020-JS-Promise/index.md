---
layout: post
title: "JavaScript Promise"
author: "Martyhoon"
study : true
type : "javaScript"
text : true
order : 4
---

<br>

<p style="font-size : 10px; color : #e9e9e9" > 아래 글은 공부하고 기억하기 위해 남겨놓는 글이다 </p>


&nbsp;&nbsp; 이번에는 데이터베이스에서 요청한 데이터를 받아 화면에 표시할 때 사용하는 Promise에 대해 공부해보겠다. 

### &#128310; Promise란?

&nbsp;&nbsp; Promise는 JS 비동기 처리에 사용된느 객체이다. 주로 Get 방식을 요청할 때 사용한다. 그렇다면 왜 사용하는 것일까? <span style ="border-bottom : 3px soild #be4e7f8; box-shadow : inset 0 -4px 0 #b4e7f8;"> 만약 내가 데이터를 보내달라고 요청했는데 데이터를 모두 받아오기 전에 화면에 데이터를 표시하려고 하면 오류가 발생한다. 이를 해결하기 위한 객체이다.</span>

```js
function getData() {
  // new Promise() 객체 추가
  return new Promise(function(resolve, reject) {
    $.get('url', function(response) {
      // 데이터를 받으면 resolve() 호출
      resolve(response);
    });
    reject(new Error("Request is failed"));
  });
}

// getData()의 실행이 끝나면 호출되는 then()
getData().then(function(tableData) {
  // resolve()의 결과 값이 여기로 전달됨
  console.log(tableData); // $.get()의 reponse 값이 tableData에 전달 

}).catch(function(err) {
  console.error(err); // reject 시 Error 출력
});
```
### &#128310; Promise의 3가지 상태 

3가지 상태는 Promise의 처리 과정을 의미한다. `new Promise()`로 Promise를 생성하고 종료할 때까지 3가지 상태를 갖는다.

* Pending(대기) : 비동기 처리 로직이 아직 완료되지 않은 상태
* Fullfilled(이행) : 비동기 처리가 완료되어 프로미스가 결과 값을 반환해준 상태
* Rejected(실패) : 비동기 처리가 실패하거나 오류가 발생한 상태 

#### Pending

`new Promise()` 메서드를 호출하면 대기 상태가 된다.

```js
new Promise(function(resolve, reject) {
  // ...
});
```

#### Fullfilled

여기서 콜백 함수의 인자 `resolve`를 아래와 같이 실행되면 이행 상태가 된다. 이후 `then`을 이용하여 처리 결과 값을 받을 수 있다.
```js
function getData(){
return new Promise(function(resolve, reject) {
   const data = 200;
   resolve(data);
});

}

getData().then(function(resolvedData) {
  console.log(resolvedData); // 100
});

```

#### Rejected

`new Promise()`로 프로미스 객체를 생성하면 콜백 함수 인자로 `resolve`와 `reject`를 사용할 수 있다고 했습니다. 여기서 `reject`를 아래와 같이 호출하면 실패(Rejected) 상태가 됩니다.

```js
new Promise(function(resolve, reject) {
  reject();
});

```

```js
// reject()의 결과 값 Error를 err에 받음
getData().then().catch(function(err) {
  console.log(err); // Error: Request is failed
});

```
