#application_properties #SPRING/application_properties #환경변수 
## 📌 application.properties 사용 방법
- **파일 이름**
	- application.properties
- **위치**
	- src\main\resources\application.properties

- **작성 방법**
```xml
## naver.state
naver.callBackUrl = http://127.0.0.1/ec/login/naverLoginChk.do
```

- **application.properties 사용할 수 있도록 처리**
	- 설정 클래스를 하나 생성
		- ex) ConfigProperties.java
	- 해당 클래스에 어노테이션 추가
		- @Configuration
		- @PropertySource("classpath:application.properties") (설정파일 위치)

```java
package egovframework.config;

import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.PropertySource;

@Configuration
@PropertySource("classpath:application.properties")
public class ConfigProperties {

}
```


- **프로젝트 내 활용**
	- @Value
	- @Autowired

```java
/** @Value 사용*/
@Value("#{naver.callBackUrl}")
private String callBackUrl;


/**환경변수 가져오기 위함(@Autowired + Environment객체 사용)*/
@Autowired
private Environment env;
```

