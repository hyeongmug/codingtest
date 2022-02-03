## Pangram 판별 하기
https://www.codewars.com/kata/545cedaa9943f7fe7b000048/ 

### 문제
> A pangram is a sentence that contains every single letter of the alphabet at least once. For example, the sentence "The quick brown fox jumps over the lazy dog" is a pangram, because it uses the letters A-Z at least once (case is irrelevant).
>
> Given a string, detect whether or not it is a pangram. Return True if it is, False if not. Ignore numbers and punctuation.


난 영어를 못하니까 번역기로 번역을 하고... 

> 팬그램은 알파벳의 모든 단일 문자를 적어도 한 번 포함하는 문장입니다. 예를 들어, "빠른 갈색 여우가 게으른 개를 뛰어 넘다"라는 문장은 A-Z 문자를 한 번 이상 사용하기 때문에 팬그램입니다(대소문자는 관계 없음).
>
> 문자열이 주어지면 그것이 팬그램인지 여부를 감지합니다. 있으면 True, 그렇지 않으면 False를 반환합니다. 숫자와 구두점을 무시하십시오.

아 pangram이 저런거였구나.. 끄덕 끄덕

그럼 이제 문제를 풀어 본다.

### 풀이
#### 내가 맨 처음에 짠 코드
```javascript
function isPangram(string){
    const letters = "qwertyuiopasdfghjklzxcvbnm";
    const str = string.toLowerCase();

    for (let i = 0; i < letters.length; i++) {
        if(str.indexOf(letters[i]) == -1) {
            return false;
        }
    }

    return true;
}
```
1. letters 라는 변수에 키보드 자판 순서대로 알파벳 입력해 넣어준다.
2. 문제에서 대소문자 구분 안한다고 했으므로 string을 소문자로 변환해서 str변수에 넣어준다.
3. 리턴해 줄 결과 값 변수로 result 변수에 true를 미리 정의 함
4. letters로 for문을 돌려서 알파벳 하나씩 비교해서 검증 
5. letters의 글자들(a~z)이 string에 포함 안되어 있으면 false 리턴한다.
6. for문이 완벽하게 돌고 빠져나오면 string에 letters의 글자들(a~z)이 모두 포함되어 있다는 뜻이므로 true를 리턴한다.

#### every() 메서드 사용해서 리팩토링
```javascript
function isPangram(string) {
    const str = string.toLowerCase();
    const letters = "qwertyuiopasdfghjklzxcvbnnm".split("");
    return letters.every(val=>str.indexOf(val) > -1);
}
```
코드가 좀 더 간결해졌다.  

### 배운 것 
Array.prototype.every() - https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/every  

아는 만큼 보인다.  
갈 길이 멀다.  