## Split Strings
https://www.codewars.com/kata/514b92a657cdc65150000006

### 문제
Complete the solution so that it splits the string into pairs of two characters. If the string contains an odd number of characters then it should replace the missing second character of the final pair with an underscore ('_').

Examples:
```
solution('abc') // should return ['ab', 'c_']
solution('abcdef') // should return ['ab', 'cd', 'ef']
```

### 풀이
#### 내가 짠 코드
```javascript
function solution(str){
    var arr = [];
    for (var i = 0; i < str.length; i += 2) {
        var cut = str.substring(0 + i, 2 + i);
        if (cut.length == 1) {
            cut += "_";
        }
        arr.push(cut);
    }
    return arr;
}
```

#### 다른사람이 짠 코드
https://www.codewars.com/kata/515de9ae9dcfc28eb6000001/solutions/javascript  

의외로 코드들이 천차만별, 각자의 개성이 보이는 다양한 해법들이 존재한다.

그 중에서도 역시 갑 중의 갑은 정규표현식으로 짠 코드!
```javascript
function solution(s){
    return (s+"_").match(/.{2}/g)||[]
}
```
깔끔하게 3줄 ㅋㅋ 정말 리스팩한다.

역시 문자열 다루는 문제는 정규식을 써줘야 되는 듯.