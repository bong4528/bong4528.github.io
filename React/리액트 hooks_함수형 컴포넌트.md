## 리액트 hooks: 함수형 컴포넌트 

출처 : https://velog.io/@_jouz_ryul/-%EB%A6%AC%EC%95%A1%ED%8A%B8-hooks-%ED%95%A8%EC%88%98%ED%98%95-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8

1. 리액트 hooks 기초

1.1 리액트 훅이란?
클래스형 컴포넌트의 기능을 사용할 수 있는 함수형 컴포넌트라고 볼 수 있다.
life-cycle 과  state 관리 모두 가능하다.

1.1.1 훅의 장점
재사용 가능한 로직의 관리가 쉽다.

1.2 use state: 함수형 컴포넌트에 상태값 추가하기
useStae 훅을 이용하면 함수형 컴포넌트에서도 상태값을 관리할 수 있다.

```
import React, {useState} from 'react';

function Profile(){
  const [name, setName] = useState('');
  return(
    <div>
    </div>
  )
}

```
