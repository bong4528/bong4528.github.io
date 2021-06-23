## React 와 Node.js 의 관계는 쫌 건너건너 에요.
출처 : https://velog.io/@eungook/React%EC%99%80-Node.js%EC%9D%98-%EA%B4%80%EA%B3%84%EB%8A%94-%EC%AB%8C-%EA%B1%B4%EB%84%88%EA%B1%B4%EB%84%88%EC%97%90%EC%9A%94

### 1줄 요약 : React 개발에는 Node.js 와 관련 툴들이 필요합니다.


### 1. 사실 React 는  jQuery랑 더 닮았답니다

React  : A JavaScript library for building **user interfaces**

jQuery : It makes things like **HTML document** traversal and(...) much simpler with an
         easy-to-use API

Node.js : is a **JavaScript runtimer** built on Chrome's V8 Javascript engine.


그쵸? Node.js 는 자바스크립트 런타임일 뿐, 결코 UI 혹은 HTML 을 표현하지는 않습니다.

React는 가상 DOM 을 통해 UI 를 만드는 라이브러리이고, 
JQuery 는 다 아시죠? ^^
그래서 이 둘이 더 닮았다고 할 수 있겠습니다.


### 아니 암튼! 그래서 Node.js 와 React 의 관계는요!

## 2. Node.js 와 React 사이에는 webpack 과 babel 이 있습니다.

webpack : is a **static module bundler** for modern JavaScript applications.
Babel: is a toolchain that is used to convert ES6+ code into a **backwards compatible version of JavaScript**

이것이 무슨 말인고 하니..
React 를 통한 **대규모 SPA 개발** 을 위해서는

1. 몹시 많은 정적 파일이 필요하고, (.js, .css, .png 등) 이를 번들링할 필요가 있습니다.
   => webpack 을 사용합니다
2. ES6를 해석할 수 없는 IE11 등 비 모던 웹 브라우저에 대한 지원이 필요합니다.

그래서 React 와 Node.js 의 관게는 **쫌 건너건너** 라고 할 수 있죠!


### 3. 그럼 Node.js 는 무엇인가요?

Node.js는 자바스크립트 런타임 입니다. 그리고 어떤 라이브러리를 갖고 있습니다.
웹브라우저에서 Javascript 가 해석되면, **Web API** 를 통해서 웹브라우저에서 결과가 나타납니다.
Node.js 에서 JavaScript 가 해석되면, **libuv** 를 통해서 OS에서 결과가 나타납니다.

web api : https://developer.mozilla.org/ko/docs/Web/API
libuv   : https://sjh836.tistory.com/149

그래서 Node.js 를 통해 webpack 과  Babel 을 사용하면 ( 이 과정을 보통 **빌드** 한다고 하죠. )
React 코드가 compatible version of JavaScript 로 바뀌고, 다시 **bundle** 되어 브라우저에 올리기만
하면 결과물이 나타납니다.


## 4. npm 과 create-react-app

그리고 사실 이게 제일 중요할지도 모르겠는 데요..;;
React의 **의존성 관리는 npm** 을 사용하는게 가장 일반적입니다.

그리고 React 의 부트스트랩인 **create-react-app** 을 사용하기 위해서
역시 Node.js 가 필요합니다.

여기까지 읽으셨다면
React 공식 홈페이지의 **새로운 React 앱 만들기** 도 읽어보세요.


