## Extract the domain name from a URL
https://www.codewars.com/kata/514a024011ea4fb54200004b

### 문제
Write a function that when given a URL as a string, parses out just the domain name and returns it as a string. For example:
```
domainName("http://github.com/carbonfive/raygun") == "github" 
domainName("http://www.zombie-bites.com") == "zombie-bites"
domainName("https://www.cnet.com") == "cnet"
```

5kyu 문제인데 이번엔 쉽게 풀어서 이문제가 왜 5kyu인지는 모르겠다.  
아마 출제자는 다른 방식으로 푸는 걸 의도 한 것 같다.  
하지만, 나는 그냥 replace로 풀었다.

### 풀이
#### 내가 짠 코드
```javascript
function domainName(url){
  return url.substring(url.indexOf('//')).replace('//', '').replace('www.', '').split('.')[0];
}
```
