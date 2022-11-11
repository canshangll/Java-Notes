# JavaWeb

## JavaWeb的概念

- **什么是 JavaWeb** 
  JavaWeb 是指，所有通过 Java 语言编写可以通过浏览器访问的程序的总称，叫 JavaWeb。 JavaWeb 是基于请求和响应来开发的。
- **什么是请求**
  请求是指客户端给服务器发送数据，叫请求 Request。
- 什么是响应  
  响应是指服务器给客户端回传数据，叫响应 Response。    
- **请求和响应的关系**    
  请求和响应是成对出现的，有请求就有响应。

```sequence
客户端(浏览器)->服务器(Tomcat): 客户端给服务器发数据叫请求(Request)
服务器(Tomcat)->客户端(浏览器): 服务器给客户端回传数据叫响应(Response)
```

**Web资源分类**

web 资源按实现的技术和呈现的效果的不同，又分为静态资源和动态资源两种。
静态资源： html、css、js、txt、mp4 视频 , jpg 图片 
动态资源： jsp 页面、Servlet 程序

**常用的Web服务器**

- Tomcat：由 Apache 组织提供的一种 Web 服务器，提供对 jsp 和 Servlet 的支持。它是一种轻量级的 javaWeb 容器（服务 器），也是当前应用最广的 JavaWeb 服务器（免费）。
- Jboss：是一个遵从 JavaEE 规范的、开放源代码的、纯 Java 的 EJB 服务器，它支持所有的 JavaEE 规范（免费）。    
- GlassFish： 由 Oracle 公司开发的一款 JavaWeb 服务器，是一款强健的商业服务器，达到产品级质量（应用很少）。    
- Resin：是 CAUCHO 公司的产品，是一个非常流行的服务器，对 servlet 和 JSP 提供了良好的支持， 性能也比较优良，resin 自身采用 JAVA 语言开发（收费，应用比较多）。     
- WebLogic：是 Oracle 公司的产品，是目前应用最广泛的 Web 服务器，支持 JavaEE 规范， 而且不断的完善以适应新的开发要求，适合大型项目（收费，用的不多，适合大公司）。



## Tomacat

安装：找到你需要用的 Tomcat 版本对应的 zip 压缩包，解压到需要安装的目录即可。

**目录说明**

- bin 专门用来存放 Tomcat 服务器的可执行程序 
- conf 专门用来存放 Tocmat 服务器的配置文件 
- lib 专门用来存放 Tomcat 服务器的 jar 包 
- logs 专门用来存放 Tomcat 服务器运行时输出的日记信息 
- temp 专门用来存放 Tomcdat 运行时产生的临时数据 
- webapps 专门用来存放部署的 Web 工程。 
- work 是 Tomcat 工作时的目录，用来存放 Tomcat 运行时 jsp 翻译为 Servlet 的源码，和 Session 钝化的目录。

### 启动与停止

找到 Tomcat 目录下的 bin 目录下的 startup.bat 文件，双击，就可以启动 Tomcat 服务器。
测试
打开浏览器，在浏览器地址栏中输入以下地址测试： 
1、http://localhost:8080 
2、http://127.0.0.1:8080 
3、http://真实 ip:8080

1、点击 tomcat 服务器窗口的 x 关闭按钮 
2、把 Tomcat 服务器窗口置为当前窗口，然后按快捷键 Ctrl+C 
3、找到 Tomcat 的 bin 目录下的 shutdown.bat 双击，就可以停止 Tomcat 服务器

### 部署web过程到Tomcat

- 第一种：

  把 web 工程的目录拷贝到 Tomcat 的 webapps 目录下 即可。
  在浏览器中输入访问地址格式如下： http://ip:port/工程名/目录下/文件名

