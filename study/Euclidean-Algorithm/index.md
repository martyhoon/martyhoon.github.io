---
layout: post
title: "Euclidean Algorithm"
author: "Martyhoon"
study : true
type : "algorithm"
text : true
date : "2020-09-13"
order : 8
---

### &#128310; Euclidean Algorithm

위 알고리즘은 기존의 최대공약수를 구하는 방식인 소인수분해를 통해 공통인수를 구하고 그 중 가장 높은 수를 구하는 방식을 사용했다. 이번에는 이러한 복잡한 과정없이 최대공약수를 구하는 유클리드 알고리즘을 알아보겠다. 이를 활용하면 훨씬 효율적으로 최대공약수를 구할 수 있다.
<br><br>
유클리드 알고리즘의 기본정의는 아래와 같다.

* Fact 1 : gcd(a, 0) = a
* Fact 2 : gcd(a,b) = gcd(b,r)일 때 r은 a를 b로 나눈 나머지이다.

```js 
function gcd(a,b){
  
  let r1 = a;
  let r2 = b;
  let r,q;
  
  while(r2 > 0){
  
  q = Math.floor(r1/r2);

  r = r1- q* r2;
  r1 = r2; 
  r2 = r;  
    
  }
  
  return r1;
}
```



