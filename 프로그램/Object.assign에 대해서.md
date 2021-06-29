### [JavaScript] Object.assign() 에 대한 이해 

출처 : https://engineer-mole.tistory.com/151

Object.assign을 이용해서 객체를 합치는 것이 가능하다. 또한 합칠 때는 2개의 객체가 같은 프로퍼티를 가지고 있다면
그 값을 덮어쓰기 해주며, 객체의 복제에서도 사용될 수 있다.

Object.assign는 폼(form)등에 빈번히 이용되므로 볼 수 있는 기회가 많아 어떻게 처리가 되는지
이해해둘 필요가 있다. 여기서는 Object.assign() 기본 조작과 폼의 값을 유지 예를 이용해 설명


### 1. 오브젝트를 합친다.
2개의 객체를 준비하여 Object.assign 으로 합치면 어떠한 결과가 나타나는지 확인하자.

const target = {a:1, b:2}
const source = {c:3, d:4}

const returnedTarget = Object.assign(target, source);

console.log(target);
console.log(source);
console.log(returnedTarget);

실행하면
**Object.assign()의 첫 번째 인수의 target은 source가 합쳐지지만, source의 내용은 변경되지 않는다.
Object.assign의 리턴값은 target 이라는 것을 알 수 있다.**


### 2. 같은 프로퍼티를 가지는 오브젝트를 합치는 경우

### 3. 오브젝트 배열 요소를 갱신

### 4. Object의 복사 (클론)
**Object.assign은 객체의 복사에도 빈번히 사용된다.**
```
let user = {firstName: 'John', lastName:'Doe'};
let user_clone = Object.assign( {}, user );
```

### 5. 인수가 여러 개인 경우

### 6. Object.assign을 사용한 예 (form)
어떨 때 Object.assign를 사용하면 좋을까라는 의문이 있을 것이라고 생각되므로 입력 폼의 값을
유지하는 form 객체를 사용하여 설명하도록 하겠다.

```
const form = {
  firstName: null,
  lastName: null
}
```
입력 폼에 값이 들어어고 이를 input 객체로 받는다.

```
const input = {
  firstName: 'John Doe'
}
```
form 객체를 input 객체로 덮어쓰는 경우에 Object.assign 을 이용하면 아래와 같이 firstName의 값이 덮어쓰어진
것을 알수 있다.
```
Object.assign(form, input)
// 결과
{ firstName: 'John Doe', lastName: null }
```
