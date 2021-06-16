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

```
@RestController
@RequestMapping("/hello")
public class HelloController {

    @RequestMapping(method=RequestMethod.GET)
    public void getMethod(
            @RequestParam String id,
            @RequestParam Map<String, String> queryParameters,
            @RequestParam MultiValueMap<String, String> multiMap) {

        System.out.println("id=" + id);
        System.out.println(queryParameters);
        System.out.println(multiMap);
    }
}
```

- 메소드의 인수에 @RequestParam 어노테이션를 부여하면 쿼리 매개 변수를 얻을 수 있다.
- 인수의 형태가 Map 이라면 쿼리 파라미터 정보를 Map 형태로 얻을 수 있다.
- 하나의 매개 변수의 여러 값이 설정되어있는 경우, Spring에서 제공하는 MultiValueMap 로
  받을 수 있다.


### 요청 헤더(@RequestHeader)값 얻기

```
@RestController
@RequestMapping("/hello")
public class HelloController {

    @RequestMapping(method=RequestMethod.GET)
    public void getMethod(@RequestHeader("Test-Header") String value) {
        System.out.println("Test-Header=" + value);
    }
}
```

- @RequestHeader 로 헤더 정보를 얻을 수 있다.


### 요청 바디(@RequestBody)값 얻기

```
@RestController
@RequestMapping("/hello")
public class HelloController {

    @RequestMapping(method=RequestMethod.POST)
    public void getMethod(@RequestBody String body) {
        System.out.println("body=" + body);
    }
}
```

- @RequestBody 에서 요청 바디를 얻을 수 있다.


### 응답 상태 코드(@ResponseStatus)값 지정하기

```
@RestController
@RequestMapping("/hello")
public class HelloController {

    @RequestMapping(method=RequestMethod.GET)
    @ResponseStatus(HttpStatus.BAD_REQUEST)
    public void getMethod() {
    }
}
```

- 메소드를 @ResponseStatus 에 어노테이션을 부여하고 value 에 상태 코드를 지정하면,
  그 응답의 상태 코드를 지정할 수 있다.
- 아무것도 지정하지 않으면 200 OK 가 반환된다.


### 여러가지 응답의 반환방법

Spring MVC의 컨트롤러 메소드에서 사용할 수 있는 반환 값에 어떤 것이 있는지, 
어떤 방법이 있는지 대해 설명한다.

#### @Controller 와 @RestController 의 차이
 
@Controller 는 주로 Web 페이지의 컨트롤러에서 사용한다.
Web 페이지용 컨트롤로는 JSP 나 템플릿 엔진 View 로 전환 응답의 HTML 을 생성하기 때문에
기본적으로 메소드의 반환 값은 View 전환 대상을 지정하는 데 사용한다.
 
@RestController 는 Json 이나 XML 등을 반환 WebAPI용 컨트롤러로 사용한다.
이것은 View로 전환하지 않기 때문에 메소드의 반환 값은 응답 (Response)의 내용(content)이 된다.

#### @Controller
##### 반환 값을 String 으로 한다.

View 이동 페이지를 지정하는 가장 간단한 방법이다.
```
@RequestMapping("/method1")
public String method1() {
    return "/index.html";
}
```

##### 반환 값을 ModelAndView 으로 한다.

ModelAndView를 사용하면 View로 전달하려는 정보를 함께 반환할 수 있다.
```
@RequestMapping("/method2")
public ModelAndView method2() {
    ModelAndView modelAndView = new ModelAndView();
    modelAndView.addObject(new User("kimkc"));
    modelAndView.setViewName("/index.html");
    return modelAndView;
}
```

##### 포워드

반환 값으로 지정하여 이동처로 "forward:"를 붙이면 다른 컨트롤러 메소드로 이동한다.
```
@RequestMapping("/forward1")
public String forward1() {
    return "forward:method1";
}
```

