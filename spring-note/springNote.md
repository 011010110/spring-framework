spring源码阅读笔记
======
1.Bean的创建
===
2.容器的创建
===
3.AOP的实现
===
4.jdbc,ORM集成方式
===
5.事务的实现机制
===
6.springMVC
===
6.1springMVC基本配置
---
+ web.xml配置
><web-app>
	<display-name>Archetype Created Web Application</display-name>
	<context-param>
		<param-name>contextConfigLocation</param-name>
		<param-value>classpath*:spring/spring.xml</param-value>
	</context-param>
	<listener>
		<listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
	</listener>
	<servlet>
		<servlet-name>dispatcherServlet</servlet-name>
		<servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
		<init-param>
			<param-name>contextConfigLocation</param-name>
			<param-value>classpath*:spring/spring-mvc.xml</param-value>
		</init-param>
		<load-on-startup>1</load-on-startup>
	</servlet>
	<!-- Map all requests to the DispatcherServlet for handling -->
	<servlet-mapping>
		<servlet-name>dispatcherServlet</servlet-name>
		<url-pattern>*.html</url-pattern>
	</servlet-mapping>
</web-app>

6.2springMVC初始化
---
+ ContextLoaderListener
    ContextLoaderListener负责启动web容器，并将容器添加到ServletContext中
+ 类图

![ContextLoaderListener类图](img/uml/ContextLoaderListener.png)
+ 初始化root webApplication

![contextLoaderListener初始化时序图](img/sequence/contextLoaderListenterInit.png)

6.3请求调用过程
---