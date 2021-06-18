## multipartRequest 와 AbstractView를 사용한 upload / download 처리

### 파일 업로드
Spring의 multipartrequest를 사용하여 파일 업로드 처리를 해 보겠다. ( 다중파일 업로드 가능)
multipartrequest를 사용하여 파일 처리를 하기 위해선
JSP에서 파일을 보낼때 다음과 같이 form 에 **enctype="multipart/form-data"** 라고 알려주어야 한다.

`<form name="test" enctype="multipart/form-data">`


controller 에서는 jsp에서 넘어온 request 정보를 multipartRequest로 캐스팅 후 파일 정보를 추추라여 업로드 처리를 한다.
```

```