- 第二种：

  找到 Tomcat 下的 conf 目录\Catalina\localhost\ 下,创建如下的配置文件：如 abc.xml
  配置文件内容：
      <!-- Context 表示一个工程上下文 path 表示工程的访问路径:/abc docBase 表示你的工程目录在哪里 --> <Context path="/abc" docBase="E:\book" />
  访问这个工程的路径如下:http://ip:port/abc/ 就表示访问 E:\book 目录

**ROOT 的工程的访问**

当我们在浏览器地址栏中输入访问地址如下： http://ip:port/ ====>>>> 没有工程名的时候，默认访问的是 ROOT 工程。 
当我们在浏览器地址栏中输入的访问地址如下： http://ip:port/工程名/ ====>>>> 没有资源名，默认访问 index.html 页面



## Servlet

**什么是Servlet**

- Servlet 是 JavaEE 规范之一。规范就是接口 
- Servlet 就 JavaWeb 三大组件之一。三大组件分别是：Servlet 程序、Filter 过滤器、Listener 监听器。 
- Servlet 是运行在服务器上的一个 java 小程序，它可以接收客户端发送过来的请求，并响应数据给客户端。

**手动实现 Servlet 程序 **

- 编写一个类去实现 Servlet 接口
- 实现 service 方法，处理请求，并响应数据
- 到web.xml 中去配置 servlet 程序的访问地址

