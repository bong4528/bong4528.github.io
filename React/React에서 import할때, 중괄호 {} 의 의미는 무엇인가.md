## [React] React에서 import할때, 중괄호 {} 의 의미는 무엇인가??

출처: https://codingmania.tistory.com/333 [개발자의 개발 블로그]



**default import : 어떤 것은 그냥 import 하고,**

**member import (named import) : 어떤 것은 중괄호 {} 안에 변수를 적어 준다는 것이다.**

무슨 차이가 있는지 검색해 봤다.

만약, 아래과 같은 코드가 있다고 해보자

```
import React from 'react';
import { render } from 'react-dom';
```

이 파일은 이제부터 React 와 render 라는 변수를 사용할 수 있다.

React 변수는 react 패키지에서 불러왔고,
render 변수는 react-dom 이라는 패키지에서 불러왔다.

그런데,
첫 번째는 그냥 React 인데, 두 번째는 { render } 처럼 괄호 안에 감싸져 있다.

**차이점은 보내주는 export 방식의 차이였다.**

모듈을 불러올 때 import 라고 써주는 것처럼,
모듈을 다른 파일로 보내려면 export 라고 명시적으로 써줘야 한다.

예를 들어보면,
App.js 에서 다음과 같이 선언한다.

```
const a = 1;
const b = 2;

export { a };
export default b;
export const c = 3;

```
위와 같이 App.js 에서 세 가지 방식으로 export를 했다.

변수 a는 객체에 담아서 export 하고, 
변수 b는 독특하게 앞에 default 라는 키워드를 붙인 채 export 했다.
변수 c 는 선언 및 초기화와 동시에 바로 export 했다.


또 다른 함수 Sub.js 에서 App.js 에서 export 한 것들을 불러오려고 한다.
```
import b, {a, c as e } from './App';
console.log(a, b, e); // 1,2,3
```
와 같이 작성한다.

(해석)
App.js 에서 export 한 값들을 불러오려면,
Sub.js 에서는 코드 윗쪽에 import 를 선언하면 된다.



