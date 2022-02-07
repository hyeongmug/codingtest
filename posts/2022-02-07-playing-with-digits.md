## Complementary DNA
https://www.codewars.com/kata/554e4a2f232cdd87d9000038/train/javascript

### 문제
Some numbers have funny properties. For example:

> 89 --> 8¹ + 9² = 89 * 1

> 695 --> 6² + 9³ + 5⁴= 1390 = 695 * 2

> 46288 --> 4³ + 6⁴+ 2⁵ + 8⁶ + 8⁷ = 2360688 = 46288 * 51

Given a positive integer n written as abcd... (a, b, c, d... being digits) and a positive integer p

- we want to find a positive integer k, if it exists, such as the sum of the digits of n taken to the successive powers of p is equal to k * n.

In other words:

> Is there an integer k such as : (a ^ p + b ^ (p+1) + c ^(p+2) + d ^ (p+3) + ...) = n * k

If it is the case we will return k, if not return -1.

Note: n and p will always be given as strictly positive integers.
```
digPow(89, 1) should return 1 since 8¹ + 9² = 89 = 89 * 1
digPow(92, 1) should return -1 since there is no k such as 9¹ + 2² equals 92 * k
digPow(695, 2) should return 2 since 6² + 9³ + 5⁴= 1390 = 695 * 2
digPow(46288, 3) should return 51 since 4³ + 6⁴+ 2⁵ + 8⁶ + 8⁷ = 2360688 = 46288 * 51
```

### 풀이
#### 내가 짠 코드
```javascript
function digPow(n, p){
  let sum = 0;
  const arr = n.toString().split('');
  
  for (let i = 0; i < arr.length; i++) {
    sum += arr[i] ** (i+p);
  }
  
  let result = sum / n;
  
  if (result.toString().indexOf('.') > -1) {
    return -1;
  }
  
  return result;
}
```

#### 다른사람이 짠 코드
```javascript
function digPow(n, p){
  var ans = n.toString().split('')
             .map((v,i) => Math.pow(parseInt(v), i+p))
             .reduce((a,b) => a+b) / n;
  return ans%1 == 0 ? ans : -1;
}
```
제곱값을 Math.pow()를 사용해서 구했고, 합산은 reduce()를 사용 했다.

### 어려웠던 점
- 우선 문제가 영어이기 때문에 문제파악을 하는데 힘들었다. (인풋 형태와 아웃풋 형태를 보면서 유추한다.)
- 제곱 ^기호와 ** 연산자가 헷갈렸다.
  - 제곱은 수식에서 ^기호를 사용하지만 프로그래밍 언어에서는 ** 연산자를 사용한다.

### 배운 점 
- Math.pow()을 사용해서 제곱값을 구할 수 있다.
- 정수 여부는 나머지 연산(%)울 사용해서 알아 낼 수 있다. 
- Array.prototype.reduce()
  - https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce
