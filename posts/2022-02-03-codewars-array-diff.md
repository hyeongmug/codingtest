## Array Diff
https://www.codewars.com/kata/523f5d21c841566fde000009/train/javascript

### 문제
Your goal in this kata is to implement a difference function, which subtracts one list from another and returns the result.

It should remove all values from list a, which are present in list b keeping their order.
```javascript
arrayDiff([1,2],[1]) == [2]
```
If a value is present in b, all of its occurrences must be removed from the other:
```javascript
arrayDiff([1,2,2,2,3],[2]) == [1,3]
```


### 풀이
#### 내가 맨 처음에 짠 코드
```javascript
function arrayDiff(a, b) {
    const result = [];
    for (let i = 0; i < a.length; i++) {
        if (b.indexOf(a[i]) == -1){
            result.push(a[i]);
        }
    }
    return result;
}
```
1. a배열로 for문을 돌린다. 
2. indexOf를 사용해서 a배열에서 꺼내온 값(a[i])이 b배열에 있는지 확인한다. 
3. a배열에서 꺼내온 값(a[i])이 b배열에 없으면 a[i]를 result배열에 push 한다.
4. for문을 다 빠져 나오면 result배열을 return 한다. 

#### filter()와 includes()를 사용해서 리팩토링
```javascript
function arrayDiff(a, b) {
    return a.filter(v => {
        return !b.includes(v);
    })
}
```

코드가 좀 더 간결해졌다.

같은 결과를 보여주는 코드여도 리팩토링한 것처럼 filtter나 includes를 사용해서 코드를 얼마나 함축 시키느냐는 한 언어에 대해서 얼마나 잘 알고 활용하는지를 알 수 있기 때문에 중요한 것 같다.

### 배운 것
Array.prototype.filter() - https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/filter
Array.prototype.includes() - https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/includes

아는 만큼 보인다.  
갈 길이 멀다.  
