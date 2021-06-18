## multipartRequest 와 AbstractView를 사용한 upload / download 처리

### 파일 업로드
Spring의 multipartrequest를 사용하여 파일 업로드 처리를 해 보겠다. ( 다중파일 업로드 가능)
multipartrequest를 사용하여 파일 처리를 하기 위해선
JSP에서 파일을 보낼때 다음과 같이 form 에 **enctype="multipart/form-data"** 라고 알려주어야 한다.

`<form name="test" enctype="multipart/form-data">`


controller 에서는 jsp에서 넘어온 request 정보를 multipartRequest로 캐스팅 후 파일 정보를 추추라여 업로드 처리를 한다.
```
public ModelAndView registBoard(HttpServletRequest request
                              , HttpServletResponse response, Object command) throws Exception{
    ModelAndView mnv = new ModelAndView();
       
    // 넘어온 request를 multipartRequest로 캐스팅 한 후
    MultipartHttpServletRequest multipartRequest = (MultipartHttpServletRequest) request;
       
    // getFileNames를 통해 구하고자 하는 파일 이름들을 구하면 Iterator 형태로 넘어온 file 들의 이름들이 리턴된다.
    Iterator fileNameIter = multipartRequest.getFileNames();
       
    // Iterator 형태로 추출된 파일들의 이름을 키값으로 하여, while 문을 돌면서 넘어온 파일들의 정보를 추출한다.
    while (fileNameIter.hasNext()){
        String key = (String)fileNameIter.next();
        MultipartFile file = multipartRequest.getFile(key);
           
        //파일 업로드 로직 부분
        ...;
    }
    
    mnv.setViewName("파일 업로드 후 전송될 페이지 정보");
    return mnv;
}
```


### 파일 다운로드

Spring에서 파일 다운로드를 구현하고 하는 경우
AbstractView 클래스를 상속받아, 다운로드 파일의 출력을 하기 위한 특정 view 클래스를 만들어 구현하는 방법이 있다.

다운로드 기능을 담당하기 위해 **AbstractView 클래스를 상속받은  FileDownloadView 클래스** 이다.

```

```



