# 서블릿
------------
1. 스프링 부트 서블릿 환경 구성
@ServletComponentScan
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

2. 서블릿 등록하기
