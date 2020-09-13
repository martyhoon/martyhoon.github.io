---
layout: post
title: "JavaScript Sort()"
author: "Martyhoon"
study : true
type : "javaScript"
text : true
date : "2020-09-08"
order : 7
---

<br>


### &#128310; Sort()

&nbsp;&nbsp; 코딩테스트 공부를 하면서 Sort를 많이 사용하는데 생각보다 이 부분 때문에 틀리는 경우가 많아 한 번 정리를 해보려고 한다. 
<br> 기본적으로 `array.sort()`를 사용할 시 <strong>compareFunction</strong>이 제공되지 않으면 요소를 문자열로 변환하고 유니 코드 코드 포인트 순서로 문자열을 비교하여 정렬된다. 
(그래서 숫자 정렬에서는 9가 80보다 앞에 오지만 숫자는 문자열로 변환되기 때문에 "80"은 유니 코드 순서에서 "9"앞에 오기에 주의해야 한다.)

```js
const months = ['March', 'Jan', 'Feb', 'Dec'];
months.sort();
console.log(months);
// expected output: Array ["Dec", "Feb", "Jan", "March"]
```
그리하여 숫자로 정렬하고 싶다면 compareFunction을 지정해야 주어야 한다. 

* `compareFunction(a,b) < 0` : a를 b보다 낮은 색인으로 정렬 (순서 : a, b)
* `compareFunction(a,b) > 0` : b를 a보다 낮은 인덱스로 정렬 (순서 : b, a)
* `compareFunction(a,b) = 0` : a와 b를 서로에 대해 변경하지 않고 모든 다른 요소에 대해 정렬

```js
const list = [4,2,1,3,5];

//오름차순 정렬 
list.sort(function(a,b){

     return a - b; 
     //내림차순 : return b-a;
});
```
다음과 같이 표현할 수도 있다.

```js
//오름차순 정렬 
list.sort(function(a, b) {
  if (a >b) {
    return 1;
  }
  if (a < b) {
    return -1;
  }
  return 0;
});
```


객체에서 value를 기준으로 정렬하고 싶다면 다음과 같이하면 된다.

```js
const list = {

    mark : 1,
    hoon : 12,
    track : 7
};

let keysSorted = Object.keys(list).sort(function(a,b){
            return list[a]-list[b];
});
// ["mark", "track", "hoon"]
```

