### login 페이지 만들기
출처 : https://ande226.tistory.com/101

1. RequestMapping 에 로그인 추가

WEB-INF/view/login/login.jsp 를 찾는다.
```
@Controller
public class IndexController{

  @RequestMapping("/login")
  public String login(){
    return "login/login";
  }

}
```

2. login 폴더 안에 login.jsp 만들기


### 데이터 보내기

1. ArticleController 클래스 만들기

```
@Controller
public class ArticleController{
  @RequestMapping("/list")
  public ModelAndView articleList(){
    ModelAndView view = new ModelAndView();
    view.setViewName("article/list");
    
    view.addObject("title", "제목");
    view.addObject("author", "글쓴이");
    
    return view;
  }
}
```

- ModelAndView : 데이터를 전송시킬 수 있는 리턴 타입 ( cf. String 타입은 단순하게 페이지만 열어주는 역할을 함. )

- 1. setViewName : 어떤 페이지를 보여줄 것인지
- 2. addObject : key 와 value 를 담아 보낼 수 있는 메서드


2. list.jsp 만들기

```
<body>
${title}
${author}
</body>
```


3. applicationContext.xml 에 내용 추가하기

```
<bean id="articleController"
      class="com.ktds.smahn.web.ArticleController" />
```

4. url 로 접속
   localhost:8080/HelloMVC/list
   

### RequestMapping_전송방식 지정하기
- method가 정의되지 않으면 어떤 방식으로든 접근할 수 있다.
- method가 정의되면 그 방식으로만 접근할 수 있다.

1. GET 방식 : url 로 접근
2. POST 방식 :  form 으로 접근

### @Requestmapping(value="/login", method=`{RequestMethod.GET, RequestMethod.POST}`)



### 파라미터 전송받기
@RequestMapping("/detail/`{author}`")
public ModelAndView detail(`@PathVariable String author`){
    ModelAndView view = new ModelAndView();
    
    return view;
}

- ?key=value 이런 식으로 할 필요없이, @PathVariable을 통해 url 자체에 파라미터를 넘길 수 있다.


### Pathvariable 로 url 파라미터 전송해 보기

1. articleController 에 추가
```
@RequestMapping("/detail/`{author}`")
public ModelAndView detail(`@PathVariable String author`){
    ModelAndView view = new ModelAndView();
    
    view.setViewName("article/detail");
    view.addObject("authorName", author);
    return view;
}
```

2.detail.jsp  추가
```
<body>
${authorName} 지은이 입니다.
</body>
```

3. url로 파라미터 전송
 localhost:/HelloMVC/detail/sangbong
 
결과 : sangbong 지은이 입니다.


- @RequestParam 으로 form 안의 데이터를 직접 받을 수도 있다.
- @PathVariable과 @RequestParam을 혼합해서 사용할 수 있다.
- @RequestParam 을 여러 개 쓸 수도 있다.
- 넘겨받아야 할 파라미터가 너무 많을 경우에는 vo를 만들어서 넣어주면 자동으로 vo에 들어간다.



### SESSION 을 사용하는 방법 : HttpSession session 을 써주기만 하면 된다.


  @RequestMapping("/list")
  public ModelAndView articleList'(HttpSession session)'{
    ModelAndView view = new ModelAndView();
    view.setViewName("article/list");
    
    view.addObject("title", "제목");
    view.addObject("author", "글쓴이");
    
    return view;
  }

