## 리액트 hooks: 함수형 컴포넌트 

출처 : https://velog.io/@_jouz_ryul/-%EB%A6%AC%EC%95%A1%ED%8A%B8-hooks-%ED%95%A8%EC%88%98%ED%98%95-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8

1. 리액트 hooks 기초

### 1.1 리액트 훅이란?
클래스형 컴포넌트의 기능을 사용할 수 있는 함수형 컴포넌트라고 볼 수 있다.
life-cycle 과  state 관리 모두 가능하다.

**1.1.1 훅의 장점**
재사용 가능한 로직의 관리가 쉽다.

**1.2 use state: 함수형 컴포넌트에 상태값 추가하기**
useStae 훅을 이용하면 함수형 컴포넌트에서도 상태값을 관리할 수 있다.
```
import React, {useState} from 'react';

function Profile(){
  const [name, setName] = useState('');
  return (
    <div>
      <p>{`name is ${name}`}</p>
      <input type='text' value={name} onChange= { e => setName(e.target.value) } />
    </div>
  );
}
```

`useState` 훅은 배열에 두 값을 넣어서 반환한다.
배열의 
첫 번째 원소는 상태값 즉 `state` 인데 함수 호출 시 입력한 인수가 초기값으로 사용된다.
두 번째 원소는 상태값을 변경할 수 있는 함수이다.
**배열의 비구조화 할당 문법** 을 이용해서 각 원소에 이르을 부여한다. 이처럼 `useStae` 훅을
통해서 함수형 컴포넌트에서도 상태값을 사용할 수 있다.

1.2.1 여러 상태값 하나로 관리하기

`useState` 훅 하나로 여러 상태값을 하나의 객체에 담아서 관리할 수 있다.

```
import React, {useState} from 'react';

function profile(){
  const [state, setState] = useState({ name: "", age: 0});
  return (
    <div>
    </div>
  )
}
```

두 개의 상태값을 하나의 객체로 관리한다.
기존 클래스형 컴포넌트에서의 setState 메소드는 기존 상태값과 입력된 값을 병합하지만 `useState` 훅은 이전 상태값을 지운다.
따라서 `...state` 와 같은 코드가 필요한 것이다.
더 나아가 하나의 객체로 상태값을 관리할 때 `useReducer` 훅이 제공된다.


### 1.3 Life-cycle 함수 사용하기 : useEffect
`useEffect` 훅을 사용하여 함수형 컴포넌트에서도 life-cycle 함수를 이용할 수 있다.
클래스형 컴포넌트에서의 각각 생명주기 메소드에 대응하는 훅이 존재하는 것은 아니지만.
`useEffect` 훅을 이용하면 비슷한 기능을 한 곳으로 모을 수 있어서 가독성이 좋아진다.

```
import React, {useState, useEffect } from 'react';

function MyComponent(){
 const [count, setCount ] = useState(0);
 useEffect( () => {
   document.title = `업데이트 횟수: ${count}`;
 });
 return <button onClick= { () => setCount( count + 1) } > 증가 </button>
}
```

1.3.1 API를 호출하는 기능 : 함수형 컴포넌트에서

1.3.2 API를 호출하는 기능: 클래스형 컴포넌트에서

1.3.3 이벤트 처리 함수 등록 및 해제: 함수형 컴포넌트로 작성하기

1.3.4 두 기능을 한 컴포넌트에서 작성하기: 함수형 컴포넌트로


### 1.4 리액트 내장 훅: useCallback & useReducer

1.4.1 useCallback

1.4.2 useReducer: 상태값을 리덕스처럼 관리하기

