### login 페이지 만들기

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




