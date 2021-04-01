[nodejs장점](#장점)

# 장점

- script 태그를 사용하여 외부의 스크립트 파일을 가져올 수는 있지만 파일마다 독립적인 파일 Scope를 갖지 않고 하나의 전역 객체(Global Object)에 바인딩되기 때문에 전역변수가 중복되는 등의 문제가 발생할 수 있다. 이것으로는 모듈화를 구현할 수 없다.

# callback

- 값이 반환될 때까지 기다리지 않고 그 다음 코드를 실행하려면 비동기 방식으로 코드를 만들어야 하는데 그대 사용 되는 방식 이다
- 함수 를 인자로 받아 함수내부에서 실행하는 형태이다.

# callback hell

- 콜백함수가 중첩되서 실행되면 가독성이 떨어진다.
- 프라미스 객체르 이용하거나 async&await 문법을 사용해 일부 해결할수있다.
- 기능별로 함수를 정의 하여 함수끼리 연결을 시키는 것입니다.

# 이벤트루프

1. fs.readFile 라는 블로킹작업을 만난 시점에 이벤트루프는 워커쓰레드에게 작업을 넘김
2. 워크쓰레드가 작업을 완료한 뒤 I/O callbacks 영역의 큐에 콜백을 등록
3. 이벤트루프가 I/O callbacks 영역을 실행할 때, 콜백을 poll 영역의 큐에 등록
4. 이벤트루프가 poll 영역을 실행할 때, 큐에 1개가 있으므로 이걸 실행함.
5. (콜백내부) 2라인에서 setTimeout() 이므로 다시 timers 영역에 넣고 5라인으로 간다.
6. (콜백내부) 5라인에서 setImmediate() 이므로 check 영역에 넣는다.
7. 이벤트루프가 poll 큐를 비우고, 다음 실행영역인 check 영역으로 간다. check 영역의 큐에는 들어있는 'B'를 콘솔에 찍는다. check 영역의 큐를 비우고 다시 while문의 시작지점으로 간다.
8. 이벤트루프가 timers 영역을 호출한다. uv\_\_run_timers()는 setTimeout()의 콜백을 poll큐에 등록한다.
9. 이벤트루프가 2번째로 poll 영역을 실행한다. 큐에 1개가 있으므로 이걸 실행하고 'A'를 찍는다.
   node 프로세스가 반환되고 끝

출처: https://sjh836.tistory.com/149
https://nodejs.org/ko/docs/guides/blocking-vs-non-blocking/

# nodejs 브라우저의 차이점

- https://oneroomtable.tistory.com/entry/Nodejs%EC%99%80-%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90-%EB%B2%88%EC%97%AD
  https://blog.insiderattack.net/javascript-event-loop-vs-node-js-event-loop-aea2b1b85f5c

# package.json

프로젝트의 루트폴터에 존재하면서 프로젝의 이름과 버젼 그리고 사용한 각종 모듈들의 의존성 에 대한 정보들을 담고있는 파일이다.
script 를 통해 npm 명령어를 지정할수도 있으며
프로젝트를 진행하면서 여러가지 패키지들을 사용(의존)하게 되는데요. 패키지들의 버전이 빠르게 변하다보니 관리하기가 힘든 경우가 많습니다. package.json은 의존중인 패키지들의 버전을 기록해줍니다. 세 가지 종류로 기록을 해 주는데 바로 dependencies, devDependencies, peerDependencies입니다.

dependencies는 일반적인 경우 의존하고 있다는 것을 알려주는 곳이고, devDependencies는 개발 모드일 때만 의존하고 있다는 것을 알려주는 겁니다. devDependencies는 실제로 배포할 때는 필요없는 테스트 도구나 웹팩, 바벨같은 것들을 넣어두면 됩니다.

peerDependencies가 문젠데요. 직접 require은 하지 않지만 호환되는 패키지의 목록입니다. 주로 자기가 어떤 패키지의 플러그인 같은 개발할 때 사용합니다. 제가 만든 react-vote, react-filepicker같은 것은 모두 peerDependencies로 react@15.3.x를 두고 있습니다.

package-lock.json 파일은 의존성 트리에 대한 정보를 모두 가지고 있습니다.
package-lock.json 파일은 저장소에 꼭 같이 커밋해야 합니다.
package-lock.json 파일은 node_modules 없이 배포하는 경우 반드시 필요합니다.

https://docs.npmjs.com/cli/v7/configuring-npm/package-json
