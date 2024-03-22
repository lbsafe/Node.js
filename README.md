# Node.js

<p align="center"><img src="https://github.com/lbsafe/Node.js/assets/65703793/ee4e0aab-ce2a-4a10-a051-4316b754ec30" alt="node.js" width="200px"></p>

## Node.js 에 대하여

> Node.js는 웹 브라우저가 아닌 환경에서도 자바스크립트 코드를  
실행시켜주는 런타임(실행 환경)이다.
***

## Node.js 설치

**:one:** : :link:[Node.js][nodelink] 공식 사이트 (LTS 버전 사용하기)
    
[nodelink]: https://nodejs.org/en "Go node"

**:two:** : 터미널 확인 (Node.js 버전 확인)
```js
node -v
```

**:three:** : NPM(Node Package Manager) 설치 확인
```js
npm -v
```
***

## 패키지

> Node.js에서 사용하는 프로젝트의 단위이다.

**:one:** : 터미널 패키지 생성/초기화 명령어
```js
npm init
```

**:two:** : package.json 파일 정보 확인
```js
{
  "name": "section03", // 패키지 이름
  "version": "1.0.0", // 패기지 버전
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node src/index.js" // 매크로 설정
  },
  "author": "",
  "license": "ISC"
}
```

**:three:** : index.js 파일 생성 후 Node.js를 통한 실행
```js 
node index.js

// node 경로/실행할 파일명
node src/index.js

// 매크로 설정 시
npm run start
```
***

## 모듈 시스템

> 모듈을 생성하고, 불러오고, 사용하는 등의 모듈을 다루는 다양한 기능을 제공하는 시스템   
(모듈이란? 기능별로 나누어진 각각의 자바스크립트 파일이다.)

### Common JS (CJS)

> 모듈로부터 특정 값을 내보내고 또 다른 모듈에서 불러오는 방법

* **:one:** math.js 를 생성 후 **module.exports** 사용해 함수를 내보낸다.

    ```js
    // math 모듈

    const add =(a,b)=>{
        return a+b;
    }

    const sub =(a,b)=>{
        return a-b;
    }

    module.exports = {
        add,
        sub
    }
    ```

* **:two:** index.js 에서 **require** 사용해 모듈을 불러온다.

    ```js
    const {add, sub} = require("./math");

    console.log(add(1, 2));
    console.log(sub(1, 2));
    ```
***

### ES Module (ESM)

> CJS 보다 최신식으로 동작하는 모듈 시스템   
ESM 은 CJS 와 함께 사용하지 못한다.

* **:one:** package.json에 **"type": "module"** 추가하여 ES Module 시스템을 사용한다.

    ```js
    {
    "name": "section03",
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "start": "node src/index.js"
    },
    "author": "",
    "license": "ISC",
    "type": "module" // 추가
    }
    ```

* **:two:** **export{}** 로 내보내고 싶은 객체를 리터럴로 생성해서 담아준다.

    ```js
    // math 모듈

    const add =(a,b)=>{
        return a+b;
    }

    const sub =(a,b)=>{
        return a-b;
    }

    export {add, sub}; // 사용부분
    ```

* **:three:** **import{} from** 으로 가져오고자 하는 값과 모듈의 경로를 지정해준다.

    **:exclamation: 확장자 명시 필수**
    ```js
    import {add, sub} from "./math.js"; // 확장자 명시

    console.log(add(1, 2));
    console.log(sub(1, 2));
    ```

**:pushpin: 추가적인 기능/활용법**

- 함수 선언문 앞에 **export**를 붙여줘도 된다.

    ```js
    // Before
    export {add, sub};

    // After
    export const add =(a,b)=>{
        return a+b;
    }
    export const sub =(a,b)=>{
        return a-b;
    }
    ```

- 하나의 모듈을 대표하는 default 값을 내보내는 방법

    > default export 구문은 하나의 파일에 단 하나만 존재해야 하고, 이름 또한 원하는 이름으로 불러올 수 있기 때문에 default export 구문을 사용할 컴포넌트는 선언할 때 이름이 없어도 된다.

    **:one:** 대표값 설정

    ```js
    // 일반 함수
    export default function multiply(a,b){
        return a*b
    }

    // 화살표 함수
    const multiply =(a,b)=>{
        return a*b;
    }
    export default multiply; 
    ```

    **:two:** 대표값 불러오기

    * 대표값은 불러올때 중괄호 없이 불러온다.
    * 대표값을 불러올때의 이름은 마음대로 정의가 가능하다.    
    (하나의 모듈에 단 하나만 존재해서 가능)
    * 동일한 경로의 import는 합치는 것이 가능하다.
    
    ```js
    // Before
    import multiply from "./math.js";
    import {add, sub} from "./math.js";

    // After
    import mul, {add, sub} from "./math.js";
    
    console.log(mul(1, 2));
    ```
***