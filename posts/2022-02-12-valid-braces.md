## Valid Braces
https://www.codewars.com/kata/5277c8a221e209d3f6000b56/train/javascript/6201d0e9778de2f26e3ef278

### 문제
Write a function that takes a string of braces, and determines if the order of the braces is valid. It should return true if the string is valid, and false if it's invalid.

This Kata is similar to the Valid Parentheses Kata, but introduces new characters: brackets [], and curly braces {}. Thanks to @arnedag for the idea!

All input strings will be nonempty, and will only consist of parentheses, brackets and curly braces: ()[]{}.

What is considered Valid?
A string of braces is considered valid if all braces are matched with the correct brace.

Examples
```
"(){}[]"   =>  True
"([{}])"   =>  True
"(}"       =>  False
"[(])"     =>  False
"[({})](]" =>  False
```

### 시행착오

```javascript
function validBraces(braces){
  var errorCases = ["(]","(}","{)","{]","[)","[}"];
  for(v of errorCases){
    if(braces.indexOf(v) > -1){
      return false;
    }
  }
  return true;
}
```
TEST 클릭 하니까 성공이다. 
그러나 ATTEMPT 에서 실패이다.  
{()] 와 같은 케이스를 고려하지 못했다.  

그리고 다른 방법으로도 해봤으나 해결하지 못했다.   

6급 문제였는데, 결국 풀지 못하고,  
솔루션을 참고하여 깨달음을 얻은 뒤 내 방법으로 다시 짜보았다.

### 풀이
#### 내가 짠 코드
```javascript
function validBraces(braces){
  while(true){
    var tmp = braces;
    braces = braces.replace("[]","").replace("{}","").replace("()",""); 
    if(tmp == braces){
      if(braces == ""){
        return true;
      }
      return false;
    }
  }
}
```

1. while문을 사용해서 replace을 사용해서 tmp와 brace가 같아 질 때 까지 '{}', '[]', '()' 을 지운다.
2. '{}', '[]', '()'로 더이상 지울 것이 없을 때 while문이 종료된다.
3. 다 지워져서 ''이면 true, 나머지는 false 이다. 


핵심은 주어진 매개변수로 주어진 문자열에서 '{}', '[]', '()' 을 지울 수 있을 때까지 지우고, 지워진 결과가 빈 문자열이면 true라는 것이다.

```
'[({})](]' -> '[()](]' -> '[](]' -> false
'([{}])[]' -> '([])' -> '()' -> '' -> true
```


