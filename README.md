# 서블릿
------------
## 1. 스프링 부트 서블릿 환경 구성
### @ServletComponentScan
: 스프링 부트는 서블릿을 직접 등록해서 사용할 수 있도록 @ServletCompoentScan을 지원한다.

*ServletApplication*
```java
@ServletComponentScan  // 서블릿 자동 등록
@SpringBootApplication
public class ServletApplication {

	public static void main(String[] args) {
		SpringApplication.run(ServletApplication.class, args);
	}

}
```

------------
## 2. 서블릿 등록하기
### @WebServlet
* name: 서블릿 이름 
* urlPatterns: URL 매핑

### service 메서드
: HTTP 요청을 통해 매핑된 URL이 호출되면 서블릿 컨테이너는 해당 메서드를 실행한다.

*HelloServlet*
```java
@WebServlet(name = "helloServlet", urlPatterns = "/hello")
public class HelloServlet extends HttpServlet {

    @Override
    protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {

        System.out.println("HelloServlet.service");
        
    }
}
```

------------
## 3. HttpServletRequest
### HTTP 요청 메시지를 편리하게 조회할 수 있음.
- START LINE
    - HTTP 메소드
    - URL
    - 쿼리 스트링
    - 스키마, 프로토콜
- 헤더
    - 헤더 조회
- 바디
    - form 파라미터 형식 조회
    - message body 데이터 직접 조회
