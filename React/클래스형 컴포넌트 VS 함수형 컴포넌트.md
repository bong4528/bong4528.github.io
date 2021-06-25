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

클래스형 컴포넌트와 함수형 컴포넌트의 역할은 동일하다. 
차이점이 있다면 **클래스형 컴포넌트의 경우 state** 기능 및 라이프 사이클 기능을 사용할 수 있다.
그리고 render 함수가 꼭 있어야 하고, 그 안에서 보여 주어야 할 JSX를 반환해야 한다.
또한 과거의 prototype 을 이용해서 구현하던 문법을 ES6 문법 부터는 class 문법을 사용하여 구현할 수도 있다.


클래스 컴포넌트
```
class Dog{
  constructor(name){
    this.name = name;
  }
  
  say(){
    console.log(this.name + ': 멍멍');
  }
}

const dog = new Dog('강아지');
dog.say();  // 강아지
```

**함수형 컴포넌트 : 과거에는 state 와 라이프 사이클 API를 사용할 수 없다는 단점
지금은 리액트 훅으로 다 한다. HOW ?**






