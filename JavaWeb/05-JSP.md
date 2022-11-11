# JSP

> **基本用不到了 拿旧笔记放着**

```java
//什么是 jsp，它有什么用?
jsp 的全换是 java server pages。Java 的服务器页面。 
jsp 的主要作用是代替 Servlet 程序回传 html 页面的数据。 
因为 Servlet 程序回传 html 页面数据是一件非常繁锁的事情。开发成本和维护成本都极高。
```

#### Jsp如何访问

```java
jsp 页面和 html 页面一样，都是存放在 web 目录下。访问也跟访问 html 页面一样。
在 web 目录下有如下的文件： 
web 目录
    a.html 页面 访问地址是 =======>>>>>> http://ip:port/工程路径/a.html 
	b.jsp 页面 访问地址是 =======>>>>>> http://ip:port/工程路径/b.jsp
```

#### jsp的本质是什么

```java
//jsp 页面本质上是一个 Servlet 程序。 
当我们第一次访问 jsp 页面的时候。Tomcat 服务器会帮我们把 jsp 页面翻译成为一个 java 源文件。并且对它进行编译成 为.class 字节码程序。
打开java 源文件：
    跟踪原代码发现，HttpJspBase 类。它直接地继承了 HttpServlet 类。也就是说。jsp 翻译出来的 java 类，它间接了继 承了 HttpServlet 类。也就是说，翻译出来的是一个 Servlet 程序
//总结：通过翻译的 java 源代码我们就可以得到结果：jsp 就是 Servlet 程序。 
    大家也可以去观察翻译出来的 Servlet 程序的源代码，不难发现。其底层实现，也是通过输出流。把 html 页面数据回传 给客户端。
```

#### jsp的三种语法

##### **jsp** **头部的** **page** **指令** 

```jsp
jsp 的 page 指令可以修改 jsp 页面中一些重要的属性，或者行为。
<%@ page contentType="text/html;charset=UTF-8" language="java" %>    
i. language 属性 表示 jsp 翻译后是什么语言文件。暂时只支持 java。 
ii. contentType 属性 表示 jsp 返回的数据类型是什么。也是源码中 response.setContentType()参数值 
iii. pageEncoding 属性 表示当前 jsp 页面文件本身的字符集。 
iv. import 属性 跟 java 源代码中一样。用于导包，导类。 
======两个属性是给 out 输出流使用=======
v. autoFlush 属性 设置当 out 输出流缓冲区满了之后，是否自动刷新冲级区。默认值是 true。 vi. buffer 属性 设置 out 缓冲区的大小。默认是 8kb
vii. errorPage 属性 设置当 jsp 页面运行时出错，自动跳转去的错误页面路径。
viii. isErrorPage 属性 设置当前 jsp 页面是否是错误信息页面。默认是 false。如果是 true 可以 获取异常信息。 
ix. session 属性 设置访问当前 jsp 页面，是否会创建 HttpSession 对象。默认是 true。 x. extends 属性 设置 jsp 翻译出来的 java 类默认继承谁。
```

##### **jsp** **中的常用脚本** 

###### 1、声明脚本(极少使用)

```jsp
声明脚本的格式是： <%! 声明 java 代码 %> 
作用：可以给 jsp 翻译出来的 java 类定义属性和方法甚至是静态代码块。内部类等。
```

###### 2、表达式脚本(常用)

```jsp
表达式脚本的格式是：<%=表达式%> 
表达式脚本的作用是：的 jsp 页面上输出数据。 
表达式脚本的特点： 
	1、所有的表达式脚本都会被翻译到_jspService() 方法中 
	2、表达式脚本都会被翻译成为 out.print()输出到页面上 
	3、由于表达式脚本翻译的内容都在_jspService() 方法中,所以_jspService()方法中的对象都可以直接使用。 
	4、表达式脚本中的表达式不能以分号结束。
```

###### 3、代码脚本

```jsp
代码脚本的格式是： 
	<% java 语句 %> 
代码脚本的作用是：可以在 jsp 页面中，编写我们自己需要的功能（写的是 java 语句）。 
代码脚本的特点是： 
	1、代码脚本翻译之后都在_jspService 方法中 
	2、代码脚本由于翻译到_jspService()方法中，所以在_jspService()方法中的现有对象都可以直接使用。 
	3、还可以由多个代码脚本块组合完成一个完整的 java 语句。 
	4、代码脚本还可以和表达式脚本一起组合使用，在 jsp 页面上输出数据
```

#### jsp中的三种注释

```jsp
i. html 注释 
	<!-- 这是 html 注释 -->
	html 注释会被翻译到 java 源代码中。在_jspService 方法里，以 out.writer 输出到客户端。 
ii. java 注释 
	<% // 单行 java 注释 /* 多行 java 注释 */ %> 
	java 注释会被翻译到 java 源代码中。 
iii. jsp 注释 
	<%-- 这是 jsp 注释 --%> 
	jsp 注释可以注掉，jsp 页面中所有代码。
```

#### Jsp九大内置对象

```jsp
jsp 中的内置对象，是指 Tomcat 在翻译 jsp 页面成为 Servlet 源代码后，内部提供的九大对象，叫内置对象。
< request	请求对象>
< response	响应对象>
< pageContext	jsp的上下文对象>
< session	会话对象>
< application	ServletContext对象>
< config	ServletConfig对象>
< out	jsp输出流对象>
< page	指向当前jsp的对象>
< exception	异常对象>
```

#### jsp四大域对象

