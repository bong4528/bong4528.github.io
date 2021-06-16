# 출처 : http://www.devkuma.com/books/pages/475


#### WAS가 웹브라우져로부터 Servlet 요청을 받으면
1. 요청을 받을 때 전달 받은 정보를 HttpServletRequest 객체를 생성하여 저장
2. 웹 브라우져에게 응답을 돌려준 HttpServletResponse 객체를 생성 ( 빈 객체 )
3. 생성된 HttpServletRequest (정보가 저장된)와 `HttpServletResponse(비어있는)`를 Servlet에게 전달


#### HTTPServletRequest

##### 1. Http프로토콜의 request 정보를 서블릿에게 전달하기 위한 목적으로 사용
##### 2. Header정보, Parameter, Cookie, URI, URL 등의 정보를 읽어들이는 메소드를 가진 클래스
##### 3. Body의 Stream 을 읽어들이는 메소드를 가지고 있음.

header 정보 확인하기 ( request 에서 확인 )

protected void doGet('HttpServletRequest' request, HttpServletResponse response) throws ServletException, IOException{
    `response`.setContentType("text/html");
    PrintWriter out = response.getWriter();
    out.println("<html>");
    out.println("<header><title>form</title></header>");
    out.println("<body>");
    
    Enumeration<String> headernames = `request`.`getHeaderNames()`;
    while(headerNames.hasMoreElements()){
      String headerName = headerNames.nextElement();
      String headerValue = request.getHeader(headerName);
      out.println(headerName + " : " + headerValue + "<br>");
    }
  
    String uri = `request.getRequestURI()`;
    StringBuffer url = `request.getRequestURL()`;
    String contextPath = `request`.getContextPath()`;
    String remoteAddr = `request`.getRemoteAddr()`;
  
  
    out.println("</body>");
    out.println("</html>");
    out.close();
}


#### HttpServletResponse
    
##### 1.Servlet은 HttpServletResponse 객체에 ContentType, 응답코드, 응답 메시지등을 담아서 전송함.


