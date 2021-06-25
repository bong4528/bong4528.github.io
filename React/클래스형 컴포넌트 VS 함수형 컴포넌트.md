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


함수형 컴포넌트를 선언할 때사용하는 방법으로 기존의 일반적인 함수 선언 방식이 있고, ES6의 화살표 함수(arrow function)방식도
있다. 화살표 함수의 경우 함수를 파라미터로 전달할 때 유용하다. 비슷한 점도 많지만, 두 문법이 확실하게 다르다는 점은 다음 예제를
통해서 알 수가 있다.

```
function Dog(){
  this.name = '흰둥이';
  return {
    name : '검둥이',
    bark: function(){
      console.log(this.name + ': 멍멍!');
    }
  }
}

const dog = new Dog();
dog.bark();   // 검둥이: 멍멍!
```

```
function Dog(){
  this.name = '흰둥이';
  return {
    name : '검둥이',
    bark: () => {
      console.log(this.name + ': 멍멍!');
    }
  }
}

const dog = new Dog();
dog.bark();   // 흰둥이: 멍멍!
```

**function()을 사용하면 검둥이**
**() =>{} 를 사용하면 흰둥이**
### 일반 함수는 자신이 종속된 객체를 this 로 가리키며, 화살표 함수는 자신이 종속된 인스턴스를 가리킨다.



props 는 프로퍼티(properties)를 줄인 표현으로 컴포넌트 속성을 설정할 때 사용하는 표현이다. props 값은 해당 컴포넌트를 불러와 
사용하는 부모 컴포넌트에서 설정할 수 있다. 그리고 경우에 따라서 propTypes 컴포넌트 속성을 통해  props의 타입을 지정해 줄 수 있다.
타입스크립트를 사용하다면 굳이 propTypes 를 사용하지 않아도 타입 체크를 할 수가 있다. 클래스형 컴포넌트의 경우 render 함수에서
this.props 를 조회해서 사용할 수 있다.

App.js
```
import React from 'react';
import MyComponent from './MyComponent';

const App = () => {
  return <MyComponent name="리액트"></MyComponent>;
}

export default App;
```

MyComponent.js
```
import React from 'react';
import PropTypes from 'prop-types';

const MyComponent = ({name} => {
  return (
    <div>제 이름은 {name}입니다.</div>
  );
};
```

**MyComponent.propTypes = {
  name: PropTypes.string
};**

```
export default MyComponent;
```




state는 컴포넌트 내부에서 바뀔 수 있는 값을 의미한다. props 의 경우 부모 컴포넌트가 설정해서 자식 컴포넌트는 읽기만 할 수 있는값
이며 바꾸기 위해서는 부모 컴포넌트에서 직접 변경을 해야 한다. 자식 컴포넌트 내에서 값을 변화하여야 하는 경우 state를 사용한다.

클래스형 컴포넌트에서는 클래스 내의 constructor 메소드에서 state의 초기값을 생성해 주어야 한다. 그리고 constructor를 작성할 때
super(props)를 반드시 호출해 주어야 한다. state를 조회할 때는 this.state로 조회하며, state의 값을 변경하고 싶을 때는 this.setState 
함수를 통해서 바꾸어 준다. 예제 코드는 다음과 같다.

```
import React, {Component } from 'react';

class Counter extends Component {
  constructor(props) {
    super(props);
    this.state = {
      number: 0
    };
  }
  
  render(){
    const { number } = this.state; // state 를 조회할 때에는 this.state 로 조회합니다.
    
  }
}
```


