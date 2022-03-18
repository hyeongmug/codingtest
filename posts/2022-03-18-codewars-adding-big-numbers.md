## Adding Big Numbers
https://www.codewars.com/kata/525f4206b73515bffb000b21

### 문제
We need to sum big numbers and we require your help.

Write a function that returns the sum of two numbers. The input numbers are strings and the function must return a string.

#### Example
```
add("123", "321"); -> "444"
add("11", "99");   -> "110"
```

#### Notes
- The input numbers are <i>big</i>.
- The input is a string of only digits
- The numbers are positives

### 풀이
#### 내가 짠 코드
```javascript
function add(a, b) {
    var sum = "",
        result = "",
        carry = 0,
        idx1 = a.length - 1,
        idx2 = b.length - 1;

    while(a[idx1] || b[idx2] || carry != 0) {
        sum = (Number(a[idx1] || 0) + Number(b[idx2] || 0) + carry).toString();
        if (sum.length == 2) {
            carry = Number(sum[0]);
            result = sum[1] + result;
        } else {
            carry = 0;
            result = sum + result;
        }
        idx1--;
        idx2--;
    }
    return result;
}
```

#### 다른사람이 짠 코드
```javascript
function add (a, b) {
    var res = '', c = 0
    a = a.split('')
    b = b.split('')
    while (a.length || b.length || c) {
        c += ~~a.pop() + ~~b.pop()
        res = c % 10 + res
        c = c > 9
    }
    return res
}
```
#### 코드 비교
공통점
- 실제로 계산 하는 것 처럼 맨 끝 자리 부터 더한 후에 받아올림 하는 방식으로 풀어낸 것

차이점
- 우선 다른사람 코드가 더 짧다, 그리고 더 효율적인 것 같다.
- 맨 끝자리부터 숫자 하나씩 가져오기
  - 내 코드 : a, b 각각 가장 끝 인덱스 구해서 -1씩 감소 시켜서 가져온다.  
  - 다른 사람 코드 : 문자열을 배열로 변환해서 `.pop()`으로 끝부터 하나씩 뺴낸다.
- 받아올림 구하기
  - 내코드 : 더한 수가 2자리면 첫 자리 수를 `carry` 변수에 저장
  - 다른 사람 코드 : 더한 수가 9보다 크면 더한 수를 `c` 변수에 저장
- 문자열에서 숫자로 형 변환
  - 내코드 : `Number()` 를 사용
  - 다른 사람 코드 : `~` 를 사용
    - `~` 은 비트 NOT 연산자 인데 자바스크립트에서 문자타입 숫자에 `~`을 두번 써주면 숫자타입으로 반환된다. (ex. `~~'112'` => `112`)

#### 배운 것
~~ 의 사용
