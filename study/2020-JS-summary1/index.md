---
layout: post
title: "JavaScript 정리 - 1"
author: "Martyhoon"
study : true
type : "javaScript"
text : true
date : "2020-07-15"
order : 1
---

<br>

### &#128310; Definition

&nbsp;&nbsp;웹에서 사용되는 프로그래밍 언어, 흔히 Front-End를 개발할 때 사용하는 언어이다. 현재는 웹이 빠르게 발전하면서 같이 빠르게 발전하고 있으며 해당 언어의 개발자들이 할 수 있는 일도 늘어나고 있는 추세이다. <span style ="border-bottom : 3px soild #be4e7f8; box-shadow : inset 0 -4px 0 #b4e7f8;">게임, App, interactive한 것 등 여러 방면에서 사용할 수 있는 굉장히 powerful한 언어이다.</span> (예시 : impact.js, three.js) 그리고 ECMAScript라는 Specification을 통해서 버전을 확인할 수 있다. <span style ="font-weight :bold">여기서는 Vanilla JS를 위주로 다룰 것이다.</span>
<br><br> <span style = "font-weight : bold"> Tip  </span> JS는 보통 body 태그의 마지막 부분에 삽입해준다.


### &#128310; Variable(변수)

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

ES6 이후로는 일반적으로 `const`를 기본으로 사용하고 변경이 될 수 있는 변수는 `let`을 사용한다. <br>
변수명을 작성 시에는 `camel case`로 작성한다. (예시 : daysofweek -> daysOfWeek, 소문자로 시작해서 스페이스가 필요 시 대문자로 작성)

<br>

### &#128310; Strict equal operator(===)

좌항과 우항의 값이 정확하게 같은지 체크할 때 사용 (== 보다는 ===를 사용) 

```js
alert(1 === "1") // false  
alert(1 == "1" ) // true
```
<br>

### &#128310; Data type(Object & Array)

Object와 Array <br>

둘은 데이터를 정렬한다는 공통점이 있지만 Object에는 각 value에 이름 부여할 수 있지만 Array는 그렇지 못한다. Object에 함수도 넣을 수 있다.

```js
const daysOfWeek = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']; // Array  
const people = { name : "Marty" , age : 26, isStudent : true , favFood : ["milk", "apple" ]}; //Object

const grades = {
    list: {name : "hoon",  age: 6 },
    show : function(){
        for(let name in this.list){
            document.write(name+' : '+this.list[name]+"<br/>");
        }
    }
};

grades.show();
```

<br>

### &#128310; Function

함수는 내가 원하는 만큼 코드를 쓸 수 있게 해주는 것이다. 아래는 기본적으로 JavaScript에서 함수를 정의하는 방법이다. 여기서 name, age는 argument에 해당된다.

```js
function sayHello(name, age){

   console.log("Hello " + name + " you are " + age + " years of age.");

   console.log(`Hello ${name} you are ${age} years old`);
   //``은 "", '' 은 매우 다르다. 

}

sayHello("Hoon", 15);
```

return 값이 있다면 이렇게 표현할 수 있다.

```js
function sayHello(name, age){

  return `Hello ${name} you are ${age} years old`;

}

const test = sayHello("Hoon", 15);

console.log(test);
```

아래는 Object와 Function을 활용해서 인자를 2개 받는 계산기를 만들어 보았다.

```js
const calculator = {
 plus : function(a, b){
   return a+b;
 },
 minus : function(a, b){
   return a-b;
 },
 multiple : function(a,b){
   return a*b;
 },
 divide : function (a, b){
    return a/b;
 },
power : function(a, b){
  return a**b;
}

}

const plus = calculator.plus(5, 5);
const minus = calculator.minus(10, 5);
const multiple = calculator.multiple(10, 20);
const divide = calculator.divide(20, 10);
const power = calculator.power(10,2);

console.log(plus);
console.log(minus);
console.log(multiple);
console.log(divide);
console.log(power);
```


<br>
