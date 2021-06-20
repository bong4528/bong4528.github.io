## **rest의 representation이란 무엇인가**
출처: https://blog.npcode.com/2017/04/03/rest%EC%9D%98-representation%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80/


클라이언트에서 서버에 요청
서버에서 hello 를 보내서 클라이언트 받음.
representation 은 선택된의 뜻.
State          :  웹 애플리케이션의 상태
Transfer       :  전송


여기서 hello 는 서버의 리소스가 아니다.
그럼? **representation data**


API 서비스를 만들어 낼때 RESTFUl 하다는 의미는 무엇인가?

**Endpoint**
메소드는 같은 URL들에 대해서 다른 요청을 하게끔 구별하는 항목
GET,POST,DELETE 등 동일한 URL에서 다른 결과를 가져옴.


REST Ful 하다의 의미
**API의 엔드포인트가 하나** 이고,
요청과 응답에 대한 **메타데이터는 HTTP 프로토콜을 사용해서 전달** 해야하며,
요청메서드는 **POST(CREATE), GET(READ), PUT(UPDATE), DELETE(DELETE)** 를 사용하고,
요청 **URL에는 동사를 사용하지 않아야** 한다.










