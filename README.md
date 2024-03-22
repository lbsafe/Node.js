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
