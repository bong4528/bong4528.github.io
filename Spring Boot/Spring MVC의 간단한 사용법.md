## Spring MVC의 간단한 사용법

### URL 매핑

```
@RestController
@RequestMapping("/hello")
public class HelloController {

    @RequestMapping(method=RequestMethod.GET)
    public String getMethod() {
        return "get";
    }

    @RequestMapping(method=RequestMethod.POST)
    public String postMethod1() {
        return "post";
    }

    @RequestMapping(value="/hey", method=RequestMethod.POST)
    public String postMethod2() {
        return "hey post";
    }
}
```

- @RequestMapping 메서드 (클래스)와 경로를 매핑한다.
- value 속성에 경로를 지정한다.
- method 속성에 HTTP 메소드를 지정한다.


### 경로변수(@PathVariable)값 얻기

```
@RestController
@RequestMapping("/hello")
public class HelloController {

    @RequestMapping(value="/{id}/{name}", method=RequestMethod.GET)
    public void getMethod(@PathVariable int id, @PathVariable String name) {
        System.out.println("id=" + id + ", name=" + name);
    }
}
```

- 경로의 정의에 중괄호 ( {} ) 로 묶은 매개 변수를 정의한다.
- 메소드의 매개 변수로 같은 이름의 인수를 정의한다.
- @PathVariable 어노테이션이 부여한다.

### 쿼리 파라미터(@RequestParam)값 얻기

### 요청 헤더(@RequestHeader)값 얻기

### 요청 바디(@RequestBody)값 얻기

### 응답 상태 코드(@ResponseStatus)값 지정하기

### 여러가지 응답의 반환방법
