## 완주하지 못한 선수
https://programmers.co.kr/learn/courses/30/lessons/42576?language=javascript

### 문제
####문제 설명
수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.

####제한사항
마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.\
completion의 길이는 participant의 길이보다 1 작습니다.\
참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.\
참가자 중에는 동명이인이 있을 수 있습니다.

####입출력 예
```
participant	completion	return
["leo", "kiki", "eden"]	["eden", "kiki"]	"leo"
["marina", "josipa", "nikola", "vinko", "filipa"]	["josipa", "filipa", "marina", "nikola"]	"vinko"
["mislav", "stanko", "mislav", "ana"]	["stanko", "ana", "mislav"]	"mislav"
```
입출력 예 설명
예제 #1
"leo"는 참여자 명단에는 있지만, 완주자 명단에는 없기 때문에 완주하지 못했습니다.

예제 #2
"vinko"는 참여자 명단에는 있지만, 완주자 명단에는 없기 때문에 완주하지 못했습니다.

예제 #3
"mislav"는 참여자 명단에는 두 명이 있지만, 완주자 명단에는 한 명밖에 없기 때문에 한명은 완주하지 못했습니다.

### 작성한 코드
#### 정확성만 통과한 코드
```javascript
function solution(participant, completion) {
    let str = "," + participant.join(",,") + ",";
    for (let name of completion) {
        str = str.replace(',' + name + ',',"");
    }
    return str.replace(/\,/g,'');
}
```
```javascript
function solution(participant, completion) {
    for (name of completion) {
        const idx = participant.indexOf(name);
        if (idx > -1) {
            participant.splice(idx, 1);
        }
    }
    return participant.toString();
}
```

위 코드들은 무난히 정확성 테스트는 통과 하였다. 하지만 효율성에서 통과 하지 못한다.

효율성 테스트에 대해서 다음과 같은 글을 찾아 보았다.

#### 코딩 테스트의 점수 산출 방법

>코딩 테스트의 경우 [정확성]과 [효율성]으로 구분해서 점수를 계산합니다.
>
>[정확성] 테스트는 지원자가 제출한 코드가 문제 지문을 충분히 구현하고 있는지를 평가하며, [효율성] 테스트는 코드의 시간복잡도(코드가 문제를 해결하는데 걸린 시간이 충분히 빠른지)를 테스트합니다.

효율성은 시간복잡도를 본다는 것이었다.

#### 위의 코드들은 무엇이 문제 였나?
replace를 사용할 경우 모든 문자를 탐색 해야되기 때문에 시간 복잡도는 O(n) 이라고 한다. (내부에서 반복문을 사용할 것으로 추측)\
위 코드들은 replace가 for문에서 사용되어지므로 시간 복잡도는 더 커진다.\
for문에서 사용된 indexOf나 splice도 마찬가지 일 듯 하다.

그러므로 다중반복문을 피하는 코드를 작성해야 된다.

#### 효율성까지 통과한 코드
```javascript
function solution(participant, completion) {
    const a = {};

    for (let name of completion) {
        a[name] = (a[name] ? a[name] : 0) + 1;
    }

    for (let name of participant) {
        if ( !a[name] || a[name] == -1) {
            return name;
        } else {
            a[name]--;
        }
    }
}
```