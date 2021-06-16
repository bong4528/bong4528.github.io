# 출처 : http://www.devkuma.com/books/pages/475


##### 컨트롤러에서 직접 텍스트 콘텐츠를 반환한다. ?? 아마도 바디에 담아 준다는 내용인듯

메소드에 @ResponseBody를 붙이면 반환 값으로 직접 응답 내용을 반환할 수 있다.
```
    @RequestMapping("/text1")
    @ResponseBody
    public String text1() {
        return "text content";
    }
```


##### HTTPServletResponse 에서 텍스트 콘텐츠를 반환한다.

반환 값을 void로 하고 HttpServletResponse를 인자로 받도록 하면 직접 응답을 쓸 수도 있다.
```
@RequestMapping("/text2")
public void text2(HttpServletResponse res) throws IOException {
    res.getWriter().write("text content");
}
```

