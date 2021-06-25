## [React]  클래스형 컴포넌트 VS 함수형 컴포넌트

출처 : https://devowen.com/298


리액트를 사용하여 프로트 개발을 할때 두 가지 방법으로 컴포넌트를 선언할 수가 있다.

과거: 클래스형 컴포넌트
현재: 함수형 컴포넌트와 훅 ( React hook )을 지원


컴포넌트는 단순한 템플릿 이상의 기능을 수행한다.
**
데이터가 주어졌을 때 이에 맞추어 UI를 만들어 주는 기능을 하는 것은 물론,
라이프 사이클 API를 통해 컴포넌트가 화면에 나타날 때, 사라질 때, 변할 때 작업들을
수행할 수도 있다.
**

클래스형 컴포넌트
```
import React, { Component } from 'react';

class App extends Component {
  render(){
    const name = '리액트';
    return <div>{name}</div>;
  }
}

export default APP
```


함수형 컴포넌트
```
import React from 'react';

function App(){
  const name = '리액트';
  return <div>{name}</div>;
}
```


