## DTO (Data Transfer Object)


개념

이름과 같이 계층 간 데이터 교환을 위해 사용하는 객체다.
여기서 말하는 계층이란, View - Controller - Service -DAO 와 같은 각 계층을 말한다.
VO 와 혼용되어 쓰이나, 이는 보통 DTO 를 지칭하는 말이다.
데이터를 담을 private 변수와 그 변수를 조작할 수 있는 Getter, Setter 메서드로 구성되어 있음.


`데이터를 오브젝트로 변환하는 객체 Getter, Setter 메서드로 구성`


### 사용 이유

form, ajax 에서 name 필드 값을 프로퍼티에 맞춰서 값을 다른 페이즈로 넘겼을 시,
값을 받아야 할 페이지에서는 값을 하나씩 일일이 받는 것이 아니라 name 속성의 이름이랑 매칭 되는
프로퍼티에 자동적으로 DTO가 인스턴스화 되어 UserDTO를 자료형으로 값을 받을 수 있음.

#### DB  : 데이터 줄게
#### DAO : 일일이 담기 귀찮다. 딱 맞는 바구니에 담을 수 없을까?
#### DAO : OK!  주는 데이터에 맞춰서 데이터 형식들을 만들어 놓을 클래스를 만들어야 겠다.
####       DTO 라고 부르자

### DB 값 -> DAO -> Service -> DTO