public class HelloServlet implements Servlet { //实现接口 }

**配置文件**

```xml
<!--    servlet标签给Tomcat配置Servlet程序-->
    <servlet>
<!--        servlet-name标签 Servlet程序起一个别名(一般是类名)-->
        <servlet-name>HelloServlet</servlet-name>
<!--        servlet-class是Servlet程序的全类名-->
        <servlet-class>com.atguigu.servlet.HelloServlet</servlet-class>
    </servlet>
<!--        servlet-mapping标签给servlet程序配置访问地址-->
    <servlet-mapping>
<!--  servlet-name标签的作用是告诉服务器，我当前配置的地址给哪个Servlet程序使用-->
        <servlet-name>HelloServlet</servlet-name>
<!--        url-pattern标签配置访问地址
            / 斜杠在服务器解析的时候，表示地址为:http://ip:post/过程路径 <br/>
            /hello 表示地址为：   http://ip:post/过程路径/hello      <br/> -->
        <url-pattern>/hello</url-pattern>
    </servlet-mapping>
```

**常见错误**

- 常见的错误 1：url-pattern 中配置的路径没有以斜杠打头。
  Invalid <url-pattern> hello in servlet mapping
- 常见错误 2：servlet-name 配置的值不存在：    
  Servlet mapping specifies an unknown servlet name HelloServlet1
- 常见错误 3：servlet-class 标签的全类名配置错误：
  com.atguigu.servlt.HelloServlet    

### Servlet的生命周期

- 执行 Servlet 构造器方法 
- 执行 init 初始化方法 第一、二步，是在第一次访问，的时候创建 Servlet 程序会调用。 
- 执行 service 方法 第三步，每次访问都会调用。
- 执行 destroy 销毁方法 第四步，在 web 工程停止的时候调用。

### GET和POST请求的分发处理

```java
/*** service 方法是专门用来处理请求和响应的 */ 
@Override 
public void service(ServletRequest servletRequest, ServletResponse servletResponse) throws ServletException, IOException {
    System.out.println("3 service === Hello Servlet 被访问了"); 
 	// 类型转换（因为它有 getMethod()方法） 
	HttpServletRequest httpServletRequest = (HttpServletRequest) 	servletRequest; 
 	// 获取请求的方式 
	String method = httpServletRequest.getMethod(); 
	if ("GET".equals(method)) { 
    	doGet(); 
	} else if ("POST".equals(method)) { 
    	doPost(); 
	} 
}
/*** 做 get 请求的操作 */ 
public void doGet(){ 
    System.out.println("get 请求");
}
/*** 做 post 请求的操作 */ 
public void doPost(){ 
    System.out.println("post 请求"); 
}
```

### 通过继承HttpServlet 实现Servlet程序

一般在实际项目开发中，都是使用继承 HttpServlet 类的方式去实现 Servlet 程序。

- 编写一个类去继承 HttpServlet 类 
- 根据业务需要重写 doGet 或 doPost 方法 
- 到 web.xml 中的配置 Servlet 程序的访问地址

```java
public class HelloServlet2 extends HttpServlet {
    @Override 
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
        System.out.println("HelloServlet2 的 doGet 方法"); 
    }
	@Override 
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
        System.out.println("HelloServlet2 的 doPost 方法"); 
    } 
}    
```

**web.xml**

```xml
<servlet>
    <servlet-name>HelloServlet2</servlet-name> 
    <servlet-class>com.atguigu.servlet.HelloServlet2</servlet-class> </servlet>
<servlet-mapping>
    <servlet-name>HelloServlet2</servlet-name> 
    <url-pattern>/hello2</url-pattern>
</servlet-mapping>
```

### ServletConfig类

- ServletConfig 类从类名上来看，就知道是 Servlet 程序的配置信息类。 
- Servlet 程序和 ServletConfig 对象都是由 Tomcat 负责创建，我们负责使用。 
- Servlet 程序默认是第一次访问的时候创建，ServletConfig 是每个 Servlet 程序创建时，就创建一个对应的 ServletConfig 对象。

**三大作用**

- 可以获取 Servlet 程序的别名 servlet-name 的值 
- 获取初始化参数 init-param 
- 获取 ServletContext 对象

**web.xml**

```xml
    <servlet>
        <servlet-name>HelloServlet</servlet-name>
        <servlet-class>com.atguigu.servlet.HelloServlet</servlet-class>
        <init-param>
            <param-name>username</param-name>
            <param-value>root</param-value>
        </init-param>
        <init-param>
            <param-name>url</param-name>
            <param-value>jdbc:mysql://localhost:3306/test</param-value>
        </init-param>
    </servlet>
    <servlet-mapping>
        <servlet-name>HelloServlet</servlet-name>
        <url-pattern>/hello</url-pattern>
    </servlet-mapping>
```

**Servlet代码**

```java
@Override 
public void init(ServletConfig config) throws ServletException { 
    super.init(config) //注意：重写init方法里面一定要调用父类的init(ServletConfig)操作
    System.out.println("2 init 初始化方法"); 
	// 1、可以获取 Servlet 程序的别名 servlet-name 的值 
	System.out.println("HelloServlet 程序的别名是:" + 		config.getServletName());
	// 2、获取初始化参数 init-param 
	System.out.println("初始化参数 username 的值是;" + 	config.getInitParameter("username")); 
	System.out.println("初始化参数 url 的值是;" + config.getInitParameter("url")); 
	// 3、获取 ServletContext 对象 
	System.out.println(config.getServletContext()); 
}
```

### ServletContext类

- ServletContext 是一个接口，它表示 Servlet 上下文对象 
- 一个 web 工程，只有一个 ServletContext 对象实例。 
- ServletContext 对象是一个域对象。 
- ServletContext 是在 web 工程部署启动的时候创建。在 web 工程停止的时候销毁。 

什么是域对象? 
域对象，是可以像 Map 一样存取数据的对象，叫域对象。 这里的域指的是存取数据的操作范围，整个 web 工程。 
		存数据 		 取数据 			删除数据 
Map 	put() 			get() 			remove() 
域对象 setAttribute() 	getAttribute()  removeAttribute();

**ServletContext类的四个作用**

- 获取 web.xml 中配置的上下文参数 context-param 
- 获取当前的工程路径，格式: /工程路径 
- 获取工程部署后在服务器硬盘上的绝对路径 
- 像 Map 一样存取数据

**ServletContext.java**

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //1.获取web.xml 中配置的上下文参数context-paaram
        ServletContext servletContext = getServletConfig().getServletContext();
        String username = servletContext.getInitParameter("username");
        System.out.println("context-param参数username的值是：" + username);
        System.out.println("context-param参数password的值是：" + servletContext.getInitParameter("password"));
        System.out.println("init-paraam参数url的值是：" + servletContext.getInitParameter("url"));
        //2.获取当前的过程路径，格式：/工程路径
        System.out.println("当前工程路径" + servletContext.getContextPath());
        //3.获取工程部署后在服务器硬盘上的绝对路径
        /**
         * / 斜杠被服务器解析地址为：http://ip:post/工程名/  映射到IDEA代码的web目录		  */
        System.out.println("过程部署的路径是："+servletContext.getRealPath("/"));
        System.out.println("工程下css目录的绝对路径是：："+servletContext.getRealPath("/css"));
        System.out.println("工程下imgs目录1/jpg的绝对路径是：："+servletContext.getRealPath("/imgs/1.jpg"));
    }
