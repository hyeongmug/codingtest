## Simple Pig Latin
https://www.codewars.com/kata/520b9d2ad5c005041100000f/train/javascript

### 문제
Move the first letter of each word to the end of it, then add "ay" to the end of the word. Leave punctuation marks untouched.

Examples
```
pigIt('Pig latin is cool'); // igPay atinlay siay oolcay
pigIt('Hello world !');     // elloHay orldway !
```
example만 봐도 문제는 금방 이해됨

### 풀이
#### 내가 짠 코드
```javascript
function pigIt(str){
  return str.split(" ").map(v => {
    if ("!?.".indexOf(v) > -1) return v;
    let x = v.substring(1) + v.substring(0,1);
    return x + "ay";
  }).join(" ");
}
```

#### 다른사람이 짠 코드
```javascript
function pigIt(str){
  return str.replace(/(\w)(\w*)(\s|$)/g, "\$2\$1ay\$3")
}
```

아니, 정규 표현식을 사용하면 이렇게 짧아진다고? 좀 충격인데..  
테스트 해보니까 잘 작동된다.   
하지만 정규표현식을 잘 모르니까 이해가 안된다.   
**정규표현식 공부좀 해야겠다.**
