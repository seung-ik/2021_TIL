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