```

**web.xml**

```xml
<context-param>
	<param-name>username</param-name>
    <param-value>context</param-value>
</context-param>
<context-param>
    <param-name>password</param-name>
	<param-value>root</param-value>
</context-param>
```

**ServletContext 像 Map 一样存取数据：**

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
    //获取ServletContext对象
	ServletContext servletContext = getServletContext();
    System.out.println(servletContext);
    System.out.println("保存之前：Context1 获取 key1的值是："+servletContext.getAttribute("key1"));
    servletContext.setAttribute("key1","value1");
    System.out.println("Context1 中获取域数据key1的值是："+servletContext.getAttribute("key1"));
}
```

### HTTP协议

什么是 HTTP 协议 
什么是协议? 
    协议是指双方，或多方，相互约定好，大家都需要遵守的规则，叫协议。 
    所谓 HTTP 协议，就是指，客户端和服务器之间通信时，发送的数据，需要遵守的规则，叫 HTTP 协议。 HTTP 协议中的数据又叫报文。

请求的 HTTP 协议格式
    客户端给服务器发送数据叫请求。 
    服务器给客户端回传数据叫响应。 
    请求又分为 GET 请求，和 POST 请求两种

**GET请求**

- 请求行 
      (1) 请求的方式 GET 
      (2) 请求的资源路径[+?+请求参数] 
      (3) 请求的协议的版本号 HTTP/1.1 
- 请求头 
      key : value 组成 不同的键值对，表示不同的含义。

**Post请求**

- 请求行
      (1) 请求的方式 POST 
      (2) 请求的资源路径[+?+请求参数] 
      (3) 请求的协议的版本号 HTTP/1.1 
- 请求头
      1) key : value 不同的请求头，有不同的含义 
          空行 
- 请求体 ===>>> 就是发送给服务器的数据

**常用请求头的说明**

- Accept: 表示客户端可以接收的数据类型 
- Accpet-Languege: 表示客户端可以接收的语言类型 
- User-Agent: 表示客户端浏览器的信息 
- Host： 表示请求时的服务器 ip 和端口号

**哪些是GET请求和POST请求**

- GET 请求有哪些：
  - form 标签 method=get 
  - a 标签 
  - link 标签引入 css 
  - Script 标签引入 js 文件 
  - img 标签引入图片 
  - iframe 引入 html 页面 
  - 在浏览器地址栏中输入地址后敲回车 
- POST 请求有哪些： 
  - form 标签 method=post

**响应的** **HTTP** **协议格式** 

- 响应行
      (1) 响应的协议和版本号 
      (2) 响应状态码 
      (3) 响应状态描述符 
- 响应头 
      (1) key : value 不同的响应头，有其不同含义 
      空行 
- 响应体 ---->>> 就是回传给客户端的数据

**常用的响应码说明**

