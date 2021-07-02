## [React] React에서 import할때, 중괄호 {} 의 의미는 무엇인가??

출처: https://codingmania.tistory.com/333 [개발자의 개발 블로그]



어떤 것은 그냥 import 하고,
어떤 것은 중괄호 {} 안에 변수를 적어 준다는 것이다.

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
