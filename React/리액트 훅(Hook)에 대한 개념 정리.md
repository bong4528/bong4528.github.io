## [React]리액트 훅(Hook)에 대한 개념 정리

출처 : https://devowen.com/312?category=778540

함수형 컴포넌트에서 기존에 라이프사이클 메서드가 없어서 사용할 수 없었던 기능들을 사용할 수 있게 만들어 주었다.


### 목적
**컴포넌트에서 상태관련 로직을 사용할 때 레이어 변화 없이 재사용할 수 있게 하기 위함**
**기존 라이프 사이클 메서드 기반이 아닌 로직 기반으로 나눌 수 있어서 컴포넌트 함수 단위로
잘게 쪼갤 수 있다는 있점.**


### useState
userState는 가장 기본적인 Hook이며, 함수형 컴포넌트에서 가변적인 상태를 지닐 수 있게 해 준다. 
함수형 컴포넌트에서 상태를 관리해야 할 때 사용한다.

**const[count, setCount] = useState(0);
: useState 함수를 호출하면 배열을 반환하는데,
1번째 원소 count 는 현재 상태값 변수, 2번째 원소 setCount는 상태값을 갱신해 주는Setter 함수
useState 괄호 안의 값은 상태의 초기값 이다.
const [상태 값 저장변수, 상태 값 갱신 함수] = useState(상태 초기값);**
출처 : https://xiubindev.tistory.com/97


```
import React, { useState } from 'react';

function Example() {
  // 새로운 state 변수를 선언하고, count라 부르겠습니다.
  // count의 초기값은 0으로 지정합니다.
  const [count, setCount] = useState(0);
  
  return (
    <div>
      <p>You clicked {count} times </p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
  
}
```

state 는 원시타입 뿐만 아니라 객레로 사용할 수도 있다. 여러개의 useState를 사용할 수도 있지만, 이와 같이 하나의 state 에
여러 프로퍼티를 추가해서 두 가지 이상의 상태를 관리할 수도 있다.
```
import React, { useState } from "react";
import "./styles.css";

export default function App(){
  const [state, setState] = useState( {
    name: "John",
    id: 0
  });
  
  return (
  <div classname = "App">
    <h3>name : {state.name}</h3>
    <he>id: {state.id} </h3>
    <button onClick={() => setState( {...state, id: state.id + 1} )}>
      increase
    </button>
  </div>
  );
}
```


