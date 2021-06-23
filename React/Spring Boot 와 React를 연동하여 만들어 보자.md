## React 와 SpringBoot 를 연동하여 개발환경 세팅하기

출처 : https://sundries-in-myidea.tistory.com/71

### 1.Spring Boot 기본 설정하기

https://start.spring.io/ 에서 설정해서 다운로드



### 2. 스프링으로 간단한 Rest API 서버 만들기

@RestController



### 3. React 설치

### npx create-react-app fronted : 디렉토리 또는 서비스
### cd fronted
### npm start



### 4. 리액트와 스프링부트의 CORS 문제 해결하기

스프링부트의 백엔드 서버는 localhost:8080 에서 실행되고 있고, React 프론트엔드 서버는
localhost:3000 번으로 실행된다. 그래서 **CORS (cross-origin requests)** 가 발생한다.
그럴때 **Proxy 를 프론트에서 잡아 줘야 한다.** 

**Package.json**  파일에
```
{
"name": "frontend",
"version": "0.1.0",
"private": true,
"dependencies": {
"react": "^16.12.0",
"react-dom": "^16.12.0",
"react-scripts": "^3.3.0"
},
"scripts": {
"start": "react-scripts start",
"build": "react-scripts build",
"test": "react-scripts test --env=jsdom",
"eject": "react-scripts eject"
},

"proxy": "http://localhost:8080", -- 추가


"browserslist": {
"production": [
">0.2%",
"not dead",
"not op_mini all"
],
"development": [
"last 1 chrome version",
"last 1 firefox version",
"last 1 safari version"
]
}
}
```

**curl http://localhost:3000/api/hello** 테스트 하면 확인가능


### 5. React 의 App.js 를 변경해서 Rest API 의 값을 받고 출력해내기

```
import React, {useState, useEffect} from 'react';  --추가
import logo from './logo.svg';
import './App.css';

-- 추가
function App () {
const [message, setMessage] = useState("");
useEffect(() => {
fetch('/api/hello')
.then(response => response.text())
.then(message => {
setMessage(message);
});
},[])

return (
<div className="App">
<header className="App-header">
<img src={logo} className="App-logo" alt="logo"/>
<h1 className="App-title">{message}</h1>  -- 추가
</header>
<p className="App-intro">
To get started, edit <code>src/App.js</code> and save to reload.
</p>
</div>
)
}
export default App;

```



