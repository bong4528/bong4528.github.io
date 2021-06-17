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
    
    return view;
  }
}
```

- ModelAndView : 데이터를 전송시킬 수 있는 리턴 타입 ( cf. String 타입은 단순하게 페이지만 열어주는 역할을 함. )





