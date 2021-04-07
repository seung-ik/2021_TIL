# Greedy(탐욕법)

#### 대표예제

- 동전지불 문제 462 원을 100원 짜리 10원짜리 1원 짜리로 가장 적은수의 동전으로 지불하는 방법
- 개념 : 매순간 최선으로 보이는 선택을 하는 경우가 전체적으로 봤을때도 최선인 경우 사용한다.
- 체육복(프로그래머스 1단계)

# Stack 과 queue

### 인덱스 잘 활용해야됨

- stack 최근에 들어온 자료가 먼저 나간다.(ex . 급식실식판)
- queue 먼저 들어온 자료가 먼저 나간다.(ex . 급식실 줄서기)

# 여러가지 정렬

O(n²) : Bubble Sort, Selection Sort, Insertion Sort, Shell Sort, Quick Sort
O(n log n) : Heap Sort, Merge Sort
O(kn) : Radix Sort (k는 자릿수, 자릿수가 적은 4바이트 정수에서나 제대로 된 성능을 낼 수 있다는 제약조건이 있다.)

### 퀵정렬

- 분할정복법을 이용한 정렬법으로 이해하기 쉬우며 일반적인 경우에는 성능도 좋은편에 속한다.
- 다만 나누는 기준값(pivot) 값이 최대값이나 최소값으로 정해지는 경우 성능이 떨어진다.>(처음 중간 끝값의 평균을 pivot 으로 지정하면 문제해결 가능)

- https://medium.com/@joongwon/%EC%A0%95%EB%A0%AC-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EA%B8%B0%EC%B4%88-805391cb088e

### 순열과 멱집합의 차이

- 순열은 중복되지 않는 선택에서 할수 있는 모든 경우의 수를 뜻한다.
- 멱집합은 중복까지 고려해서 할수 있는 모든 경우의 수를 구할때 사용한다.
- 두개다 완전탐색 느낌이다.
- 구현에 있어서 순열은 재귀함수 안에서 포문을 돌리는데 포문안에서 방금 사용한거는 지워주는 작업을 하고 재귀함수를 호출해줘야하지만
  멱집함은 포문안에서 사용한것들은 따로 지워주지 않음으로써 사용가능핟.

### dfs 코드구현

```
let dfs= function(node){
  let result=[node.value]
  if(node.children){
    for(let i=0 ; node.children.length ; i++){
      result=result.concat(dfs(el))
    }
  }
  return result
}
```

더깊이 없으면 그냥 리턴하고 그거를 위에다가 합치는데 그게 재귀형식으로 먼저들어가니까
dfs 구조가 됨

### 멱집합 코드구현(가위바위보문제)

```
const rsc = (num)=>{
  let arr=[a,b,c,d]
  let result =[]

  let recurse=(round,inner)=>{
    if(round===0){
      result.push(arr)
      return
    }
    for(let i = 0 ; i<arr.length ; i++){
      recurse(round-1,inner.concat(arr[i]))
    }
  }
  recurse(num,[])
  return result
}
```

재귀를 쓰는형태들을 알고있어야되 이거는 내아이큐로는 새롭게 생각하기 가 쉽지않아 형태들에 익숙해져야되 재귀함수 만들어서 조건에 부합해나가도록 유도 그안에서 할일하고
저기서 포문 안에서 중복제거 할수 있는거도 있는데 그건 내일 정리하자
