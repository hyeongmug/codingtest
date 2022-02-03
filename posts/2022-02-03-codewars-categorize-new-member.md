## Categorize New Member
https://www.codewars.com/kata/5502c9e7b3216ec63c0001aa/train/javascript

### 문제
The Western Suburbs Croquet Club has two categories of membership, Senior and Open. They would like your help with an application form that will tell prospective members which category they will be placed.

To be a senior, a member must be at least 55 years old and have a handicap greater than 7. In this croquet club, handicaps range from -2 to +26; the better the player the lower the handicap.

##### Input
Input will consist of a list of pairs. Each pair contains information for a single potential member. Information consists of an integer for the person's age and an integer for the person's handicap.

##### Output
Output will consist of a list of string values (in Haskell: Open or Senior) stating whether the respective member is to be placed in the senior or open category.

Example
```javascript
input =  [[18, 20], [45, 2], [61, 12], [37, 6], [21, 21], [78, 9]]
output = ["Open", "Open", "Senior", "Open", "Open", "Senior"]
```

문제가 길다.. 번역기를 돌려봤다.. 

>Western Suburbs Croquet Club에는 시니어와 오픈의 두 가지 회원 범주가 있습니다. 그들은 예상 회원에게 자신이 배치될 범주를 알려주는 신청서를 작성하는 데 도움을 받기를 원합니다.
>
>시니어가 되려면 회원이 55세 이상이어야 하고 핸디캡이 7 이상이어야 합니다. 이 크로케 클럽의 핸디캡 범위는 -2에서 +26입니다. 더 나은 플레이어는 핸디캡이 낮습니다.
>
>입력  
>입력은 쌍 목록으로 구성됩니다. 각 쌍에는 단일 잠재적 구성원에 대한 정보가 포함되어 있습니다. 정보는 개인의 나이에 대한 정수와 개인의 핸디캡에 대한 정수로 구성됩니다.
>
>산출  
>출력은 해당 구성원이 Senior 또는 Open 범주에 배치되는지 여부를 나타내는 문자열 값 목록(Haskell: Open 또는 Senior)으로 구성됩니다.

이게 무슨말이야.  
다른건 다 무시하고 핵심은:  
나이가 55세 이상이고 핸디캡이 7이상이면 Senior라는 것

### 풀이
#### 내가 짠 코드
```javascript
function openOrSenior(data){
    return data.map(arr => {
        if (arr[0] >= 55 && arr[1] >= 7) {
            return 'Senior';
        }
        return 'Open';
    });
}
```
1. output이 배열이기 때문에 map 메소드를 사용해서 바로 배열을 리턴하기로 한다. 
2. arr[0]이 나이, arr[1]이 핸디캡이다. 
3. 그렇기때문에 arr[0]이 55이상이고 arr[1]이 7이상이면 'Senior'라는 조건을 세운다.
4. 조건에 만족하면 'Senior'를 리턴하고, 그렇지 않으면 'Open'을 리턴한다.

이 문제는 좀 쉬웠다.  
하지만 문제가 긴 경우에 핵심을 파악하는 연습을 좀 해야겠다.