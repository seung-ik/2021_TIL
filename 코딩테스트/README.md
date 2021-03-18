### 03/18(목)

##### 서울에서 김서방 찾기(프로그래머스 1단계)

- 어렵진 않은데 오랜만에 풀어서 그런지 어색했다.

* (indexOf ,templete literal , O(n))

##### 같은 숫자는 싫어(프로그래머스 1단계)

- 처음에 reduce 썻다가 중복이 아니라 이전이랑 중복된거만 찾는 문제여서 filter 쓰려고 했는데 두번째 인자가 있다는 사실을 망각하고 for문으로 풀었다.

* (filter,for,reduce,O(n))

### 03/19(금)

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