- 200 表示请求成功 
- 302 表示请求重定向（明天讲） 
- 404 表示请求服务器已经收到了，但是你要的数据不存在（请求地址错误）
- 500 表示服务器已经收到请求，但是服务器内部错误（代码错误）

**MIME类型说明**

MIME 是 HTTP 协议中数据类型。 
MIME 的英文全称是"Multipurpose Internet Mail Extensions" 多功能 Internet 邮件扩充服务。MIME 类型的格式是“大类型/小 类型”，并与某一种文件的扩展名相对应。

**常见的 MIME 类型：**

| 文件               | MIME类型                             |
| ------------------ | ------------------------------------ |
| 超文本标记语言文本 | .html , .htm     text/html           |
| 普通文本           | .txt   text/plain                    |
| RTF 文本           | .rtf   application/rtf               |
| GIF 图形           | .gif   image/gif                     |
| JPEG 图形          | jpeg,.jpg    image/jpeg              |
| au 声音文件        | .au    audio/basic                   |
| MIDI 音乐文件      | mid,.midi    audio/midi,audio/x-midi |
| RealAudio 音乐文件 | .ra, .ram   audio/x-pn-realaudio     |
| MPEG 文件          | .mpg,.mpeg    video/mpeg             |
| AVI 文件           | .avi     video/x-msvideo             |
| GZIP 文件          | .gz      application/x-gzip          |
| TAR 文件           | .tar     application/x-tar           |

###  HttpServletRequest类

**作用：**

每次只要有请求进入 Tomcat 服务器，Tomcat 服务器就会把请求过来的 HTTP 协议信息解析好封装到 Request 对象中。 然后传递到 service 方法（doGet 和 doPost）中给我们使用。我们可以通过 HttpServletRequest 对象，获取到所有请求的 信息。

**HttpServletRequest类的常用方法**

| getRequestURI()          | 获取请求的资源路径                   |
| ------------------------ | ------------------------------------ |
| getRequestURL()          | 获取请求的统一资源定位符（绝对路径） |
| getRemoteHost()          | 获取客户端的 ip 地址                 |
| getHeader()              | 获取请求头                           |
| getParameter()           | 获取请求的参数                       |
| getParameterValues()     | 获取请求的参数（多个值的时候使用）   |
| getMethod()              | 获取请求的方式 GET 或 POST           |
| setAttribute(key, value) | 设置域数据                           |
| getAttribute(key)        | 获取域数据                           |
| getRequestDispatcher()   | 获取请求转发对象                     |

#### **获取请求参数**

表单：

```html
<body> 
    <form action="http://localhost:8080/07_servlet/parameterServlet" method="get">
        用户名：<input type="text" name="username"><br/>
        密码：<input type="password" name="password"><br/> 
        兴趣爱好：<input type="checkbox" name="hobby" value="cpp">C++ 
        <input type="checkbox" name="hobby" value="java">Java
        <input type="checkbox" name="hobby" value="js">JavaScript<br/>
        <input type="submit"> 
    </form> 
</body>
```

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //设置请求字体的字符编码，解决post请求的中文乱码
        req.setCharacterEncoding("UTF-8");
        //获取请求的参数
        String username = req.getParameter("username");
        String password = req.getParameter("password");
        String[] hobby = req.getParameterValues("hobby");

        System.out.println("用户名：" + username);
        System.out.println("密码：" + password);
        System.out.println("兴趣爱好：" + Arrays.asList(hobby));
    }
```

#### 请求的转发

什么是请求的转发? 
请求转发是指，服务器收到请求后，从一次资源跳转到另一个资源的操作叫请求转发。

```java
public class Servlet1 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("=======doGet=======");
        //获取请求的参数(办事的材料)查看
        String username = req.getParameter("username");
        System.out.println("在Servlet1(柜台1)中查看参数(材料)：" + username);
        //给材料 盖一个章，并传递到Servlet2(柜台2)去查看
        req.setAttribute("key","柜台1的章");
        //问路:Servlet2(柜台2) 怎么走
        /**
         * 请求转发必须要以斜杠打头，/ 斜杠表示地址为：http://ip:port/工程名/ ，映射到IDEA代码的web目录
         */
        RequestDispatcher requestDispatcher = req.getRequestDispatcher("/form.html");
        //走向 Servlet2 （柜台2）
        requestDispatcher.forward(req,resp);
    }
}

