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
### &#128310; Extended Euclidean Algorithm

2개의 정수 a,b가 존재할 시, 아래의 식을 만족하는 정수 s와 t를 찾을 수 있다. <br><br>

<p style="font-size: 20px; text-align : center; font-weight : bold;">s*a + t*b = gcd(a,b) </p> <br><br>

예제) a= 161 이고  b =28 일 때 gcd(a,b)와 s, t를 구하시오

|   q       |r1 &nbsp; r2|  r  |s1 &nbsp; s2|  s  | t1 &nbsp; t2| t   |
|:------:|:----------:|:---:|:----------:|:---:|:-----------:|:---:|
|5         |161 &nbsp; &nbsp; 28 | 21|1 &nbsp; &nbsp; 0 | 1| 0 &nbsp; &nbsp; 1 | -5 |
|1|28 &nbsp; 21| 7|0 &nbsp; &nbsp; 1 | -1| 1 &nbsp; &nbsp; -5 | 6 |
|3|21 &nbsp; 7| 0 |1 &nbsp; &nbsp; -1 | 4| -5 &nbsp; &nbsp; 6 | -23 |
|| <strong>7</strong> &nbsp; 0| | <strong>-1</strong> &nbsp; 4 | | <strong>6</strong> &nbsp; -23| |
{:.mbtablestyle}
<br>
gcd(a,b) = 7, s = -1 t= 6 이 된다. (초기 s1 s2 : 1 0 , t1 t2 : 0 1)

<br><br>

이러한 확장 유클리드 알고리즘을 사용하여 `Linear Diophantine Equation(부정방정식)`풀 수 있다. 부정방정식 기본 type은 `ax + by =c` 이고 a,b,c는 주어지고 x,y를 구하는 갓이다. <br>
d = gcd(a,b)라 할 때 
* `c%d != 0` 이면 해가 없고
* `c%d == 0` 이면 해가 무수히 많다.

ax + by = c를 d로 나눈다. a'x + b'y = c' 이 때 a', b'는 서로소 이기 때문에 최대공약수는 1이 된다. 그럼 위의 식을 이용하면 a's+ b't = 1이 된다. 위를 통해 s,t를 구하고

* a'x + b'y = c'
* a's+ b't = 1

를 풀면 `x0 = (c/d)s, y0 = (c/d)t` 란 특수해가 하나 구해진다. 이를 통해 일반해를 구하면 아래의 결과가 나온다. (k는 정수)
 
* x = x0 + k(b/d)
* y = y0 - k(a/d)

<br><br>

### &#128310; 관련 문제

* [백준 알고리즘 - 캔디 분배](https://www.acmicpc.net/problem/3955)
* [백준 알고리즘 - 역원 구하기](https://www.acmicpc.net/problem/14565)
* [백준 알고리즘 - 피보나치 문제해결전략](https://www.acmicpc.net/problem/10327)



