## Roman Numerals Encoder
https://www.codewars.com/kata/51b62bf6a9c58071c600001b

### 문제
Create a function taking a positive integer as its parameter and returning a string containing the Roman Numeral representation of that integer.

Modern Roman numerals are written by expressing each digit separately starting with the left most digit and skipping any digit with a value of zero. In Roman numerals 1990 is rendered: 1000=M, 900=CM, 90=XC; resulting in MCMXC. 2008 is written as 2000=MM, 8=VIII; or MMVIII. 1666 uses each Roman symbol in descending order: MDCLXVI.

Example:
```
solution(1000); // should return 'M'
```
Help:
```
Symbol    Value
I          1
V          5
X          10
L          50
C          100
D          500
M          1,000
```
Remember that there can't be more than 3 identical symbols in a row.

More about roman numerals - http://en.wikipedia.org/wiki/Roman_numerals

### 풀이
#### 내가 짠 코드
```javascript
function solution(number){

  const roman = {M: 1000,CM: 900,D: 500,CD: 400,C: 100,XC: 90,L: 50,XL: 40,X: 10,IX: 9,V: 5,IV: 4,I: 1};
  let result = "";
  
  for(key in roman) {
    
    const value = roman[key];
    let quotient = parseInt(number / value);
    
    while(quotient > 0) {
      quotient--;
      number-=value;
      result+=key; 
    }
  }
  return result;
}
```

#### 다른사람이 짠 코드
```javascript
function solution(number){
  var roman = {M: 1000,CM: 900,D: 500,CD: 400,C: 100,XC: 90,L: 50,XL: 40,X: 10,IX: 9,V: 5,IV: 4,I: 1};
  var str = '';
  for (var i of Object.keys(roman)) {
    var q = Math.floor(number / roman[i]);
    number -= q * roman[i];
    str += i.repeat(q);
  }
  return str;
}
```

#### 코드 비교
- roman 오브젝트에서 key와 value 꺼내기
  - 내 코드는 for...in문 사용
  - 다른사람 코드는 Object.keys 로 키를 배열로 뽑아서 for...of문 사용
- 반복 문자열 붙이기
  - 내 코드는 while문을 사용해서 한글자씩 문자열을 붙임
  - 다른사람 코드는 repeat메서드를 사용해서 간단하게 해결함

### 배운 것
- String.prototype.repeat()
  - https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/repeat