```jsp
四个域对象分别是： 
<	pageContext (PageContextImpl 类) 当前 jsp 页面范围内有效 
<	request (HttpServletRequest 类)、 一次请求内有效 
<	session (HttpSession 类)、 一个会话范围内有效（打开浏览器访问服务器，直到关闭浏览器） 
<	application (ServletContext 类) 整个 web 工程范围内都有效（只要 web 工程不停止，数据都在） 
域对象是可以像 Map 一样存取数据的对象。四个域对象功能一样。不同的是它们对数据的存取范围。 虽然四个域对象都可以存取数据。在使用上它们是有优先顺序的。 
四个域在使用的时候，优先顺序分别是，他们从小到大的范围的顺序。
	pageContext ====>>> request ====>>> session ====>>> application
```

scope.jsp页面

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
    <%
        pageContext.setAttribute("key","pageContent");
        request.setAttribute("key","request");
        session.setAttribute("key","session");
        application.setAttribute("key","application");
    %>
    pageContext域是否有值：<%=pageContext.getAttribute("key")%><br>
    request域是否有值：<%=request.getAttribute("key")%><br>
    session域是否有值：<%=session.getAttribute("key")%><br>
    application域是否有值：<%=application.getAttribute("key")%><br>
    <%
        request.getRequestDispatcher("/scope1.jsp").forward(request,response);
    %>
</body>
</html>
```

scope1.jsp

```jsp
<body>
    <h1>scope2.jsp页面</h1>
    pageContext域是否有值：<%=pageContext.getAttribute("key")%><br>
    request域是否有值：<%=request.getAttribute("key")%><br>
    session域是否有值：<%=session.getAttribute("key")%><br>
    application域是否有值：<%=application.getAttribute("key")%><br>
</body>
```

#### jsp中的out输出和response.getWriter输出的区别

```jsp
response 中表示响应，我们经常用于设置返回给客户端的内容（输出） 
out 也是给用户做输出使用的。
```

```java
由于 jsp 翻译之后，底层源代码都是使用 out 来进行输出，所以一般情况下。我们在 jsp 页面中统一使用 out 来进行输出。避免打乱页面输出内容的顺序。 
    out.write() 输出字符串没有问题 
    out.print() 输出任意数据都没有问题（都转换成为字符串后调用的 write 输出） 
//深入源码，浅出结论：在 jsp 页面中，可以统一使用 out.print()来进行输出
```

#### jsp常用标签

##### jsp静态包含

```jsp
<%--
    <%@ include file=""%> 就是静态包含 
		file 属性指定你要包含的 jsp 页面的路径 
		地址中第一个斜杠 / 表示为 http://ip:port/工程路径/ 映射到代码的 web 目录
静态包含的特点： 
	1、静态包含不会翻译被包含的 jsp 页面。 
	2、静态包含其实是把被包含的 jsp 页面的代码拷贝到包含的位置执行输出。
--%> 
<%@ include file="/include/footer.jsp"%>
```

##### jsp动态包含

```jsp
<%--
    <jsp:include page=""></jsp:include> 这是动态包含 
    page 属性是指定你要包含的 jsp 页面的路径 
    动态包含也可以像静态包含一样。把被包含的内容执行输出到包含位置 
    动态包含的特点： 
        1、动态包含会把包含的 jsp 页面也翻译成为 java 代码 
        2、动态包含底层代码使用如下代码去调用被包含的 jsp 页面执行输出。 JspRuntimeLibrary.include(request, response, "/include/footer.jsp", out, false); 
		3、动态包含，还可以传递参数 
--%> 
<jsp:include page="/include/footer.jsp">
    <jsp:param name="username" value="bbj"/> 
    <jsp:param name="password" value="root"/> 
</jsp:include>
```

##### jsp标签-转发

```jsp
<%--
    <jsp:forward page=""></jsp:forward> 是请求转发标签，它的功能就是请求转发 page 属性设置请求转发的路径 
--%> 
<jsp:forward page="/scope2.jsp"></jsp:forward>
```

#### **Listener** **监听器**

```java
ServletContextListener 它可以监听 ServletContext 对象的创建和销毁。 ServletContext 对象在 web 工程启动的时候创建，在 web 工程停止的时候销毁。 
    监听到创建和销毁之后都会分别调用 ServletContextListener 监听器的方法反馈。 
```

两个方法分别是：

```java
public interface ServletContextListener extends EventListener { 
    /*** 在 ServletContext 对象创建之后马上调用，做初始化 */ 
    public void contextInitialized(ServletContextEvent sce); 
    /*** 在 ServletContext 对象销毁之后调用 */ 
    public void contextDestroyed(ServletContextEvent sce); }
```

使用 ServletContextListener 监听器监听 ServletContext 对象。 

```java
使用步骤如下： 
1、编写一个类去实现 ServletContextListener 
2、实现其两个回调方法 
3、到 web.xml 中去配置监听器
```

监听实现类：

```java
public class MyServletContextListenerImpl implements ServletContextListener { 
    @Override 
    public void contextInitialized(ServletContextEvent sce) { 
        System.out.println("ServletContext 对象被创建了"); 
    }
    @Override
    public void contextDestroyed(ServletContextEvent sce) { 
        System.out.println("ServletContext 对象被销毁了"); 
    } 
}
```

web.xml配置：

```xml
<!--配置监听器-->
<listener> 
    <listener-class>com.atguigu.listener.MyServletContextListenerImpl</listener-class></listener>
```

