## Multiples of 3 or 5
https://www.codewars.com/kata/514b92a657cdc65150000006

### 문제
If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Finish the solution so that it returns the sum of all the multiples of 3 or 5 below the number passed in. Additionally, if the number is negative, return 0 (for languages that do have them).

Note: If the number is a multiple of both 3 and 5, only count it once.


### 풀이
#### 내가 짠 코드
```javascript
function solution(number){
    let sum = 0;
    
    if (0 > number) return 0;
    
    for (let i = 1; i < number; i++) {
        if (i % 3 == 0 || i % 5 == 0) {
            sum += i;
        }
    }
    return sum;
}
```

사실 위 코드에는 불필요한 코드가 존재한다.   

바로 이 부분이다.
```javascript
if (0 > number) return 0;
```
해당 코드는 number가 음수이면 0을 반환하라고 해서 작성한 코드이다.   

그러면 이 부분이 왜 불필요한 코드일까?

그 이유는 for문에서 number의 값이 음수이면 i의 값보다 작기 때문에 for문이 실행되지 않기 떄문이다.  

만약 `number`가 `-10`이라면 `1 < -10` 이 되어서 for문이 실행되지 않는다.  

그렇기 때문에 결과는 초기에 `sum`에 선언한 `0`이 리턴된다. 

그래서 위의 코드는 다음과 같이 수정하는 것이 좋다.

#### 수정한 코드
```javascript
function solution(number){
    let sum = 0;
    for (let i = 1; i < number; i++) {
        if (i % 3 == 0 || i % 5 == 0) {
            sum += i;
        }
    }
    return sum;
}
```

### 오늘의 교훈
for문에 음수가 들어가는 경우가 있을 것을 생각해서 코딩하자.