public class Servlet2 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //获取请求的参数(办事的材料)查看
        String username = req.getParameter("username");
        System.out.println("在Servlet2(柜台2)中查看参数(材料)：" + username);
        //查看 是否有柜台1 的盖章
        Object key = req.getAttribute("key");
        System.out.println("柜台1是否有章：" + key);
        //处理自己的业务
        System.out.println("Servlet2 处理自己的业务");
    }
}
```

#### base标签的作用

base标签可以设置当前页面中所有相对路径工作时，参照哪个路径来进行跳转

```html
<!--base 标签设置页面相对路径工作时参照的地址 href 属性就是参数的地址值 -->
<base href="http://localhost:8080/07_servlet/a/b/">
```

#### web中 / 斜杠的不同意义

在 web 中 / 斜杠 是一种绝对路径。 
/ 斜杠 如果被浏览器解析，得到的地址是：http://ip:port/ 
	<a href="/"> 斜杠 </a> 
/ 斜杠 如果被服务器解析，得到的地址是：http://ip:port/工程路径 
	1、<url-pattern>/servlet1</url-pattern> 
    2、servletContext.getRealPath(“/”); 
	3、request.getRequestDispatcher(“/”); 
特殊情况： response.sendRediect(“/”); 把斜杠发送给浏览器解析。得到 http://ip:port/

### HttpServletResponse类

**作用**

HttpServletResponse 类和 HttpServletRequest 类一样。每次请求进来，Tomcat 服务器都会创建一个 Response 对象传 递给 Servlet 程序去使用。HttpServletRequest 表示请求过来的信息，HttpServletResponse 表示所有响应的信息,我们如果需要设置返回给客户端的信息，都可以通过 HttpServletResponse 对象来进行设置

**两个输出流的说明**

字节流 getOutputStream(); 常用于下载（传递二进制数据） 
字符流 getWriter(); 常用于回传字符串（常用） 
两个流同时只能使用一个。 
使用了字节流，就不能再使用字符流，反之亦然，否则就会报错。
//同时使用报错： getOutputStream() has already been called for this response

**往客户端回传数据** 

```java
public class ResponseIOServlet extends HttpServlet { 
    @Override 
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
        // 要求 ： 往客户端回传 字符串 数据。 
        PrintWriter writer = resp.getWriter(); 
        writer.write("response's content!!!"); 
    } 
}
```

**响应的乱码解决**

解决响应中文乱码方案一(不推荐使用):
	设置服务器字符集为 
	UTF-8 resp.setCharacterEncoding("UTF-8"); 
	通过响应头，设置浏览器也使用 UTF-8 字符集 
	resp.setHeader("Content-Type", "text/html; charset=UTF-8");

解决响应中文乱码方案二(推荐)
	它会同时设置服务器和客户端都使用 UTF-8 字符集，还设置了响应头 
	此方法一定要在获取流对象之前调用才有效 
	resp.setContentType("text/html; charset=UTF-8");

**请求重定向**

请求重定向，是指客户端给服务器发请求，然后服务器告诉客户端说。我给你一些地址。你去新地址访问。叫请求 重定向（因为之前的地址可能已经被废弃）。

请求重定向的第一种方案： 
    设置响应状态码 302 ，表示重定向，（已搬迁） 
    resp.setStatus(302); 
	设置响应头，说明 新的地址在哪里 
	resp.setHeader("Location", "http://localhost:8080"); 

请求重定向的第二种方案（推荐使用）： 
    resp.sendRedirect("http://localhost:8080");