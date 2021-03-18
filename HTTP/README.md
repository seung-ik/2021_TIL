[cors](#cors)

# cors

> same-origin origin
>
> - 불러온 문서나 스크립트가 다른 출처에서 가져온것이라면 이는 잠재적인 악성 문서이거나 공격 경로일수 있기 때문에 기본적으로 같은 출처가 아니라면 접근이 허용되지 않는데 이를 Cors-origin-Resource-Sharing 라고한다.

#### 해결방법은 어떤것들이 있나요???

### 1. 서버측에서 Access-Control-Allow-Origin response 헤더를 추가

```
app.get('/corstest',(req,res)=>{
  let data = ...
  res.header("Access-Control-Allow-Origin","http://localhost:3000")
  res.send(data)
})
```

### 2. Cors 미들웨어 사용
