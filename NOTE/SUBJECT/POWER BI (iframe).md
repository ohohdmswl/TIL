- power bi 를 iframe 사용해서  표출되는지 검토
- [power bi 웹 게시 공홈 설명](https://learn.microsoft.com/ko-kr/power-bi/collaborate-share/service-publish-to-web)
	-  power bi 예시 보고서를 iframe로 표출

![image](https://github.com/user-attachments/assets/0574b481-ed7e-4874-a77f-95954582f714)

![[Pasted image 20240813113554.png]]


- [postgis st_ 함수] (https://postgis.net/docs/manual-2.4/postgis-ko_KR.html#ST_AsText)


- 대체 에이젝스 왜 안되는거임
```java
                <!-- json 사용 위한 추가 내용(@responsebody) -->
		<property name="messageConverters">
			<list>
				<bean class="org.springframework.http.converter.json.MappingJackson2HttpMessageConverter" />
				
				<bean class="org.springframework.http.converter.xml.Jaxb2RootElementHttpMessageConverter" >
					<property name = "supportedMediaTypes">
						<list>
							<value>*/*;charset=UTF-8</value>
						</list>
					</property>
				</bean>
			</list>
		</property>
```


- dispatcher-servlet
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xmlns:p="http://www.springframework.org/schema/p"
        xmlns:context="http://www.springframework.org/schema/context"
        xmlns:mvc="http://www.springframework.org/schema/mvc"
        xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-4.0.xsd
                http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context-4.0.xsd
                http://www.springframework.org/schema/mvc http://www.springframework.org/schema/mvc/spring-mvc-4.0.xsd">

    <context:component-scan base-package="projectNm">
        <context:include-filter type="annotation" expression="org.springframework.stereotype.Controller"/>
        <context:include-filter type="annotation" expression="org.springframework.stereotype.Service"/>
        <context:include-filter type="annotation" expression="org.springframework.stereotype.Repository"/>
    </context:component-scan>

    <bean class="org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter">
        <property name="webBindingInitializer">
            <bean class="egovframework.example.cmmn.web.EgovBindingInitializer"/>
        </property>
        
                <!-- json 사용 위한 추가 내용(@responsebody) -->
		<property name="messageConverters">
			<list>
				<bean class="org.springframework.http.converter.json.MappingJackson2HttpMessageConverter" />
				
				<bean class="org.springframework.http.converter.xml.Jaxb2RootElementHttpMessageConverter" >
					<property name = "supportedMediaTypes">
						<list>
							<value>*/*;charset=UTF-8</value>
						</list>
					</property>
				</bean>
			</list>
		</property>
        
        
        
    </bean>
    <bean class="org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerMapping">
        <property name="interceptors">
            <list>
                <ref bean="localeChangeInterceptor" />
            </list>
        </property>
    </bean>
    
    <bean id="localeResolver" class="org.springframework.web.servlet.i18n.SessionLocaleResolver" />
    <!-- 쿠키를 이용한 Locale 이용시 <bean id="localeResolver" class="org.springframework.web.servlet.i18n.CookieLocaleResolver"/> -->
    <bean id="localeChangeInterceptor" class="org.springframework.web.servlet.i18n.LocaleChangeInterceptor">
        <property name="paramName" value="language" />
    </bean>


    <bean class="org.springframework.web.servlet.handler.SimpleMappingExceptionResolver">
        <property name="defaultErrorView" value="cmmn/egovError"/>
        <property name="exceptionMappings">
            <props>
                <prop key="org.springframework.dao.DataAccessException">cmmn/dataAccessFailure</prop>
                <prop key="org.springframework.transaction.TransactionException">cmmn/transactionFailure</prop>
                <prop key="org.egovframe.rte.fdl.cmmn.exception.EgovBizException">cmmn/egovError</prop>
                <prop key="org.springframework.security.AccessDeniedException">cmmn/egovError</prop>
            </props>
        </property>
    </bean>

    <bean class="org.springframework.web.servlet.view.UrlBasedViewResolver" p:order="1"
	    p:viewClass="org.springframework.web.servlet.view.JstlView"
	    p:prefix="/WEB-INF/jsp/" p:suffix=".jsp"/>

    <!-- For Pagination Tag -->
    <bean id="imageRenderer" class="egovframework.example.cmmn.web.EgovImgPaginationRenderer"/>

    <bean id="paginationManager" class="org.egovframe.rte.ptl.mvc.tags.ui.pagination.DefaultPaginationManager">
        <property name="rendererType">
            <map>
                <entry key="image" value-ref="imageRenderer"/>
            </map>
        </property>
    </bean>
	<!-- /For Pagination Tag -->


<!-- dispatcher-servlet.xml에 설정 -->
<!-- <bean class="org.springframework.web.servlet.view.BeanNameViewResolver">  -->
<!-- 	<property name="order" value="0"/>  -->
<!-- </bean> -->
<!-- <bean id="jsonView" class="org.springframework.web.servlet.view.json.MappingJackson2JsonView"> -->
<!-- 	<property name="contentType" value="application/json;charset=UTF-8"></property> -->
<!-- </bean> -->




    <mvc:view-controller path="/cmmn/validator.do" view-name="cmmn/validator"/>
</beans>
```


