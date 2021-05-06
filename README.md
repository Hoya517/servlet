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
- name: 서블릿 이름 
- urlPatterns: URL 매핑

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

### 부가기능
*임시 저장소 기능*
- 해당 HTTP 요청이 시작부터 끝날 때 까지 유지되는 임시 저장소 기능
    - 저장: request.setAttribute(name, value)
    - 조회: request.getAttribute(name)

*세션 관리 기능*
- request.getSession(create: true)

------------
## 4. HTTP 요청 데이터
### 주로 3가지 방법 사용
- **GET - 쿼리 파라미터**
    - /url**?username=hello&age=20**
    - 메시지 바디 없이, URL의 쿼리 파라미터에 데이터를 포함해서 전달
    - 예) 검색, 필터, 페이징등에서 많이 사용하는 방식
- **POST - HTML Form**
    - content-type: application/x-www-form-urlencoded
    - 메시지 바디에 쿼리 파리미터 형식으로 전달 username=hello&age=20
    - 예) 회원 가입, 상품 주문, HTML Form 사용
- **HTTP message body**에 데이터를 직접 담아서 요청
    - HTTP API에서 주로 사용, JSON, XML, TEXT
    - 데이터 형식은 주로 JSON 사용
    - POST, PUT, PATCH
