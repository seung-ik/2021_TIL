### 03/17(수)

##### 서울에서 김서방 찾기(프로그래머스 1단계)

- 어렵진 않은데 오랜만에 풀어서 그런지 어색했다.

* (indexOf ,templete literal , O(n))

##### 같은 숫자는 싫어(프로그래머스 1단계)

- 처음에 reduce 썻다가 중복이 아니라 이전이랑 중복된거만 찾는 문제여서 filter 쓰려고 했는데 두번째 인자가 있다는 사실을 망각하고 for문으로 풀었다.

* (filter,for,reduce,O(n))

### 03/18(목)

##### 모의고사(프로그래머스 1단계)

- 내꺼보다 좋은코드 일부가 반복될때 비교하는 법 나는 일일이 만들어서 함. 푸쉬할때도 나는 객체로 만들어서 했는데 저런 방법도 있네

```
function solution(answers) {
    var answer = [];
    var a1 = [1, 2, 3, 4, 5];
    var a2 = [2, 1, 2, 3, 2, 4, 2, 5]
    var a3 = [ 3, 3, 1, 1, 2, 2, 4, 4, 5, 5];

    var a1c = answers.filter((a,i)=> a === a1[i%a1.length]).length;
    var a2c = answers.filter((a,i)=> a === a2[i%a2.length]).length;
    var a3c = answers.filter((a,i)=> a === a3[i%a3.length]).length;
    var max = Math.max(a1c,a2c,a3c);

    if (a1c === max) {answer.push(1)};
    if (a2c === max) {answer.push(2)};
    if (a3c === max) {answer.push(3)};


    return answer;
}
```

### 03/19(금)

##### 3진법(프로그래머스 1단계)

```
function solution(n) {
    const answer = [];
    while(n !== 0) {
        answer.unshift(n % 3);
        n = Math.floor(n/3);
    }
    return answer.reduce((acc,v,i) => acc + (v * Math.pow(3, i)),0);
}
```

```
const solution = (n) => {
    return parseInt([...n.toString(3)].reverse().join(""), 3);
}
```

##### k번째수(프로그래머스 1단계)

- compareFunction이 제공되지 않으면 요소를 문자열로 변환하고 유니 코드 코드 포인트 순서로 문자열을 비교하여 정렬됩니다. 예를 들어 "바나나"는 "체리"앞에옵니다. 숫자 정렬에서는 9가 80보다 앞에 오지만 숫자는 문자열로 변환되기 때문에 "80"은 유니 코드 순서에서 "9"앞에옵니다.

- 이중배열에서 구조분해할당

##### 두정수 사이의 합 (프로그래머스 1단계)

- 간단한 조건의 삼항연산자 사용
- 가우스의 재림

##### 콜라츠 추측 (프로그래머스 1단계)

```
function collatz(num,count = 0) {
    return num == 1 ? (count >= 500 ? -1 : count) : collatz(num % 2 == 0 ? num / 2 : num * 3 + 1,++count);
}
```

- 이걸 재귀함수로 푸네 대박

##### 소수찾기 (프로그래머스 1단계)(실패)

- Array.from({length:100},(v,i)=>i+1)
- 에라토스 체

##### 폰켓몬 (프로그래머스 1단계)

- let many= Object.keys(obj).length 객체의 길이구하기
- reduce 로 객체 만들기

```
 const check = nums.reduce((total,cur) => {
        total[cur] ? total[cur]++ : total[cur] = 1;
        return total;
    },{});
```

##### 2016년 (프로그래머스 1단계)

- 이상하게 푼거같은데?

### 03/19(금)

##### 평균 구하기(프로그래머스 1단계)

- reduce 로 평균구할수 있구나

##### 체육복 (프로그래머스 1단계)

- 탐욕법 에대해서 정리하기

##### 두개뽑아서 더하기 (프로그래머스 1단계)

- 배열에서 중복제거 하는 방법 (filter, reduce, new Set+...operator)

##### 신규 아이디 추천 (프로그래머스 1단계)

- 정규표현식 공부해보기

```
function solution(new_id) {
    const answer = new_id
        .toLowerCase() // 1
        .replace(/[^\w-_.]/g, '') // 2
        .replace(/\.+/g, '.') // 3
        .replace(/^\.|\.$/g, '') // 4
        .replace(/^$/, 'a') // 5
        .slice(0, 15).replace(/\.$/, ''); // 6
    const len = answer.length;
    return len > 2 ? answer : answer + answer.charAt(len - 1).repeat(3 - len);
}
```

##### 시저암호 (프로그래머스 1단계)

- 아스키 코드 안쓰고 푸는 방법
- 아스키 코드로 푸는 방법 => String.fromCharCode(31) , sentence.charCodeAt(index)

```
function solution(s, n) {
    var upper = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    var lower = "abcdefghijklmnopqrstuvwxyz";
    var answer= '';

    for(var i =0; i <s.length; i++){
        var text = s[i];
        if(text == ' ') {
            answer += ' ';
            continue;
        }
        var textArr = upper.includes(text) ? upper : lower;
        var index = textArr.indexOf(text)+n;
        if(index >= textArr.length) index -= textArr.length;
        answer += textArr[index];
    }
    return answer;
}
```

- 인덱스로 분리해서 생각하기 와 우 와 우 와 우

##### 비밀지도 (프로그래머스 1단계)

```
const addZero = (n, s) => {
    return '0'.repeat(n - s.length) + s;
}
```

- add 제로 다른 사람은 되게 간단하게 품(정규표현식 사용해서+)

### 03/21(일)

##### 문자열내 p와 y의 개수 (프로그래머스 1단계)

- 아 uppercase 해서 할수잇엇겟다.

##### 소수만들기 (프로그래머스 1단계)

- 멱집합으로도 해보기 멱집합에 대한개념 공부해야됨

### 03/22(월)

##### 예산(프로그래머스1단계)

- 아니 문제 진짜 그지 같네 sort() 랑 sort(func) 차이점 확실히 알아보기

##### 크레인 인형뽑기 (프로그래머스 1단계)

- 아 인덱스 생각좀 잘하자 ...
- 그뭐지 그 그 그 그 그 그 그 그 그 continue 랑 breack 개념이 아직 쫌 잘 안잡힌듯

##### 행렬의 덧셈 (프로그래머스 1단계)

- 2차원 배열 map 으로 풀기

##### 최대공약수와 최소공배수 (프로그래머스 1단계)

- 은근 어렵네 ㅋㅋ

##### 자연수 뒤집어 배열로 만들기 (프로그래머스 1단계)

- 숫자를 문자로 바꾸기 전에 10나누기로 풀수 있는 문제인가?

### 03/22(월)

###### 프린터

- 2단계 개업렫ㅂ다 그뭐지 그 그그그그그ㅡ그그그그그그그그그그그그그그그그그그그 큐 공부하자
