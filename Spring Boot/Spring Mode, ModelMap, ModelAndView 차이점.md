## Spring Model, ModelMap, ModelAndView 차이점


### Model, ModelMap VS ModelAndView 차이점

- 데이터만 저장한다 VS 데이터와 이동하고자 하는 View Page 를 같이 저장한다.



### Model, ModelMap 공통점
- model.addAttribute("변수명");
- modelMap.addAttribute("변수명");
- 둘 다 addAttribute 를 사용함.
- Model or ModelMap 에 데이터만 저장 후 View 에서 사용목적


### Model, ModelMap 차이점
- Model    : 인터페이스
- ModelMap : 클래스


Java Controller
```
@RequestMapping(value="/test.do")
public String test(HttpServletRequest request, Model model, ModelMap modelMap){
String modelStr = "Model Test";
String modelMapStr = "ModelMap Test";

model.addAttribute("modelVar", modelStr);
modelMap.addAttribute("modelMapVar", modelMapStr);

return "temp/test";
}
```

JSP
```
<body>
Model    저장한 값 : <input type="text" value="$modelVar}" /><br/>
ModelMap 저장한 값 : <input type="text" value="$modelMapVar}" /><br/>
</body>
```


