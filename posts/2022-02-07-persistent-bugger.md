## Persistent Bugger.
https://www.codewars.com/kata/55bf01e5a717a0d57e0000ec/train/javascript

### 문제
Write a function, persistence, that takes in a positive parameter num and returns its multiplicative persistence, which is the number of times you must multiply the digits in num until you reach a single digit.

For example (Input --> Output):
```
39 --> 3 (because 3*9 = 27, 2*7 = 14, 1*4 = 4 and 4 has only one digit)
999 --> 4 (because 9*9*9 = 729, 7*2*9 = 126, 1*2*6 = 12, and finally 1*2 = 2)
4 --> 0 (because 4 is already a one-digit number)
```

### 풀이
#### 내가 처음에 짠 코드
```javascript
function a(num, i=0) {
  if (num.toString().length == 1) {
    return i;
  }
  let num2 = num.toString().split("").reduce((p, v) => {
    return p * parseInt(v);
  });
  return a(num2, ++i);
}

function persistence(num) {
   return a(num);
}
```

재귀로 짜보고 싶어서 이렇게 했다가 무한루프 몇번 빠지고, 헷갈리고..ㅋㅋ;;  
사실 for문 사용하면 간단한데 재귀 한번 써보겠다고 왜 이렇게 짰나 싶다.

#### for문으로 리팩토링 한 코드
```javascript
function persistence(num) {
  let i = 0;
  for (i; 1 < num.toString().length; i ++) {
    num = num.toString().split("").reduce((p, v) => {
      return p * v;
    })
  }
  return i;
}
```
처음 짠 코드 보다 익숙한 for문을 사용해서 가독성도 좋아지고 이해하기 쉬워졌다.

### 교훈
빠른 길을 놔두고 먼길로 돌아가지 말 것
