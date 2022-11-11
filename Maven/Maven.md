# Maven

#  为什么学习Maven

## 1、Maven 作为依赖管理工具

### ①jar 包的规模

随着我们使用越来越多的框架，或者框架封装程度越来越高，项目中使用的jar包也越来越多。项目中，一个模块里面用到上百个jar包是非常正常的。

比如下面的例子，我们只用到 SpringBoot、SpringCloud 框架中的三个功能：

- Nacos 服务注册发现
- Web 框架环境
- 图模板技术 Thymeleaf

最终却导入了 106 个 jar 包：

> org.springframework.security:spring-security-rsa:jar:1.0.9.RELEASE:compile
> com.netflix.ribbon: ribbon:jar:2.3.0:compile
> org.springframework.boot:spring-boot-starter-thymeleaf:jar:2.3.6.RELEASE:compile
> commons-configuration:commons-configuration:jar:1.8:compile
> org.apache.logging.log4j:log4j-api:jar:2.13.3:compile
> org.springframework:spring-beans:jar:5.2.11.RELEASE:compile
> org.springframework.cloud:spring-cloud-starter-netflix-ribbon:jar:2.2.6.RELEASE:compile
> org.apache.tomcat.embed:tomcat-embed-websocket:jar:9.0.39:compile
> com.alibaba.cloud:spring-cloud-alibaba-commons:jar:2.2.6.RELEASE:compile
> org.bouncycastle:bcprov-jdk15on:jar:1.64:compile
> org.springframework.security:spring-security-crypto:jar:5.3.5.RELEASE:compile
> org.apache.httpcomponents:httpasyncclient:jar:4.1.4:compile
> com.google.j2objc:j2objc-annotations:jar:1.3:compile
> com.fasterxml.jackson.core:jackson-databind:jar:2.11.3:compile
> io.reactivex:rxjava:jar:1.3.8:compile
> ch.qos.logback:logback-classic:jar:1.2.3:compile
> org.springframework:spring-web:jar:5.2.11.RELEASE:compile
> io.reactivex:rxnetty-servo:jar:0.4.9:runtime
> org.springframework:spring-core:jar:5.2.11.RELEASE:compile
> io.github.openfeign.form:feign-form-spring:jar:3.8.0:compile
> io.github.openfeign.form:feign-form:jar:3.8.0:compile
> com.netflix.ribbon:ribbon-loadbalancer:jar:2.3.0:compile
> org.apache.httpcomponents:httpcore:jar:4.4.13:compile
> org.thymeleaf.extras:thymeleaf-extras-java8time:jar:3.0.4.RELEASE:compile
> org.slf4j:jul-to-slf4j:jar:1.7.30:compile
> com.atguigu.demo:demo09-base-entity:jar:1.0-SNAPSHOT:compile
> org.yaml:snakeyaml:jar:1.26:compile
> org.springframework.boot:spring-boot-starter-logging:jar:2.3.6.RELEASE:compile
> io.reactivex:rxnetty-contexts:jar:0.4.9:runtime
> org.apache.httpcomponents:httpclient:jar:4.5.13:compile
> io.github.openfeign:feign-core:jar:10.10.1:compile
> org.springframework.boot:spring-boot-starter-aop:jar:2.3.6.RELEASE:compile
> org.hdrhistogram:HdrHistogram:jar:2.1.9:compile
> org.springframework:spring-context:jar:5.2.11.RELEASE:compile
> commons-lang:commons-lang:jar:2.6:compile
> io.prometheus:simpleclient:jar:0.5.0:compile
> ch.qos.logback:logback-core:jar:1.2.3:compile
> org.springframework:spring-webmvc:jar:5.2.11.RELEASE:compile
> com.sun.jersey:jersey-core:jar:1.19.1:runtime
> javax.ws.rs:jsr311-api:jar:1.1.1:runtime
> javax.inject:javax.inject:jar:1:runtime
> org.springframework.cloud:spring-cloud-openfeign-core:jar:2.2.6.RELEASE:compile
> com.netflix.ribbon:ribbon-core:jar:2.3.0:compile
> com.netflix.hystrix:hystrix-core:jar:1.5.18:compile
> com.netflix.ribbon:ribbon-transport:jar:2.3.0:runtime
> org.springframework.boot:spring-boot-starter-json:jar:2.3.6.RELEASE:compile
> org.springframework.cloud:spring-cloud-starter-openfeign:jar:2.2.6.RELEASE:compile
> com.fasterxml.jackson.module:jackson-module-parameter-names:jar:2.11.3:compile
> com.sun.jersey.contribs:jersey-apache-client4:jar:1.19.1:runtime
> io.github.openfeign:feign-hystrix:jar:10.10.1:compile
> io.github.openfeign:feign-slf4j:jar:10.10.1:compile
> com.alibaba.nacos:nacos-client:jar:1.4.2:compile
> org.apache.httpcomponents:httpcore-nio:jar:4.4.13:compile
> com.sun.jersey:jersey-client:jar:1.19.1:runtime
> org.springframework.cloud:spring-cloud-context:jar:2.2.6.RELEASE:compile
> org.glassfish:jakarta.el:jar:3.0.3:compile
> org.apache.logging.log4j:log4j-to-slf4j:jar:2.13.3:compile
> com.fasterxml.jackson.datatype:jackson-datatype-jsr310:jar:2.11.3:compile
> org.springframework.cloud:spring-cloud-commons:jar:2.2.6.RELEASE:compile
> org.aspectj:aspectjweaver:jar:1.9.6:compile
> com.alibaba.cloud:spring-cloud-starter-alibaba-nacos-discovery:jar:2.2.6.RELEASE:compile
> com.google.guava:listenablefuture:jar:9999.0-empty-to-avoid-conflict-with-guava:compile
> com.alibaba.spring:spring-context-support:jar:1.0.10:compile
> jakarta.annotation:jakarta.annotation-api:jar:1.3.5:compile
> org.bouncycastle:bcpkix-jdk15on:jar:1.64:compile
> com.netflix.netflix-commons:netflix-commons-util:jar:0.3.0:runtime
> com.fasterxml.jackson.core:jackson-annotations:jar:2.11.3:compile
> com.google.guava:guava:jar:29.0-jre:compile
> com.google.guava:failureaccess:jar:1.0.1:compile
> org.springframework.boot:spring-boot:jar:2.3.6.RELEASE:compile
> com.fasterxml.jackson.datatype:jackson-datatype-jdk8:jar:2.11.3:compile
> com.atguigu.demo:demo08-base-api:jar:1.0-SNAPSHOT:compile
> org.springframework.cloud:spring-cloud-starter-netflix-archaius:jar:2.2.6.RELEASE:compile
> org.springframework.boot:spring-boot-autoconfigure:jar:2.3.6.RELEASE:compile
> org.slf4j:slf4j-api:jar:1.7.30:compile
> commons-io:commons-io:jar:2.7:compile
> org.springframework.cloud:spring-cloud-starter:jar:2.2.6.RELEASE:compile
> org.apache.tomcat.embed:tomcat-embed-core:jar:9.0.39:compile
> io.reactivex:rxnetty:jar:0.4.9:runtime
> com.fasterxml.jackson.core:jackson-core:jar:2.11.3:compile
> com.google.code.findbugs:jsr305:jar:3.0.2:compile
> com.netflix.archaius:archaius-core:jar:0.7.6:compile
> org.springframework.boot:spring-boot-starter-web:jar:2.3.6.RELEASE:compile
> commons-codec:commons-codec:jar:1.14:compile
> com.netflix.servo:servo-core:jar:0.12.21:runtime
> com.google.errorprone:error_prone_annotations:jar:2.3.4:compile
> org.attoparser:attoparser:jar:2.0.5.RELEASE:compile
> com.atguigu.demo:demo10-base-util:jar:1.0-SNAPSHOT:compile
> org.checkerframework:checker-qual:jar:2.11.1:compile
> org.thymeleaf:thymeleaf-spring5:jar:3.0.11.RELEASE:compile
> commons-fileupload:commons-fileupload:jar:1.4:compile
> com.netflix.ribbon:ribbon-httpclient:jar:2.3.0:compile
> com.netflix.netflix-commons:netflix-statistics:jar:0.1.1:runtime
> org.unbescape:unbescape:jar:1.1.6.RELEASE:compile
> org.springframework:spring-jcl:jar:5.2.11.RELEASE:compile
> com.alibaba.nacos:nacos-common:jar:1.4.2:compile
> commons-collections:commons-collections:jar:3.2.2:runtime
> javax.persistence:persistence-api:jar:1.0:compile
> com.alibaba.nacos:nacos-api:jar:1.4.2:compile
> org.thymeleaf:thymeleaf:jar:3.0.11.RELEASE:compile
> org.springframework:spring-aop:jar:5.2.11.RELEASE:compile
> org.springframework.boot:spring-boot-starter:jar:2.3.6.RELEASE:compile
> org.springframework.boot:spring-boot-starter-tomcat:jar:2.3.6.RELEASE:compile
> org.springframework.cloud:spring-cloud-netflix-ribbon:jar:2.2.6.RELEASE:compile
> org.springframework:spring-expression:jar:5.2.11.RELEASE:compile
> org.springframework.cloud:spring-cloud-netflix-archaius:jar:2.2.6.RELEASE:compile

而如果使用 Maven 来引入这些 jar 包只需要配置三个『**依赖**』：

```xml
<!-- Nacos 服务注册发现启动器 -->
    <dependency>
        <groupId>com.alibaba.cloud</groupId>
        <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
    </dependency>

    <!-- web启动器依赖 -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <!-- 视图模板技术 thymeleaf -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-thymeleaf</artifactId>
    </dependency>
```

### ②jar 包的来源

- 这个jar包所属技术的官网。官网通常是英文界面，网站的结构又不尽相同，甚至找到下载链接还发现需要通过特殊的工具下载。
- 第三方网站提供下载。问题是不规范，在使用过程中会出现各种问题。
  - jar包的名称
  - jar包的版本
  - jar包内的具体细节
- 而使用 Maven 后，依赖对应的 jar 包能够**自动下载**，方便、快捷又规范。

③jar 包之间的依赖关系

框架中使用的 jar 包，不仅数量庞大，而且彼此之间存在错综复杂的依赖关系。依赖关系的复杂程度，已经上升到了完全不能靠人力手动解决的程度。另外，jar 包之间有可能产生冲突。进一步增加了我们在 jar 包使用过程中的难度。

下面是前面例子中 jar 包之间的依赖关系：

![jar包之间的依赖关系](.\img\jar包之间的依赖关系.png)

而实际上 jar 包之间的依赖关系是普遍存在的，如果要由程序员手动梳理无疑会增加极高的学习成本，而这些工作又对实现业务功能毫无帮助。

而使用 Maven 则几乎不需要管理这些关系，极个别的地方调整一下即可，极大的减轻了我们的工作量。

## 2、Maven 作为构建管理工具

### ①你没有注意过的构建

你可以不使用 Maven，但是构建必须要做。当我们使用 IDEA 进行开发时，构建是 IDEA 替我们做的。

### ②脱离 IDE 环境仍需构建

![构建](.\img\构建.png)

## 3、结论

- **管理规模庞大的 jar 包，需要专门工具。**
- **脱离 IDE 环境执行构建操作，需要专门工具。**



# 什么是 Maven？

Maven 是 Apache 软件基金会组织维护的一款专门为 Java 项目提供**构建**和**依赖**管理支持的工具。

## 1、构建

Java 项目开发过程中，构建指的是使用**『原材料生产产品』**的过程。

- 原材料

  - Java 源代码

  - 基于 HTML 的 Thymeleaf 文件

  - 图片

  - 配置文件

  - ###### ……

- 产品

  - 一个可以在服务器上运行的项目

构建过程包含的主要的环节：

- 清理：删除上一次构建的结果，为下一次构建做好准备
- 编译：Java 源程序编译成 *.class 字节码文件
- 测试：运行提前准备好的测试程序
- 报告：针对刚才测试的结果生成一个全面的信息
- 打包
  - Java工程：jar包
  - Web工程：war包
- 安装：把一个 Maven 工程经过打包操作生成的 jar 包或 war 包存入 Maven 仓库
- 部署
  - 部署 jar 包：把一个 jar 包部署到 Nexus 私服服务器上
  - 部署 war 包：借助相关 Maven 插件（例如 cargo），将 war 包部署到 Tomcat 服务器上

## 2、依赖

如果 A 工程里面用到了 B 工程的类、接口、配置文件等等这样的资源，那么我们就可以说 A 依赖 B。例如：

- junit-4.12 依赖 hamcrest-core-1.3
- thymeleaf-3.0.12.RELEASE 依赖 ognl-3.1.26
  - ognl-3.1.26 依赖 javassist-3.20.0-GA
- thymeleaf-3.0.12.RELEASE 依赖 attoparser-2.0.5.RELEASE
- thymeleaf-3.0.12.RELEASE 依赖 unbescape-1.1.6.RELEASE
- thymeleaf-3.0.12.RELEASE 依赖 slf4j-api-1.7.26



依赖管理中要解决的具体问题：

- jar 包的下载：使用 Maven 之后，jar 包会从规范的远程仓库下载到本地
- jar 包之间的依赖：通过依赖的传递性自动完成
- jar 包之间的冲突：通过对依赖的配置进行调整，让某些jar包不会被导入

## 3、Maven 的工作机制

![Maven的工作机制](.\img\Maven的工作机制.png)

#  Maven 核心程序解压和配置

## 1、Maven 官网地址

首页：

[Maven – Welcome to Apache Maven(opens new window)](https://maven.apache.org/)

下载页面：

[Maven – Download Apache Maven(opens new window)](https://maven.apache.org/download.cgi)

下载链接：

![FIles](.\img\FIles.png)

具体下载地址：https://dlcdn.apache.org/maven/maven-3/3.8.4/binaries/apache-maven-3.8.4-bin.zip

## 压Maven核心程序

![jar包之间的依赖关系](E:\java\Maven\笔记\img\jar包之间的依赖关系.png)

核心程序压缩包：apache-maven-3.8.4-bin.zip，解压到**非中文、没有空格**的目录。例如：

![核心程序压缩包](.\img\核心程序压缩包.png)

在解压目录中，我们需要着重关注 Maven 的核心配置文件：**conf/settings.xml**

## 3、指定本地仓库

本地仓库默认值：用户家目录/.m2/repository。由于本地仓库的默认位置是在用户的家目录下，而家目录往往是在 C 盘，也就是系统盘。将来 Maven 仓库中 jar 包越来越多，仓库体积越来越大，可能会拖慢 C 盘运行速度，影响系统性能。所以建议将 Maven 的本地仓库放在其他盘符下。配置方式如下：

```xml
<!-- localRepository
| The path to the local repository maven will use to store artifacts.
|
| Default: ${user.home}/.m2/repository
<localRepository>/path/to/local/repo</localRepository>
-->
<localRepository>D:\maven-repository</localRepository>
```

本地仓库这个目录，我们手动创建一个空的目录即可。

**记住**：一定要把 localRepository 标签**从注释中拿出来**。

**注意**：本地仓库本身也需要使用一个**非中文、没有空格**的目录。

## 4、配置阿里云提供的镜像仓库

Maven 下载 jar 包默认访问境外的中央仓库，而国外网站速度很慢。改成阿里云提供的镜像仓库，**访问国内网站**，可以让 Maven 下载 jar 包的时候速度更快。配置的方式是：

### ①将原有的例子配置注释掉

```xml
<!-- <mirror>
  <id>maven-default-http-blocker</id>
  <mirrorOf>external:http:*</mirrorOf>
  <name>Pseudo repository to mirror external repositories initially using HTTP.</name>
  <url>http://0.0.0.0/</url>
  <blocked>true</blocked>
</mirror> -->
```

### ②加入我们的配置

将下面 mirror 标签整体复制到 settings.xml 文件的 mirrors 标签的内部。

```xml
	<mirror>
		<id>nexus-aliyun</id>
		<mirrorOf>central</mirrorOf>
		<name>Nexus aliyun</name>
		<url>http://maven.aliyun.com/nexus/content/groups/public</url>
	</mirror>
```

## 5、配置 Maven 工程的基础 JDK 版本

如果按照默认配置运行，Java 工程使用的默认 JDK 版本是 1.5，而我们熟悉和常用的是 JDK 1.8 版本。修改配置的方式是：将 profile 标签整个复制到 settings.xml 文件的 profiles 标签内。

```xml
	<profile>
	  <id>jdk-1.8</id>
	  <activation>
		<activeByDefault>true</activeByDefault>
		<jdk>1.8</jdk>
	  </activation>
	  <properties>
		<maven.compiler.source>1.8</maven.compiler.source>
		<maven.compiler.target>1.8</maven.compiler.target>
	<maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
	  </properties>
	</profile>
```

# 配置环境变量

## 1、检查 JAVA_HOME 配置是否正确

Maven 是一个用 Java 语言开发的程序，它必须基于 JDK 来运行，需要通过 JAVA_HOME 来找到 JDK 的安装位置。

![JAVA_HOME配置](./img/JAVA_HOME配置.png)

可以使用下面的命令验证：

```shell
C:\Users\Administrator>echo %JAVA_HOME%
D:\software\Java

C:\Users\Administrator>java -version
java version "1.8.0_141"
Java(TM) SE Runtime Environment (build 1.8.0_141-b15)
Java HotSpot(TM) 64-Bit Server VM (build 25.141-b15, mixed mode)
```

## 2、配置 MAVEN_HOME

![MAVEN_HOME配置](./img/MAVEN_HOME配置.png)

TIP

配置环境变量的规律：

XXX_HOME 通常指向的是 bin 目录的上一级

PATH 指向的是 bin 目录

## 3、配置PATH

![PATH配置](./img/PATH配置.png)

## 4、验证

```bash
C:\Users\Administrator>mvn -v
Apache Maven 3.8.4 (9b656c72d54e5bacbed989b64718c159fe39b537)
Maven home: D:\software\apache-maven-3.8.4
Java version: 1.8.0_141, vendor: Oracle Corporation, runtime: D:\software\Java\jre
Default locale: zh_CN, platform encoding: GBK
OS name: "windows 10", version: "10.0", arch: "amd64", family: "windows"
```

# 实验一：根据坐标创建 Maven 工程

## 1、Maven 核心概念：坐标

### ①数学中的坐标

![数学中的坐标](./img/数学中的坐标.png)

使用 x、y、z 三个**『向量』**作为空间的坐标系，可以在**『空间』**中唯一的定位到一个**『点』**。

### ②Maven中的坐标

#### [1]向量说明

使用三个**『向量』**在**『Maven的仓库』**中**唯一**的定位到一个**『jar』**包。

- **groupId**：公司或组织的 id
- **artifactId**：一个项目或者是项目中的一个模块的 id
- **version**：版本号

#### [2]三个向量的取值方式

- groupId：公司或组织域名的倒序，通常也会加上项目名称
  - 例如：com.atguigu.maven
- artifactId：模块的名称，将来作为 Maven 工程的工程名
- version：模块的版本号，根据自己的需要设定
  - 例如：SNAPSHOT 表示快照版本，正在迭代过程中，不稳定的版本
  - 例如：RELEASE 表示正式版本

举例：

- groupId：com.atguigu.maven
- artifactId：pro01-atguigu-maven
- version：1.0-SNAPSHOT

### ③坐标和仓库中 jar 包的存储路径之间的对应关系

坐标：

```xml
  <groupId>javax.servlet</groupId>
  <artifactId>servlet-api</artifactId>
  <version>2.5</version>
```

上面坐标对应的 jar 包在 Maven 本地仓库中的位置：

```text
Maven本地仓库根目录\javax\servlet\servlet-api\2.5\servlet-api-2.5.jar
```

一定要学会根据坐标到本地仓库中找到对应的 jar 包。

## 2、实验操作

### ①创建目录作为后面操作的工作空间

例如：D:\maven-workspace\space201026

WARNING

此时我们已经有了三个目录，分别是：

- Maven 核心程序：中军大帐
- Maven 本地仓库：兵营
- 本地工作空间：战场

### ②在工作空间目录下打开命令行窗口

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img010.7f3addf6.png)

### ③使用命令生成Maven工程

![images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img008.be45c9ad.png)

运行 **mvn archetype:generate** 命令

下面根据提示操作

> TIP
>
> Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): 7:【直接回车，使用默认值】
>
> Define value for property 'groupId': com.lmj.maven
>
> Define value for property 'artifactId': pro01-lmj-java
>
> Define value for property 'version' 1.0-SNAPSHOT: :【直接回车，使用默认值】
>
> Define value for property 'package' com.lmj.maven: :【直接回车，使用默认值】
>
> Confirm properties configuration: groupId: com.lmj.maven artifactId: pro01-maven-java version: 1.0-SNAPSHOT package: com.lmj.maven Y: :【直接回车，表示确认。如果前面有输入错误，想要重新输入，则输入 N 再回车。】

### ④调整

Maven 默认生成的工程，对 junit 依赖的是较低的 3.8.1 版本，我们可以改成较适合的 4.12 版本。

自动生成的 App.java 和 AppTest.java 可以删除。

```xml
<!-- 依赖信息配置 -->
<!-- dependencies复数标签：里面包含dependency单数标签 -->
<dependencies>
	<!-- dependency单数标签：配置一个具体的依赖 -->
	<dependency>
		<!-- 通过坐标来依赖其他jar包 -->
		<groupId>junit</groupId>
		<artifactId>junit</artifactId>
		<version>4.12</version>
		
		<!-- 依赖的范围 -->
		<scope>test</scope>
	</dependency>
</dependencies>
```

### ⑤自动生成的 pom.xml 解读

```xml
  <!-- 当前Maven工程的坐标 -->
  <groupId>com.atguigu.maven</groupId>
  <artifactId>pro01-maven-java</artifactId>
  <version>1.0-SNAPSHOT</version>
  
  <!-- 当前Maven工程的打包方式，可选值有下面三种： -->
  <!-- jar：表示这个工程是一个Java工程  -->
  <!-- war：表示这个工程是一个Web工程 -->
  <!-- pom：表示这个工程是“管理其他工程”的工程 -->
  <packaging>jar</packaging>

  <name>pro01-maven-java</name>
  <url>http://maven.apache.org</url>

  <properties>
	<!-- 工程构建过程中读取源码时使用的字符集 -->
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  </properties>

  <!-- 当前工程所依赖的jar包 -->
  <dependencies>
	<!-- 使用dependency配置一个具体的依赖 -->
    <dependency>
	
	  <!-- 在dependency标签内使用具体的坐标依赖我们需要的一个jar包 -->
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.12</version>
	  
	  <!-- scope标签配置依赖的范围 -->
      <scope>test</scope>
    </dependency>
  </dependencies>
```

## 3、Maven核心概念：POM

### ①含义

POM：**P**roject **O**bject **M**odel，项目对象模型。和 POM 类似的是：DOM（Document Object Model），文档对象模型。它们都是模型化思想的具体体现。

### ②模型化思想

POM 表示将工程抽象为一个模型，再用程序中的对象来描述这个模型。这样我们就可以用程序来管理项目了。我们在开发过程中，最基本的做法就是将现实生活中的事物抽象为模型，然后封装模型相关的数据作为一个对象，这样就可以在程序中计算与现实事物相关的数据。

### ③对应的配置文件

POM 理念集中体现在 Maven 工程根目录下 **pom.xml** 这个配置文件中。所以这个 pom.xml 配置文件就是 Maven 工程的核心配置文件。其实学习 Maven 就是学这个文件怎么配置，各个配置有什么用。

## 4、Maven核心概念：约定的目录结构

### ①各个目录的作用

![约定的目录结构](./img/约定的目录结构.png)

另外还有一个 target 目录专门存放构建操作输出的结果。

### ②约定目录结构的意义

Maven 为了让构建过程能够尽可能自动化完成，所以必须约定目录结构的作用。例如：Maven 执行编译操作，必须先去 Java 源程序目录读取 Java 源代码，然后执行编译，最后把编译结果存放在 target 目录。

### ③约定大于配置

Maven 对于目录结构这个问题，没有采用配置的方式，而是基于约定。这样会让我们在开发过程中非常方便。如果每次创建 Maven 工程后，还需要针对各个目录的位置进行详细的配置，那肯定非常麻烦。

目前开发领域的技术发展趋势就是：约定大于配置，配置大于编码。

# 第二节 实验二：在 Maven 工程中编写代码

## 1、主体程序

![约定的目录结构](./img/约定的目录结构.png)

主体程序指的是被测试的程序，同时也是将来在项目中真正要使用的程序。

```java
package com.lmj.maven;
public class Calculator {
	public int sum(int i, int j){
		return i + j;
	}
}
```

##  2、测试程序

![测试程序](img/测试程序.png)

```java
package com.atguigu.maven;
import org.junit.Test;
import com.atguigu.maven.Calculator;
// 静态导入的效果是将Assert类中的静态资源导入当前类
// 这样一来，在当前类中就可以直接使用Assert类中的静态资源，不需要写类名
import static org.junit.Assert.*;
public class CalculatorTest{
	@Test
	public void testSum(){
		// 1.创建Calculator对象
		Calculator calculator = new Calculator();
		// 2.调用Calculator对象的方法，获取到程序运行实际的结果
		int actualResult = calculator.sum(5, 3);
		// 3.声明一个变量，表示程序运行期待的结果
		int expectedResult = 8;
		// 4.使用断言来判断实际结果和期待结果是否一致
		// 如果一致：测试通过，不会抛出异常
		// 如果不一致：抛出异常，测试失败
		assertEquals(expectedResult, actualResult);
	}
}
```

# 实验三：执行 Maven 的构建命令

## 1、要求

运行 Maven 中和构建操作相关的命令时，必须进入到 pom.xml 所在的目录。如果没有在 pom.xml 所在的目录运行 Maven 的构建命令，那么会看到下面的错误信息：

```java
The goal you specified requires a project to execute but there is no POM in this directory
```

> TIP
>
> mvn -v 命令和构建操作无关，只要正确配置了 PATH，在任何目录下执行都可以。而构建相关的命令要在 pom.xml 所在目录下运行——操作哪个工程，就进入这个工程的 pom.xml 目录。

## 2、清理操作

mvn clean

效果：删除 target 目录

## 3、编译操作

主程序编译：mvn compile

测试程序编译：mvn test-compile

主体程序编译结果存放的目录：target/classes

测试程序编译结果存放的目录：target/test-classes

## 4、测试操作

mvn test

测试的报告存放的目录：target/surefire-reports

## 5、打包操作

mvn package

打包的结果——jar 包，存放的目录：target

## 6、安装操作

mvn install

```log
[INFO] Installing D:\maven-workspace\space201026\pro01-maven-java\target\pro01-maven-java-1.0-SNAPSHOT.jar to D:\maven-rep1026\com\atguigu\maven\pro01-maven-java\1.0-SNAPSHOT\pro01-maven-java-1.0-SNAPSHOT.jar
[INFO] Installing D:\maven-workspace\space201026\pro01-maven-java\pom.xml to D:\maven-rep1026\com\atguigu\maven\pro01-maven-java\1.0-SNAPSHOT\pro01-maven-java-1.0-SNAPSHOT.pom
```

安装的效果是将本地构建过程中生成的 jar 包存入 Maven 本地仓库。这个 jar 包在 Maven 仓库中的路径是根据它的坐标生成的。

坐标信息如下：

```xml
  <groupId>com.atguigu.maven</groupId>
  <artifactId>pro01-maven-java</artifactId>
  <version>1.0-SNAPSHOT</version>
```

在 Maven 仓库中生成的路径如下：

```log
D:\maven-rep1026\com\atguigu\maven\pro01-maven-java\1.0-SNAPSHOT\pro01-maven-java-1.0-SNAPSHOT.jar
```

另外，安装操作还会将 pom.xml 文件转换为 XXX.pom 文件一起存入本地仓库。所以我们在 Maven 的本地仓库中想看一个 jar 包原始的 pom.xml 文件时，查看对应 XXX.pom 文件即可，它们是名字发生了改变，本质上是同一个文件。

# 实验四：创建 Maven 版的 Web 工程

## 1、说明

使用 mvn archetype:generate 命令生成 Web 工程时，需要使用一个专门的 archetype。这个专门生成 Web 工程骨架的 archetype 可以参照官网看到它的用法：

![web工程骨架](img/web工程骨架.png)

参数 archetypeGroupId、archetypeArtifactId、archetypeVersion 用来指定现在使用的 maven-archetype-webapp 的坐标。

## 2、操作

注意：如果在上一个工程的目录下执行 mvn archetype:generate 命令，那么 Maven 会报错：不能在一个非 pom 的工程下再创建其他工程。所以不要再刚才创建的工程里再创建新的工程，**请回到工作空间根目录**来操作。

然后运行生成工程的命令：

```log
mvn archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-webapp -DarchetypeVersion=1.4
```

下面的操作按照提示执行：

> TIP
>
> Define value for property 'groupId': com.atguigu.maven Define value for property 'artifactId': pro02-maven-web Define value for property 'version' 1.0-SNAPSHOT: :【直接回车，使用默认值】
>
> Define value for property 'package' com.atguigu.maven: :【直接回车，使用默认值】 Confirm properties configuration: groupId: com.atguigu.maven artifactId: pro02-maven-web version: 1.0-SNAPSHOT package: com.atguigu.maven Y: :【直接回车，表示确认】

## 3、生成的pom.xml

确认打包的方式是war包形式

```xml
<packaging>war</packaging>
```

## 4、生成的Web工程的目录结构

![Web工程目录结构](img/Web工程目录结构.png)

webapp 目录下有 index.jsp

WEB-INF 目录下有 web.xml

## 5、创建 Servlet

### ①在 main 目录下创建 java 目录

![main目录下创建Java目录](img/main目录下创建Java目录.png)

### ②在 java 目录下创建 Servlet 类所在的包的目录

![创建Servlet类所在目录](img/创建Servlet类所在目录.png)

### ③在包下创建 Servlet 类

```java
package com.atguigu.maven;
	
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.ServletException;
import java.io.IOException;
	
public class HelloServlet extends HttpServlet{
	
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		
		response.getWriter().write("hello maven web");
		
	}
}
```

### ④在 web.xml 中注册 Servlet

```xml
  <servlet>
	<servlet-name>helloServlet</servlet-name>
	<servlet-class>com.atguigu.maven.HelloServlet</servlet-class>
  </servlet>
  <servlet-mapping>
	<servlet-name>helloServlet</servlet-name>
	<url-pattern>/helloServlet</url-pattern>
  </servlet-mapping>
```

## 6、在 index.jsp 页面编写超链接

```html
<html>
<body>
<h2>Hello World!</h2>
<a href="helloServlet">Access Servlet</a>
</body>
</html>
```

> TIP
>
> JSP全称是 Java Server Page，和 Thymeleaf 一样，是服务器端页面渲染技术。这里我们不必关心 JSP 语法细节，编写一个超链接标签即可。

## 7、编译

> 此时直接执行 mvn compile 命令出错：
>
> DANGER
>
> 程序包 javax.servlet.http 不存在
>
> 程序包 javax.servlet 不存在
>
> 找不到符号
>
> 符号: 类 HttpServlet
>
> ……

上面的错误信息说明：我们的 Web 工程用到了 HttpServlet 这个类，而 HttpServlet 这个类属于 servlet-api.jar 这个 jar 包。此时我们说，Web 工程需要依赖 servlet-api.jar 包。

![Web工程依赖](img/Web工程依赖.png)

## 8、配置对 servlet-api.jar 包的依赖

对于不知道详细信息的依赖可以到https://mvnrepository.com/网站查询。使用关键词搜索，然后在搜索结果列表中选择适合的使用。

![配置servlet-api.jar](img/配置servlet-api.jar.png)

比如，我们找到的 servlet-api 的依赖信息：

```xml
<!-- https://mvnrepository.com/artifact/javax.servlet/javax.servlet-api -->
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>javax.servlet-api</artifactId>
    <version>3.1.0</version>
    <scope>provided</scope>
</dependency>
```

## 9、将 Web 工程打包为 war 包

运行 mvn package 命令，生成 war 包的位置如下图所示：

![打包成war包](img/打包成war包.png)

## 10、将 war 包部署到 Tomcat 上运行

将 war 包复制到 Tomcat/webapps 目录下

![将war包部署到Tomcat上](img/将war包部署到Tomcat上.png)

启动 Tomcat,并加war把放入 webapps目录下

![Tomcat自动解压war包](img/Tomcat自动解压war包.png)

# 实验五：让 Web 工程依赖 Java 工程

## 1、观念

明确一个意识：从来只有 Web 工程依赖 Java 工程，没有反过来 Java 工程依赖 Web 工程。本质上来说，Web 工程依赖的 Java 工程其实就是 Web 工程里导入的 jar 包。最终 Java 工程会变成 jar 包，放在 Web 工程的 WEB-INF/lib 目录下。

## 2、操作

在 pro02-maven-web 工程的 pom.xml 中，找到 dependencies 标签，在 dependencies 标签中做如下配置：

```xml
<!-- 配置对Java工程pro01-maven-java的依赖 -->
<!-- 具体的配置方式：在dependency标签内使用坐标实现依赖 -->
<dependency>
	<groupId>com.atguigu.maven</groupId>
	<artifactId>pro01-maven-java</artifactId>
	<version>1.0-SNAPSHOT</version>
</dependency>
```

## 3、在 Web 工程中，编写测试代码

### ①补充创建目录

pro02-maven-web**\src\test\java\com\atguigu\maven**

### ②确认 Web 工程依赖了 junit

```xml
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.12</version>
      <scope>test</scope>
    </dependency>
```

### ③创建测试类

把 Java 工程的 CalculatorTest.java 类复制到 pro02-maven-wb**\src\test\java\com\atguigu\maven** 目录下

## 4、执行Maven命令

### ①测试命令

mvn test

说明：测试操作中会提前自动执行编译操作，测试成功就说明编译也是成功的。

### ②打包命令

mvn package

![war的解压目录](img/war的解压目录.png)

通过查看 war 包内的结构，我们看到被 Web 工程依赖的 Java 工程确实是会变成 Web 工程的 WEB-INF/lib 目录下的 jar 包。

![WEB-INF-lib目录下的jar包](img/WEB-INF-lib目录下的jar包.png)

### ③查看当前 Web 工程所依赖的 jar 包的列表

mvn dependency:list

> TIP
>
> [INFO] The following files have been resolved:
> [INFO] org.hamcrest:hamcrest-core:jar:1.3:test
> [INFO] javax.servlet:javax.servlet-api:jar:3.1.0:provided
> [INFO] com.atguigu.maven:pro01-maven-java:jar:1.0-SNAPSHOT:compile
> [INFO] junit:junit:jar:4.12:test

说明：javax.servlet:javax.servlet-api:jar:3.1.0:provided 格式显示的是一个 jar 包的坐标信息。格式是：

> TIP
>
> groupId:artifactId:打包方式:version:依赖的范围

这样的格式虽然和我们 XML 配置文件中坐标的格式不同，但是本质上还是坐标信息，大家需要能够认识这样的格式，将来从 Maven 命令的日志或错误信息中看到这样格式的信息，就能够识别出来这是坐标。进而根据坐标到Maven 仓库找到对应的jar包，用这样的方式解决我们遇到的报错的情况。

### ④以树形结构查看当前 Web 工程的依赖信息

mvn dependency:tree

> TIP
>
> [INFO] com.atguigu.maven:pro02-maven-web:war:1.0-SNAPSHOT
> [INFO] +- junit:junit:jar:4.12:test
> [INFO] | \- org.hamcrest:hamcrest-core:jar:1.3:test
> [INFO] +- javax.servlet:javax.servlet-api:jar:3.1.0:provided
> [INFO] \- com.atguigu.maven:pro01-maven-java:jar:1.0-SNAPSHOT:compile

我们在 pom.xml 中并没有依赖 hamcrest-core，但是它却被加入了我们依赖的列表。原因是：junit 依赖了hamcrest-core，然后基于依赖的传递性，hamcrest-core 被传递到我们的工程了。

# 实验六：测试依赖的范围

## 1、依赖范围

标签的位置：dependencies/dependency/**scope**

标签的可选值：**compile**/**test**/**provided**/system/runtime/**import**

### ①compile 和 test 对比

|         | main目录（空间） | test目录（空间） | 开发过程（时间） | 部署到服务器（时间） |
| ------- | ---------------- | ---------------- | ---------------- | -------------------- |
| compile | 有效             | 有效             | 有效             | 有效                 |
| test    | 无效             | 有效             | 有效             | 无效                 |

### ②compile 和 provided 对比

|          | main目录（空间） | test目录（空间） | 开发过程（时间） | 部署到服务器（时间） |
| -------- | ---------------- | ---------------- | ---------------- | -------------------- |
| compile  | 有效             | 有效             | 有效             | 有效                 |
| provided | 有效             | 有效             | 有效             | 无效                 |

### ③结论

compile：通常使用的第三方框架的 jar 包这样在项目实际运行时真正要用到的 jar 包都是以 compile 范围进行依赖的。比如 SSM 框架所需jar包。

test：测试过程中使用的 jar 包，以 test 范围依赖进来。比如 junit。

provided：在开发过程中需要用到的“服务器上的 jar 包”通常以 provided 范围依赖进来。比如 servlet-api、jsp-api。而这个范围的 jar 包之所以不参与部署、不放进 war 包，就是避免和服务器上已有的同类 jar 包产生冲突，同时减轻服务器的负担。说白了就是：“**服务器上已经有了，你就别带啦！**”

## 2、测试

### ①验证 compile 范围对 main 目录有效

> TIP
>
> main目录下的类：HelloServlet 使用compile范围导入的依赖：pro01-atguigu-maven
>
> 验证：使用compile范围导入的依赖对main目录下的类来说是有效的
>
> 有效：HelloServlet 能够使用 pro01-atguigu-maven 工程中的 Calculator 类
>
> 验证方式：在 HelloServlet 类中导入 Calculator 类，然后编译就说明有效。

### ②验证test范围对main目录无效

测试方式：在主体程序中导入org.junit.Test这个注解，然后执行编译。

具体操作：在pro01-maven-java\src\main\java\com\atguigu\maven目录下修改Calculator.java

```java
package com.atguigu.maven;
import org.junit.Test;

public class Calculator {
	public int sum(int i, int j){
		return i + j;
	}
}
```

执行Maven编译命令：

```java
[ERROR] /D:/maven-workspace/space201026/pro01-maven-java/src/main/java/com/atguigu/maven/Calculator.java:[3,17] 程序包org.junit不存在
```

### ③验证test和provided范围不参与服务器部署

其实就是验证：通过compile范围依赖的jar包会放入war包，通过test范围依赖的jar包不会放入war包。

# 实验七：测试依赖的传递性

## 1、依赖的传递性

### ①概念

A 依赖 B，B 依赖 C，那么在 A 没有配置对 C 的依赖的情况下，A 里面能不能直接使用 C？

### ②传递的原则

在 A 依赖 B，B 依赖 C 的前提下，C 是否能够传递到 A，取决于 B 依赖 C 时使用的依赖范围。

- B 依赖 C 时使用 compile 范围：可以传递
- B 依赖 C 时使用 test 或 provided 范围：不能传递，所以需要这样的 jar 包时，就必须在需要的地方明确配置依赖才可以。

## 2、使用 compile 范围依赖 spring-core

测试方式：让 pro01-maven-java 工程依赖 spring-core

具体操作：编辑 pro01-maven-java 工程根目录下 pom.xml

```xml
<!-- https://mvnrepository.com/artifact/org.springframework/spring-core -->
<dependency>
	<groupId>org.springframework</groupId>
	<artifactId>spring-core</artifactId>
	<version>4.0.0.RELEASE</version>
</dependency>
```

使用 mvn dependency:tree 命令查看效果：

> TIP
>
> [INFO] com.atguigu.maven:pro01-maven-java:jar:1.0-SNAPSHOT
> [INFO] +- junit:junit:jar:4.12:test
> [INFO] | \- org.hamcrest:hamcrest-core:jar:1.3:test
> [INFO] \- org.springframework:spring-core:jar:4.0.0.RELEASE:compile
> [INFO] \- commons-logging:commons-logging:jar:1.1.1:compile

还可以在 Web 工程中，使用 mvn dependency:tree 命令查看效果（需要重新将 pro01-maven-java 安装到仓库）：

> TIP
>
> [INFO] com.atguigu.maven:pro02-maven-web:war:1.0-SNAPSHOT
> [INFO] +- junit:junit:jar:4.12:test
> [INFO] | \- org.hamcrest:hamcrest-core:jar:1.3:test
> [INFO] +- javax.servlet:javax.servlet-api:jar:3.1.0:provided
> [INFO] \- com.atguigu.maven:pro01-maven-java:jar:1.0-SNAPSHOT:compile
> [INFO] \- org.springframework:spring-core:jar:4.0.0.RELEASE:compile
> [INFO] \- commons-logging:commons-logging:jar:1.1.1:compile

## 3、验证 test 和 provided 范围不能传递

从上面的例子已经能够看到，pro01-maven-java 依赖了 junit，但是在 pro02-maven-web 工程中查看依赖树的时候并没有看到 junit。

要验证 provided 范围不能传递，可以在 pro01-maven-java 工程中加入 servlet-api 的依赖。

```xml
<dependency>
	<groupId>javax.servlet</groupId>
	<artifactId>javax.servlet-api</artifactId>
	<version>3.1.0</version>
	<scope>provided</scope>
</dependency>
```

效果还是和之前一样：

> TIP
>
> [INFO] com.atguigu.maven:pro02-maven-web:war:1.0-SNAPSHOT
> [INFO] +- junit:junit:jar:4.12:test
> [INFO] | \- org.hamcrest:hamcrest-core:jar:1.3:test
> [INFO] +- javax.servlet:javax.servlet-api:jar:3.1.0:provided
> [INFO] \- com.atguigu.maven:pro01-maven-java:jar:1.0-SNAPSHOT:compile
> [INFO] \- org.springframework:spring-core:jar:4.0.0.RELEASE:compile
> [INFO] \- commons-logging:commons-logging:jar:1.1.1:compile

# 第八节 实验八：测试依赖的排除

## 1、概念

当 A 依赖 B，B 依赖 C 而且 C 可以传递到 A 的时候，A 不想要 C，需要在 A 里面把 C 排除掉。而往往这种情况都是为了避免 jar 包之间的冲突。

![依赖冲突](img/依赖冲突.png)

所以配置依赖的排除其实就是阻止某些 jar 包的传递。因为这样的 jar 包传递过来会和其他 jar 包冲突。

## 2、配置方式

```xml
<dependency>
	<groupId>com.atguigu.maven</groupId>
	<artifactId>pro01-maven-java</artifactId>
	<version>1.0-SNAPSHOT</version>
	<scope>compile</scope>
	<!-- 使用excludes标签配置依赖的排除	-->
	<exclusions>
		<!-- 在exclude标签中配置一个具体的排除 -->
		<exclusion>
			<!-- 指定要排除的依赖的坐标（不需要写version） -->
			<groupId>commons-logging</groupId>
			<artifactId>commons-logging</artifactId>
		</exclusion>
	</exclusions>
</dependency>
```

## 3、测试

测试的方式：在 pro02-maven-web 工程中配置对 commons-logging 的排除

```xml
<dependency>
	<groupId>com.atguigu.maven</groupId>
	<artifactId>pro01-maven-java</artifactId>
	<version>1.0-SNAPSHOT</version>
	<scope>compile</scope>
	<!-- 使用excludes标签配置依赖的排除	-->
	<exclusions>
		<!-- 在exclude标签中配置一个具体的排除 -->
		<exclusion>
			<!-- 指定要排除的依赖的坐标（不需要写version） -->
			<groupId>commons-logging</groupId>
			<artifactId>commons-logging</artifactId>
		</exclusion>
	</exclusions>
</dependency>
```

运行 mvn dependency:tree 命令查看效果：

> TIP
>
> [INFO] com.atguigu.maven:pro02-maven-web:war:1.0-SNAPSHOT
> [INFO] +- junit:junit:jar:4.12:test
> [INFO] | \- org.hamcrest:hamcrest-core:jar:1.3:test
> [INFO] +- javax.servlet:javax.servlet-api:jar:3.1.0:provided
> [INFO] \- com.atguigu.maven:pro01-maven-java:jar:1.0-SNAPSHOT:compile
> [INFO] \- org.springframework:spring-core:jar:4.0.0.RELEASE:compile

发现在 spring-core 下面就没有 commons-logging 了。

# 第九节 实验九：继承

## 1、概念

Maven工程之间，A 工程继承 B 工程

- B 工程：父工程
- A 工程：子工程

本质上是 A 工程的 pom.xml 中的配置继承了 B 工程中 pom.xml 的配置。

## 2、作用

在父工程中统一管理项目中的依赖信息，具体来说是管理依赖信息的版本。

它的背景是：

- 对一个比较大型的项目进行了模块拆分。
- 一个 project 下面，创建了很多个 module。
- 每一个 module 都需要配置自己的依赖信息。

它背后的需求是：

- 在每一个 module 中各自维护各自的依赖信息很容易发生出入，不易统一管理。
- 使用同一个框架内的不同 jar 包，它们应该是同一个版本，所以整个项目中使用的框架版本需要统一。
- 使用框架时所需要的 jar 包组合（或者说依赖信息组合）需要经过长期摸索和反复调试，最终确定一个可用组合。这个耗费很大精力总结出来的方案不应该在新的项目中重新摸索。

通过在父工程中为整个项目维护依赖信息的组合既**保证了整个项目使用规范、准确的 jar 包**；又能够将**以往的经验沉淀**下来，节约时间和精力。

## 3、举例

在一个工程中依赖多个 Spring 的 jar 包

> TIP
>
> [INFO] +- org.springframework:**spring-core**:jar:**4.0.0**.RELEASE:compile
> [INFO] | \- commons-logging:commons-logging:jar:1.1.1:compile
> [INFO] +- org.springframework:**spring-beans**:jar:**4.0.0**.RELEASE:compile
> [INFO] +- org.springframework:**spring-context**:jar:**4.0.0**.RELEASE:compile
> [INFO] +- org.springframework:**spring-expression**:jar:4.0.0.RELEASE:compile
> [INFO] +- org.springframework:**spring-aop**:jar:**4.0.0**.RELEASE:compile
> [INFO] | \- aopalliance:aopalliance:jar:1.0:compile

使用 Spring 时要求所有 Spring 自己的 jar 包版本必须一致。为了能够对这些 jar 包的版本进行统一管理，我们使用继承这个机制，将所有版本信息统一在父工程中进行管理。

## 4、操作

### ①创建父工程

创建的过程和前面创建 pro01-maven-java 一样。

工程名称：pro03-maven-parent

工程创建好之后，要修改它的打包方式：

```xml
  <groupId>com.atguigu.maven</groupId>
  <artifactId>pro03-maven-parent</artifactId>
  <version>1.0-SNAPSHOT</version>

  <!-- 当前工程作为父工程，它要去管理子工程，所以打包方式必须是 pom -->
  <packaging>pom</packaging>
```

只有打包方式为 pom 的 Maven 工程能够管理其他 Maven 工程。打包方式为 pom 的 Maven 工程中不写业务代码，它是专门管理其他 Maven 工程的工程。

### ②创建模块工程

模块工程类似于 IDEA 中的 module，所以需要**进入 pro03-maven-parent 工程的根目录**，然后运行 mvn archetype:generate 命令来创建模块工程。

假设，我们创建三个模块工程：

![模块工程](img/模块工程.png)

### ③查看被添加新内容的父工程 pom.xml

下面 modules 和 module 标签是聚合功能的配置

```xml
<modules>  
	<module>pro04-maven-module</module>
	<module>pro05-maven-module</module>
	<module>pro06-maven-module</module>
</modules>
```

### ④解读子工程的pom.xml

```xml
<!-- 使用parent标签指定当前工程的父工程 -->
<parent>
	<!-- 父工程的坐标 -->
	<groupId>com.atguigu.maven</groupId>
	<artifactId>pro03-maven-parent</artifactId>
	<version>1.0-SNAPSHOT</version>
</parent>

<!-- 子工程的坐标 -->
<!-- 如果子工程坐标中的groupId和version与父工程一致，那么可以省略 -->
<!-- <groupId>com.atguigu.maven</groupId> -->
<artifactId>pro04-maven-module</artifactId>
<!-- <version>1.0-SNAPSHOT</version> -->
13
```

### ⑤在父工程中配置依赖的统一管理

```xml
<!-- 使用dependencyManagement标签配置对依赖的管理 -->
<!-- 被管理的依赖并没有真正被引入到工程 -->
<dependencyManagement>
	<dependencies>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-core</artifactId>
			<version>4.0.0.RELEASE</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-beans</artifactId>
			<version>4.0.0.RELEASE</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-context</artifactId>
			<version>4.0.0.RELEASE</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-expression</artifactId>
			<version>4.0.0.RELEASE</version>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-aop</artifactId>
			<version>4.0.0.RELEASE</version>
		</dependency>
	</dependencies>
</dependencyManagement>
```

### ⑥子工程中引用那些被父工程管理的依赖

关键点：省略版本号

```xml
<!-- 子工程引用父工程中的依赖信息时，可以把版本号去掉。	-->
<!-- 把版本号去掉就表示子工程中这个依赖的版本由父工程决定。 -->
<!-- 具体来说是由父工程的dependencyManagement来决定。 -->
<dependencies>
	<dependency>
		<groupId>org.springframework</groupId>
		<artifactId>spring-core</artifactId>
	</dependency>
	<dependency>
		<groupId>org.springframework</groupId>
		<artifactId>spring-beans</artifactId>
	</dependency>
	<dependency>
		<groupId>org.springframework</groupId>
		<artifactId>spring-context</artifactId>
	</dependency>
	<dependency>
		<groupId>org.springframework</groupId>
		<artifactId>spring-expression</artifactId>
	</dependency>
	<dependency>
		<groupId>org.springframework</groupId>
		<artifactId>spring-aop</artifactId>
	</dependency>
</dependencies>
```

### ⑦在父工程中升级依赖信息的版本

```xml
……
			<dependency>
				<groupId>org.springframework</groupId>
				<artifactId>spring-beans</artifactId>
				<version>4.1.4.RELEASE</version>
			</dependency>
……
```

然后在子工程中运行mvn dependency:list，效果如下：

> TIP
>
> [INFO] org.springframework:spring-aop:jar:4.1.4.RELEASE:compile
> [INFO] org.springframework:spring-core:jar:4.1.4.RELEASE:compile
> [INFO] org.springframework:spring-context:jar:4.1.4.RELEASE:compile
> [INFO] org.springframework:spring-beans:jar:4.1.4.RELEASE:compile
> [INFO] org.springframework:spring-expression:jar:4.1.4.RELEASE:compile

### ⑧在父工程中声明自定义属性

```xml
<!-- 通过自定义属性，统一指定Spring的版本 -->
<properties>
	<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
	
	<!-- 自定义标签，维护Spring版本数据 -->
	<atguigu.spring.version>4.3.6.RELEASE</atguigu.spring.version>
</properties>
```

在需要的地方使用${}的形式来引用自定义的属性名：

```xml
			<dependency>
				<groupId>org.springframework</groupId>
				<artifactId>spring-core</artifactId>
				<version>${atguigu.spring.version}</version>
			</dependency>
```

真正实现“一处修改，处处生效”。

![实际意义](img/实际意义.png)

编写一套符合要求、开发各种功能都能正常工作的依赖组合并不容易。如果公司里已经有人总结了成熟的组合方案，那么再开发新项目时，如果不使用原有的积累，而是重新摸索，会浪费大量的时间。为了提高效率，我们可以使用工程继承的机制，让成熟的依赖组合方案能够保留下来。

如上图所示，公司级的父工程中管理的就是成熟的依赖组合方案，各个新项目、子系统各取所需即可。

# 实验十：聚合

## 1、聚合本身的含义

部分组成整体

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img029.48831f65.jpg)

动画片《战神金刚》中的经典台词：“我来组成头部！我来组成手臂！”就是聚合关系最生动的体现。

## 2、Maven 中的聚合

使用一个“总工程”将各个“模块工程”汇集起来，作为一个整体对应完整的项目。

- 项目：整体
- 模块：部分



> TIP
>
> 概念的对应关系：
>
> 从继承关系角度来看：
>
> - 父工程
> - 子工程
>
> 从聚合关系角度来看：
>
> - 总工程
> - 模块工程

## 3、好处

- 一键执行 Maven 命令：很多构建命令都可以在“总工程”中一键执行。

  以 mvn install 命令为例：Maven 要求有父工程时先安装父工程；有依赖的工程时，先安装被依赖的工程。我们自己考虑这些规则会很麻烦。但是工程聚合之后，在总工程执行 mvn install 可以一键完成安装，而且会自动按照正确的顺序执行。

- 配置聚合之后，各个模块工程会在总工程中展示一个列表，让项目中的各个模块一目了然。

## 4、聚合的配置

在总工程中配置 modules 即可：

```xml
	<modules>  
		<module>pro04-maven-module</module>
		<module>pro05-maven-module</module>
		<module>pro06-maven-module</module>
	</modules>
```

## 5、依赖循环问题

如果 A 工程依赖 B 工程，B 工程依赖 C 工程，C 工程又反过来依赖 A 工程，那么在执行构建操作时会报下面的错误：

> DANGER
>
> [ERROR] [ERROR] The projects in the reactor contain a cyclic reference:

这个错误的含义是：循环引用。



# IDEA创建父工程

## 1、创建 Project

![NewProject](img/NewProject.png)

## 2、开启自动导入

创建 Project 后，IDEA 会自动弹出下面提示，我们选择**『Enable Auto-Import』**，意思是启用自动导入。

![自动导入](img/自动导入.png)

这个自动导入**一定要开启**，因为 Project、Module 新创建或 pom.xml 每次修改时都应该让 IDEA 重新加载 Maven 信息。这对 Maven 目录结构认定、Java 源程序编译、依赖 jar 包的导入都有非常关键的影响。

另外也可以通过 IDEA 的 Settings 设置来开启：

![自动导入设置](img/自动导入设置.png)

# 配置Maven信息

每次创建 Project 后都需要设置 Maven 家目录位置，否则 IDEA 将使用内置的 Maven 核心程序（不稳定）并使用默认的本地仓库位置。这样一来，我们在命令行操作过程中已下载好的 jar 包就白下载了，默认的本地仓库通常在 C 盘，还影响系统运行。

配置之后，IDEA 会根据我们在这里指定的 Maven 家目录自动识别到我们在 settings.xml 配置文件中指定的本地仓库。

![配置Maven信息](img/配置Maven信息.png)

# 创建Java模块工程

![创建Java模块工程1](img/创建Java模块工程1.png)

![创建Java模块工程2](img/创建Java模块工程2.png)

# 创建Web模块工程

## 1、创建模块

按照前面的同样操作创建模块，**此时**这个模块其实还是一个**Java模块**。

## 2、修改打包方式

Web 模块将来打包当然应该是 **war** 包。

```xml
<packaging>war</packaging>
```

## 3、Web 设定

首先打开项目结构菜单：

![web项目结构菜单](img/web项目结构菜单.png)

然后到 Facets 下查看 IDEA 是否已经帮我们自动生成了 Web 设定。正常来说只要我们确实设置了打包方式为 war，那么 IDEA 2019 版就会自动生成 Web 设定。

![Web设定](img/Web设定.png)

## 4、借助IDEA生成web.xml

![修改web.xml生成位置](img/修改web.xml生成位置.png)

![按照Maven工程的目录结构设置](img/按照Maven工程的目录结构设置.png)

## 5、设置 Web 资源的根目录

结合 Maven 的目录结构，Web 资源的根目录需要设置为 src/main/webapp 目录。

![设置Web资源根目录](img/设置Web资源根目录.png)

# 其他操作

## 1、在IDEA中执行Maven命令

### ①直接执行

![IDEA执行Maven命令](img/IDEA执行Maven命令.png)

### ②手动输入

![images](data:image/png;base64,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)

![images](data:image/png;base64,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)

![images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img029.7b9c7a12.png)

![images](data:image/png;base64,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)

如果有需要，还可以给命令后面附加参数：

![images](data:image/png;base64,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)

```sh
# -D 表示后面要附加命令的参数，字母 D 和后面的参数是紧挨着的，中间没有任何其它字符
# maven.test.skip=true 表示在执行命令的过程中跳过测试
mvn clean install -Dmaven.test.skip=true
```

## 2、在IDEA中查看某个模块的依赖信息

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img041.c804be73.png)

## 3、工程导入

Maven工程除了自己创建的，还有很多情况是别人创建的。而为了参与开发或者是参考学习，我们都需要导入到 IDEA 中。下面我们分几种不同情况来说明：

### ①来自版本控制系统

目前我们通常使用的都是 Git（本地库） + 码云（远程库）的版本控制系统，结合 IDEA 的相关操作方式请点[**这里** (opens new window)](http://heavy_code_industry.gitee.io/code_heavy_industry/pro008-Git/lecture/chapter05/verse03.html)查看**克隆远程库**部分。

### ②来自工程目录

直接使用 IDEA 打开工程目录即可。下面咱们举个例子：

#### [1]工程压缩包

假设别人发给我们一个 Maven 工程的 zip 压缩包：maven-rest-demo.zip。从码云或GitHub上也可以以 ZIP 压缩格式对项目代码打包下载。

#### [2]解压

如果你的所有 IDEA 工程有一个专门的目录来存放，而不是散落各处，那么首先我们就把 ZIP 包解压到这个指定目录中。

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img008.bb31d9a2.png)

#### [3]打开

只要我们确认在解压目录下可以直接看到 pom.xml，那就能证明这个解压目录就是我们的工程目录。那么接下来让 IDEA 打开这个目录就可以了。

![./images](data:image/png;base64,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)

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img010.900e648d.png)

#### [4]设置 Maven 核心程序位置

打开一个新的 Maven 工程，和新创建一个 Maven 工程是一样的，此时 IDEA 的 settings 配置中关于 Maven 仍然是默认值：

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img011.d7914ffd.png)

所以我们还是需要像新建 Maven 工程那样，指定一下 Maven 核心程序位置：

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img012.a62a48e8.png)

## 4、模块导入

### ①情景重现

在实际开发中，通常会忽略模块（也就是module）所在的项目（也就是project）仅仅导入某一个模块本身。这么做很可能是类似这样的情况：比如基于 Maven 学习 SSM 的时候，做练习需要导入老师发给我们的代码参考。

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img013.5f438a0d.png)

### ②导入 Java 类型模块

#### [1]找到老师发的工程目录

![./images](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAZkAAADqCAIAAAD/Bq9CAAAiw0lEQVR42u2dC5QUxaGGa2E1aqJRgSAqkiAQDxcwhpwoIF5FTHj6woMCIg9hV1BhBRQRH1cCvnjtAgouREAjKgGPN/KIwQeJgkAAk8XrEZcYFQXXlWgkUQywe2umZrqr69HTM9O93V3zfxzH2Zqu6np0/V1V01N/UX19PQEAgJhTBC0DABgAtAwAYALQMgCACRTt3r077DwAAEC+YFwGADABaBkAwASgZcbSs2fPnTt3hp0LECfOO++8V155Jexc5Ai0zFhOPvnkRo0affnll2FnBMSJurq6sLOQI9AyY6FCRl+/+OKLsDMC4sEpp5xCoGUggjAti++lCRqYuF8w0DJjifulCRqYuF8w0DJjifulCRqYuF8w/mhZVVVVv3791qxZ06lTJz587dq1s2fPpq/HH3982CXNi2+++aZv374TJ06kr2HnxStBX5q6Ri8oIlgJBw4cuPDCC5977rlsswQtS+CvltHjaWr0zUknnfT666+zNGkLdezYcf/+/XygFT5p0qQJEyZYmenevftXX30lHJkP0DKZCHbjhieClQAtC4QctIy2xLhx45YsWUKj0IijR4/etWvXCSecQEWEXjRUsITAd999t3PnzpdccgnTMiZtixcvph/5OCo0WMviWLT44lLbfjUEtEyE1iwd1Fx66aWNGzfOOfU81cRqFfr+2muvfeONN5o0aSI3+YgRI6h+MS3jz0iPHDRo0LRp0/K/Z0a2w7s0E7QsgsRXy3wRhEDRatlLL720ZcuWNm3aXHfddRlzT0faltZYk0H2ER0xMWXhw6ncMOmx5oP0PR2oC61oDcFoTlatWrV06VIWzosXcdUydnHQuOwA5ajt66+/tjLWokULejpLMWnKkydPPuecc2gK11xzDbvOWJ6vvvpqmp85c+bQQCsiGyqyWCxBq1DKksp1oqwlF1yaSXlpCtm44IILrNOxlrJqg87QaSlefvllGlhdXW21r9XWn3zyidzoGWPR93x+WMebOnXqzTffTHNFs0QD2QqD7iLp0aOHNUinIbQJaKDQjlZl0sSHDh1K09fVJ9/QfJMJF4DuOtFd+da5+MC77rqLXjN8bVv3eP4woSEy9hfhvMOGDeNLPXz4cNZx5OwJZdy4cSPRa1lWghAKWi07evTos88+u2fPHi+5t1qUvrfEgiRV5sMPP2QNY90rLImhF+WMGTNojfPTSetaZ822YsUKejC9XulHXrSMj8XW3WiT7969m0WnIQ888MCAAQPowSwWbXh+uU2ewPLSxmRr8ODBbBlO7p/sMCsWn5pcUlZX/Eoff0f1eJd2aSZZy2iacjZYSdmJeK1nGWB14q5lfKNnjCVrGY3LxOLVV1+l7cX6nnW8supop2L3IZoCyzwVZbnqmFL/8pe/ZAkqF7ZcmowPF5ZlrcP4StBlgG9ij+My5ZWg7C/Kq0gu9RlnnKFMkC+j+7gsK0EIBbf1sv/85z9z5849dOgQvVFcdNFFLqlYV551kbEbjjX2YZcpH8W61QhDG3at08D777/fWrmnKXgclxHuqwOabVrvt9xyC0lPUX/1q19deeWVtNfNnz9/5MiRdPq5d+9ePsNCM1vXHAtv27btiy++aGWSXTT//ve/rXwKV6rwp1BSoa74nMu15IKumXSXpnIsyTIprAlYf7prma7RlbFIsu9Z3+HwfYzvwMJEScgzSQuH1bI0D3LVsRGK1YHZggM9I58B2qbKJhMuAKFmrMNatmzpkoEf//jHQhMLgqXLicuVkPEqEnSQlZpe53KCY8aM4cuYcVHCuyCEgs/jMhctkxfO2Bjqvvvuo43E37epNtFPLeUimpmjcr2MhzYqvTvRsTHtrrRFy8rKLBWjE0Yqjs8884yQMavtlZf4Z599xuZB/L2dfbRjxw6XjkGveLmkSi3Ldnkxq3GZssIbWMuUc0wXLaPH6C4S2ugsEfaNkFx1yl6tHJfloGUsNcKJqZwBOVcex2XK4iibz7uWyQkKmTF2XJbbehnRTDfY5N+ae9JxMm0Pvhno3WbWrFn8oJ2/6N2bWadlfDhNf/Xq1e3atWOLXPQ9m2nKcwdh8qJUJTaHpaWm0ek9SugArVq1YkJsFUpZUr6uaDrr1q3r06ePXEtC5/feTPKlyVedlQ2Pc0xrgia3FNHPMeVY2WoZ3wn5RGjl01ajKdAQdrxcdcQ573PRMrnJ+Goh0qM/sl4T5+qKlQGhielN1OMc02N/UV5FutGokKBQRncti/F6WVZfW/A3TP7pMGsZmNa+vGzJGu+1116jIUOGDKFDG+VYnR1sReenogxes/g0+Qkav44mLJ3wa6LC2r9ytsiOp4H0SHpxL1u2jKRXWK2paGVlpZyaUFLWIYVCuX8ZklUzKdfLlNlg0xa25Ew7p/V0Ht981tTGisjfdfhn+txjZatlbKgr51nQIKJaF/c+LtM1GS86yuuEv/KVbSc3MV/bwgBc2RDu/UW+iohGwXUd0KOWxfh7TJADkXq+If/HhXJ+1DlGP/bIs8l0c+c4YuzzZSAH4q5lNP+jRo2aN2+e/M2d77EiQp5NZj0REgvhdgdaBmzirmXEOVPz8i1qPrGiQM5NxtZS5BWP+AItAxEl7pcmaGDifsFAy4wl7pcmaGDifsFAy4wl7pcmaGDifsFAy4yFXZoAZAW0DESOSy+9lD2LBIBH2rVr9+6774adixyBlgEATABaBgAwAWgZAMAEinbv3h12HgAAIF8wLgMAmAC0DABgAtAyAIAJQMsAACYALQMAmAC0DABgAtAyAIAJqLXs0KFDxx13XNh5A5k5ePDg7NmzJ06ceOKJJ4adl4Jm3759p59+eti5KGigZTGGCllpaenFF1+8fft2qmiQsxCBloUOtCyuMCEbNGhQ//7933vvvVmzZkHOQgRaFjrQsljCCxkLgZyFC7QsdKBlsYRq2Y4dO+jskg+kckaSW1CFnbtCBFoWOtAyAHwAWhY60DIAfABaFjrQMgB8AFoWOsFp2TtzRrx81oPjrjlN8/mnG8dP2fA+6XT30mtJ5dRNP5sx4adhVwYAuaLXstpV9z5DxqY6wlYvl/rO58bv61HRr5kjMNVfZBI96HziTDyVQu2cEU9bjg+X3Gp4FwtIy97hK9Gi9YAy2kIfr5k3ZnWN3QaJRqoZnG4PAOKIVsvo5f0Y6X5mFbl83AXb2ZWfpuVlC6ddfObO5/rPr0qFdBnyYkn7rZXz9l4uDQJoOr/7QUVJe2coFcpXW05L9J10t7JpPeCyVqtruiV7licNjTn+axmrU/EmkGzR22nLpf622oC+KV++15ECk7ywawaALNBpGe0OM8mgwfue2UTIa29at/DEzZ7IfSShVkQcByQFLqOWEfW4bBe0LEctSwjZtk70bvMJf2+hd54Xmi9MCZksXvYgmRRGpQPz0GhZQrM+HFBGtSzdHdiUpfmwB9Ujr9tPf5lqH7uXO/qCNy2b/mbqg+SAAHNM39bLEneebtunTifJG4v4KbtjvLNqTbNrkhPPRBP+7P+cwzcA4oFSyxJX9TZCfs6Py6iK9fxoSlpiunBdI6FWpPvHG5aT5NzTudCW63oZxmV+fI+pnmwyUmsE9t0ppWWYWoJ4otSyrWs2ElK1IjnHZOOyZKcgicue1H58WrPEPdspUq0HDOm+bVdyqPXOnHs/G2jd13Mcl0HL8tMyvk550gthtasqX/3oY9JtWsdNtLWurBmzvePCxNC6Z/dtT390peE1Dowk43rZ3ssTw7EP7a+/SOpGbi0lp9WKRbmdPOO4u+e4XoY5Zq5axlSsdcvmdFwtDrLS3zQnm6qnffNJ3jrOSI3LajM8yQFAJPGgZWnlmrKBJBSNpKaQZKO0rqJaU8ukZfIAonWXTuTj5ixljMtyRD1hTGvZ1srnSEmPvYk2oK/lbCBmR0l+UfDitIvDrhkAssBdy1LTkXvLU2thyTWW1EDJGpfZX5EltYw9sWEl5GFclvpzbPMV7CEnmuD2jmw9DlqWI/KjLgzuYQuhDbBeBuKNBy1LwlaKhSV/tl6WFC9irTITemSNPTTLvPbPfVeQULHmwz6uyu4Z3ZgTwrgs+QenZelnBY2fzwODyaxlsooxrOGYPf20Ok5yKHemp+fLRLXilnQcj6abC36PCYAP4PeYoQMtA8AHoGWhAy0DwAegZaEDLQPAB6BloQMtA8AHoGWhAy0DwAegZaEDLQPAB6BloQMtA8AHoGWhAy0DAJgAtAwAYALQMgCACUDLAAAmAC0DAJgAtAwAYALQMgCACUDLAAAmEJSWHay6PJFy4h9JvLKzpN/Ql8bH/fD7HR8Nu/gAAEMISsu++mv/k864NqFepC4hXfQ1oWT264EPX2zy83VhFx8AYAiBadlf+p905kCdkNGQAx+sbXI+tAwA4A9Badk//9L/+2deoxMy+ubzD9c3ddGyPRXd2q4cWL1pfBtn+PrSount5WAAQIETmJa9RbVsgE7I6JvPP1jf9IL12vjQMmAGVcvHLdmRfHd6v6l3/qK5EMoFqo9MfbDfGZSg5g8PzdjfZ96wTupjVKcQIurOaId3HpVKX1EqRZa04cpP9TnMiaC07Mud/U5uebVOyOib2r+/1KzL+qzThZaBOFG1/KFPe7F+mui5JCkNCS3Z+dNk97UDtUeu2de5c+cd+1uI3Z1+tpSMuPMXRHWM8hRCxBrVGZPv17XQa0uGLNHPdMrk/NQth7kRqJZdpRMyOves/eAP0DJQSKRFgvDjKcfgSjyyuebvjMfUuJxCqVVWYFroMo2SFKkko/60xZqdSiUUPq3JWAlZE5iW7aBadoVOyJLjsg3Nuv5eGz8xx3zn7vrHeyf+oALWp9L6qGt5WsvscDssEbFsczKwZF0qPgDhY40+6Ju3znOTFmmcoj7GGeQIcDmFTsrYGdOKsybT3E9KJqVH572VDucGXopPM1ZC9gSlZV9s73vKWVfohKy+7nDtBxubnb+qqPh76vi2liUEi6zjVO1tplv8CM06ek9F6dq+jyfDHPEACJXk/KqFNW90GSZxR1rIXd0pBeIxLqeQIzrOmFzCSi2SOcRIRMiS9acd7pxECp96GStmS5Ba1rK/Usjo+y/37Th65JvG3217coeZ6viWOgmTSutP51iNcEMzjMxApEhqBXEseWuGJOKRaVR6J87JPI3LpIiKvHFncpEY3VjPfQhpv43RuOwff+576ln9lEJGQz77+6tNWnY9sHfzD7ppppletExeOEvKGGGi5pilAhAOinVtzcqWywq40NUzr7FpTiGPhsQzOpfLvGkZW9N3fmzPTjWf9tk/Q7O8lzOBadm2Pqe26qsUMvpa8/6rzVv3SLxe+JIjmvUoBlHOMXmtEuaepeRxh/AlD+2AcRkIE3Un5UJ1ky4nTk1RH6o9Rjcq0+ctNTPMZo6pCFdFFxRQymFeBKVlB7b1aXJWb91vmGre39i89cWJ1+4Ztcy5xF/eoWxle/1k0g7qWlJCKgnGZSBM7Ae1UnBLUWyw0tl+EkJ5ZDoZxyBG9U2jct3NcQohovaMmZ8uIz5omSqH+VH0yhtbenQ7Xwj1Qcu29mnSqpfuN0yfvv/H01r/d+JV0DIAgCs5D2J8Gv1El6JHl604p01rQc7y17LPt/Zp2uoXut8wffq31087u3vi9SJoGQDegZRpSWhZ01NPGdi/Fx/qg5Zt6Z2avNan9/vhtwAi9UWkqKj4u827Ph92DQAATKCo9sA/qJYJodiLEQAQL7CvLADABKBlAAATgJYBAEwAWgYAMAF4lwAATADeJQAAE4B3CQDABKLqXRIDct2IQ2dlkCPrS4teuNJLLnw7r2qLEp8LBUDWRNW7JHesX6Lbe806gn3b1AxaFlyhDKJQvEu8GJE4Y2nLmyNx8y7JANel+D2BAnEJyErLgttNzV3LgjgvPBe8UyDeJZ6MSJzeJVXqs+dB3LxL3HH0XG7j7G7DyHLf+x60zPeymI253iVejEjcnE38+d171LxLWN9bR/oIE0IuvKu9F2N6k+wSe/zF9etUn+u7lkrZwA5lZYqZp0Xy2HUDV/ZJ7H6WSI6kkk8eTxwzKDtdZVbljdW4rNLklpNhaXnJtJ23W6nTBeHK7Pm8RFl7rGDlqZrS7znuOCwVZmumrgULHoO9S5SnO/evbt4lyrPnV8FR8y5hHYfTptQ80RnOe5hwh7V1DkJSmtNuJu22qZjaZZ1k32bdl3VzoYtyY5G0eOizqvBP4cZH/Hgxw5hJLrVs12JpmefzamqPhVfaBZc2xeTrSnuYrloKG6O9S9Sn47RM4WyiPHt+RM27ROjfmn4vznLSnxLVuIxqGXdwOmq18ysCPkXle/5NWjvUWU3/4RjLaDWl0jFSFL64kEqtsGup5svs6by62ustaCWbmCszKR1GhHGZuloKk4LwLnEZaeqdTXTlzY2oeZfkrGXJHlXNh6ejtHUsl2kWezJqWeocwgRRkdW2Sv8UpZbZEcs2K+e+7qW2cm4PEz2dV1d7bZRaJmcSWpYFBeBd4rZ45uJsUuPPzNImYt4lTssR7o890vTROUuyBSd9mDMwNbF0m2Nm0LJkt32nA3m7/XJuHUnOqto/RT3HrKgeP95eDZQ7vKLUol2LpWXez6utPbVISZnMrGWqFixICsW7RFci/X7//lgvOYiYdwnrMB1KKiuFhWO5tytXr/lZFr/onPHpMg9aJiqoW1Zl/5RUqHMNPlO2pFIrvixwzHk9ntdt7V8al0mZ9DAuU1RLQVI43iXK07lomWt5cyMwLcvRuyTSUxI8jOCBSLegAWDDfx1BaVmu3iUR7gkRzlqUQDUFCqRMS2BalqN3SUR7Av+cBnAloi0IjCcof0wAAGhIgvLHBACAhiQof0wAAGhI4I8JADABeJcAAEwA3iUAABOAdwkAwATgXQIAMAF4l+RHhPa5N/Qh1QjVMIg0xnmXyBuvch+8Xe53n4hQT4OWRZJC8S7R51OXGfvn6PAuUbC+tNt7t29S7K1atrmkpKTybZN/GW6SlhlTlgLyLtHlk+jKa53Sp5+KmuVd4kDc1cL0XS6M6f+GlcXCXO8S10B1ZoiHbYyyxCzvEh5pp3l3LdPsLp0pJ/amYGrjD8e21/TTldyuh96sUgSbPOX82bXq1BYpqjD39ImzOETaXU7pVyKnKTVlMJYrkcNg7xJloDUaq1Fl5rTf67eizRGjvEt6O5MR9jN10zLFOMBbToTN+wVHjzZ8zvhNrL1bpfBB7ut92XipKMqrNEYRTqGrdt2plWkKTRmM5UrU1Mxo7xJ1YDp6wsNE7WyiOmkemOVdYo84SLlqY3ynh4ngXSI4dHjLiaOnSbutVjvzqd6N2tUqhVRoNumXi5CVl4pUXq0xCneKal21a05NlGkS3X2Dy17+liv5XLw+Y753iWugNjPc9wH9WuwkvaI6xwzHu6SNYohm4WG9jHfoCFfLUu/oBMsuWIbcZ+WlIpW32sNqorba9VqmSFOuwOAsV8KnILxLXANdnU2sI8TBYg6Y5V3iumTsPseUHDq85cRdy9zmmNlapfBJra+oaDtetV7m1Utlj9KRRDZGkatQaxmjqitlmtrbkp+WKxHRskLxLlEF2tGVmcmQVA6Y5V0iTZQE/xKXkYfk0OEtJxm0zOFkIq79Z7BKkdb81LYsnqpO9jRR2KZkclHXVruLX4kiTcUgLgjLlUhQON4lynxaUihnxveny+BdoieAnBj7VEh0Ws18sOG/DniX6PAlJzSRme02qb57NYrotJrxQMq0wLtEh0854SZZ0X30KV+i02qgcMFejAAAE4CWAQBMAFoGADAB+GMCAEwA/pgAABMIyh8T3iUAgIYkKH9MeJcAABoSeJcAAEwA3iX5Ea0Ns1IP5up/TQmAsRSGd4mXDVNzI0pahqfvo0gBeZfow5UngneJK0rvEmWggQT/03WoZbYUiHeJ47PTZX8mxYngXZIFyq5t7FYVDVI2aFk+mO5dkvYK2OmmS+l4NfAuycO7RBtonTjO3iVcdfC7YAv1I1Rju5lu2RA00WkpovAcIfryAuO9S1KKed5b/M6P0laOfCXAuyRn7xJ1oP1R3L1L+HGZN5ORjNlwqyal54iuvAWP6d4l1p/OXWyd0fkT6U6aB4XiXSIFmuddokneJfOesuFijyINZtfrylvQmO9dwv2hi6IoGrxLEmTpXeJ5xT/W3iXuWqY0GfGyVbemdZSeI9AyiQLwLrG/j7SRvxclLuMueJd49C7xsmBtgneJ6xxTnLFKMbLVMrXnCOaYTgrMu4SIZ0tGJxlWw+Bd4tm7hLgZmiiSi6t3ic4A1KUas9UyzlJkU9+1Ks8RTXkLlQLzLiFKLatRngjeJQ0HvEtQ3iiCDf91wLtEB7xLUN4IAinTAu8SHfAuQXlBnMAe2QAAE4CWAQBMAFoGADABaBkAwASgZQAAEwhKy+BdAgBoSILyx4R3CQCgIQnKHxPeJQCAhiQof8xC8S4BAESDoPwxQ/MuASBSFIp3if50qqLJ+wRFdy/GkLxLAIgUBeJd4nY6TSUISea/RbbJ3iUARApzvUtqMpZIm23i106M0fMucfUQkVxL8OtlEBsM9i5Rnu7cv7p5l+gLkjMR8y7J6CGCnWRAHDHau0R9OlnLFEXzaXqZJGreJZk8RLC9H4gbBeFd4j7S1BXNTymLnHcJQ+8hAi0DsaIAvEvcFs+0J8qUfg5EzLtE4yEiuJa4W3gAEBUKxbtEVyJ37xKft7qNmneJxkOEX0LLZOEBQFQoHO8S5encvEt8nmCS6HmXAADcwIb/OqLmXQIAcAFSpiVq3iUAAJAL2IsRAGAC0DIAgAlAywAAJgAtAwCYALQMAGACQWnZihUr6mjSdeILfT3+uON69+7dtGnTsMsOADCHoLTsN08/PXjQIPa+PvVfgpUrn/vJT36yddu2fn37Qs4AAH4RlJY99dRTQ4YMOVpXx54mSz1ZRsjzq1f17NmztrZ269atI0aMCLv4AABDCErLnnzyyeuvv/7o0bqUiKX/9/zq1fv2JX62VXzsseNvvTXYwiV+ublyYIHvqhHFSsh7t5MsCkXP9cKV+N1uARCUP+ayZctvuGHokaNHE3/UW1PM1ACtuHHjBY8+WjZ+XLCFi2I3bnCiWAmFpGXwLnF8Kvxkfkmm/WuzICh/zKVLl94wbNhRqmW2kJG0fXlCy+YtmD+hrMxbYordZkFguNS2Xw3RkLvQhatl8C5hn/7+tDvT29YSaddal53bsiEof8xfP/HE8GHDqZZxM1hrOltf3Li4Yt68iRNu85YYtKwhgZYFBLxLdPu1+bP7T1D+mEuWLBkxYmRqjpnAWv5PKNoxxcXlFRWTJk5QxBTNS+wNzYjoXdK1vLxD2cr24u6z6m0cPccSM5TseOsGruyTyFUiSySVkr2Tt5hnxxSI+0N2XUkmTvNT5kxQqpGUe4t9Cme45OoiHiVWAn8uPjCdFUVuXBrCpSoIUZy3mi81d5ycoFxGrkoS0TK2TmS0DN4lfCwP22pnS1Br/5WLF9848sYjR48k/pCmmVTL5syde8ftk6R4eypK1/Z9PHnJ2jvI8t2R31c22W9IuQctyyaWmKVkB2M9g/W1EiFTqjzbIw/rOH4wwgf2qbQTVK4BOd1bnNWidXWxDhO6vSoDTi8Yj+MyZWrK5pNPoSy1JkFHGeWMZGydaGhZgXuXpHdqtFbLvIwVsyUoLXv88cpRo248csQxx7RE7ZjixrPnzJ18x+3KuBpbueT1KMxOrD/dtSyrWPwITuxjuvdyntOfEodq8cW0Ryh2Bx5Gllud0sqAIC6a3cPFeVv607auGWg3U5rtiXcOdU7UxWlDlANr8RTrFaWuViZI1MKqFmjl+/C1DN4lfKzUVwYxGpctXLRo9OjRVMvSAdx56uuLjymeNXv2lMmTxWjcmMkx8GlQLRPI1FuIMs+pj5eTYUyfNGtEql6tGpflpGXJ1IimEogyFvE6LlOmpmw+71qmqJ89cdcyeJeo49V4j+KVoLTssYULS0pKjhxOzDH5E7DTHXNM8cyZs+6acqcYjbsak/2iQzZzzNQEzY7oaY4pxXLJk/J9tTLPrJO+04G83X75JmHSlfyjlI5de3vWMj5VVbUQxRxT1GtdBgQvGOJ5jimlpm4++RTa0aiUPWcZrfYiMdEyeJew7zpSX2OKqUs5zIugtGzBo4/dVFp6+MgRLsw+FdWyhx+ZefddU6R49gSla0kJqSR3W/4lNNSe6KQOsVfxuZh2RHHY5S2WmKWMvUWdZyLLo2Jd3PO4rENJZaVz6V8xZsm09q9cmJe8YBy1rWwesSEcJ1NUhXgKTak1CcZYy+BdYukW+5BPUo6SH0Fp2fwFC8bcNCalZdI5qJY99PDD90ydmm/2c/tyP2Ymm/k9CYEHWswCG/7rCErLKubPHztmjMsBDzz40H333J19wrRrzmy3SfXNnf+xIkJeahTFx/5B7kDKtASlZeUV8+rqE//SO/3U19ULAfX/c+89uSTNzUS6epek3GJFgly1LDXjhIsoKAiwFyMAwASgZQAAE4CWAQBMAFoGADABaBkAwAT817L777+fvp577rlVVVUdO3bctWsXe6WBQ4YMOfvss1PH1dWVn3jCx19/O0uVAQAAyAr/tezee+/t2rVrr169NmzYcNlll1mvmzdvLioquuqqq6i00cOq/vjmi4Ou+3L/RzOhZQCAvPFfy6ZOnTpjxoxFCxcOHTZi2RNLbhg+8sllTwy6ftj8ijn33HPP9OnTqZyd3facpb+r+sMLKxbPm/qDpqeGXQkAgNjjv5ZNmTLlwQcfPFpX17hRIyvw8JGjD8yYTrWMvqdyNvXi2c/v7PHJsVeUjR0edg24EP52MQAAj/ivZXfccccjjzzy0WcHDn7zLR++evkSdq6+nXZ1PO5/t6w/0r38cKNGxWHXgAvQMpA38C7RFU39i/Pc8V/LJk2aNGvWLPqmTpVyo6Ki+j99560/Hf72mP/qMnlXvtkPFmgZyBN4l+gqgTvOL+8S37Xstttumzt3zqdfHDzw1b/kT9v+a3Ld3mfpoOy/y48UFTXOL/NBAy0DPgLvEj4ev7GsP797998fc/z48eXlcz//6sDBQ4otfX707vI/bzi8v+ngK8p+o4qt8+kg6s25vBiLWOmm9xJLb/pHYmN7AQwA3iXOotmqqfAgyAX//TFvueWW+Qsqdla/dWzxn4WP2n2x5NBHVTtfO7KmeMLs2bNVsXU+HRpjjszWFTapXcvsHe5jYnsBDKDAvUtUReOWy/wx+/XfH3Ps2LGPPjZ/5R9/e8qPFvPh32vcosue325df/iMfuWzfvu3iooKVWzN3vZEY8zRO+O2onziTLGsEVu0tyQFpgDvEsWJHELpz4KZ//6YpaWlCxc9Nn3F9B922cCHX1tbffCDf1Tt/M4lD311663jFixYoIrtXcusTeKhZSC6wLtEeaJ4eMqNHj16UeXCoQ8PPbP3e1Zgl+MvOWv7B99WPf/6j0bdXrJw7JibFy1apIqt8+nQGHN4MkmyjXaZMZIzAFoGAgPeJeJ3HYrz+DYu813LRo4cufjXlV3Gdzm5l/095vCiC38zc/O0Ue3HbvngzYotN5XctHjxYlVsnU8HcVv796Bl7WZaWmgpJIGWgWCBdwmzj1OeiMtARJ8vGz58+JInlpw5+PTaf9bKnzb7frNPnvl01Mgbly5dqooNpw0A3MCG/zr817KhQ4dSLStunHigv4j+c9Io+cOmG2644cknn1TFhpYB4AKkTEsgWlZXV+d+DFW0p556SvUJtAwAkAvYixEAYALQMgCACUDLAAAmAC0DAJgAtAwAYALQMgCACUDLAAAmAC0DAJgAtAwAYALQMgCACUDLAAAmAC0DAJgAtAwAYALQMgCACUDLAAAm8P8f8p9Ut0m73gAAAABJRU5ErkJggg==)

#### [2]复制我们想要导入的模块目录

![./images](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAZkAAADqCAIAAAD/Bq9CAAAjC0lEQVR42u2dC5QUxaGGa2E1aqJRgSAqkiBsPFzAGHKigHgRMeHpCw8KiAsIu4IKKw8R8XEl4IvXLqDgQgQ0ohDweCOPGFRMFAQCmCxej7jEqCC4rkQjiWKA3VszNdNdXY+enpnu7Z6a/+M4ztZ0vbv+qaqZqb+gvr6eAABAjlMALQMAGAC0DABgAtAyAIAJFOzZsyfsMgAAQLZgXgYAMAFoGQDABKBlAAATgJYBAEwAWgYAMAFoGQDABKBlAAATgJYBAEzAHy2rqqrq16/f2rVrO3bsyIevW7du9uzZ9PHkk08Ou6ZZ8c033/Tt23fChAn0MeyyRAVdp+cVEWyEQ4cOXXrppStXroxOkRqGKGoZvZ6mRp+cdtppb7zxBkuT9lCHDh0OHjzIB1rhEydOHD9+vFWYbt26ffXVV8KV2QAtk4ngMEYjEGhZQGSgZbQnxo4du2TJEhqFRhw1atTu3btPOeUUKiL0pqGCJQS+9957nTp1uvzyy5mWMWlbvHgxfcnHWaHBWmZw1SKIS2v71RHQMhHasnRSc8UVVzRu3Djj1LNUE6tX6PMbbrjhzTffbNKkidzlw4cPp/rFtIzPkV45aNCgadOmZd+pkR3w2XdTZKtmJLmrZb4IQqBotezll1/eunVrmzZtbrzxxpSlpzNtS2usxSB7ic6YmLLw4VRumPRY60H6nE7UhV60pmC0JKtXr166dCkL58WLuGoZuzloXHaBctb29ddfWwVr0aIFzc5STJry5MmTL7jgAprC9ddfz+4zVubrrruOlmfOnDk00IrIpoosFkvQqpSypnKbKFvJhbS6SS7GJZdcYmXHespqDbpCp7V45ZVXaGB1dbXVv1Zff/LJJ3Knp4xFn/PlYQNv6tSpt912Gy0VLRINZDsMupukR48e1iSdhtAuoIFCP1qNSRMfOnQoTV/XnnxH810m3AC6+0R351t58YH33HMPvWf41rbe4/nLhI5IOV6EfIuLi/laDxs2jA0cuXhyHV3mHOneaQ2PVsuOHz/+/PPP792710vprR6lzy2xIHGV+eijj1jHWO8VlsTQm3LGjBm0xfnlpHWvs25bsWIFvZjer/QlL1rGx2L7brTL9+zZw6LTkIceemjAgAH0YhaLdjy/3SYvYHlpY7I1ePBgtg0nj092mRWLT02uKWsrfqePf0f1+C6dVjfRNOVisJqyjHitZwVgbeKuZXynp4wlaxmNywbSa6+9RvuLjT3remXT0UHF3odoCqzwVJTlpmNK/ctf/pIlqNzYcukyPlzYlrUu4xtBVwC+iz3Oy5R3gnK8KO8iudbnnHOOMkG+ju5KkdadFgpu+2X/+c9/5s6de+TIEfpGcdlll7mkYt151k3GBN6a+7DblI9ivdUIUxvWpjTwwQcftHbuaQoe52WE++iAFpu2++23306SS9Rf/epX11xzDR118+fPHzFiBF1+7tu3jy+w0M3WPcfC27Zt+9JLL1mFZDfNv//9b6ucwp0q/CnUVGgrvuRyK7ngvZsYyrkkK6SwJ2D96a5luk5XxiLxsWd9hsOPMX4ACwslocwkKRxWz9IyyE3HZijWAGYbDjRHvgC0T5VdJtwAQstYl7Vs2dKlAD/+8Y+FLhYES1cSlzsh5V0k6CCrNb3P5QRHjx6d1qo23TutgfF5XuaiZfLGGZtDPfDAA7ST+Pdtqk30VUu5iGblqNwv46GdSt+d6NyYDlfao2VlZZaK0QUjFcfnnntOKJjV98pb/LPPPmPrIP69nb20c+dOl4FB73i5pkotS3d7Md1ukovRwFqmXGO6aBm9RneT0E5nibBPhOSmU45q5bwsAy1jqRFOTOUCyKXyOC9TVkfZfd61TE4wrR26HJ6XZbZfRjTLDbb4t9aedJ5M+4PvBvpuM2vWLH7Szt/07t2s0zI+nKa/Zs2aoqIitslFn7OVprx2EBYvSlVia1haaxqdvkcJA6BVq1ZMiK1KKWvKtxVNZ/369X369JFbyX3yn1Y38U1nFcPjGtNaoMk9RfRrTDlWulrGD0I+Edr4tNdoCjSEXS83HXGu+1y0TO4yvlmI9NUfWa+Jc3fFKoDQxfRN1OMa0+N4Ud5FutmokKBQR3dyeL8srY8t+DdM/tth1jYwbX1525J13qZNm2jIkCFD6NRGOVdnF1vR+aUog9csPk1+gcbvowlbJ/yeqLD3r1wtsutpIL2S3tzLli0jyR1WaylaWVkppybUlA1IoVLuH4Zk2U26YrBlC9typoPT+nYe333W0saKyL/r8N/pc4+Vrpaxqa5cZkGDiGpf3Pu8TNdl/DhX3if8na/sO7mL+dYWJuDKjnAfL/JdRDQKrhuAHrUshz/HBBlg2PcbMv6qcw792CPLLtOtnUHDAy3zk1zXMlr+kSNHzps3T/7kzvdYESHLLrO+EZITwm020DI/yXUtI86VmpdPUbOJFQUy7jK2lyLveICwgJYBAEwAWgYAMAFoGQDABKBlAAATgJYBAEwAWgYAMAFoGQDABKBlAAATKNizZ0/YZQAAgGzBvAwAYALQMgCACUDLAAAmAC0DAJgAtAwAYALQMgCACUDLAAAmoNayI0eOnHTSSWGXDaTm8OHDs2fPnjBhwqmnnhp2WfKaAwcOnH322WGXIq+BluUwVMhKS0u7d+++Y8cOqmiQsxCBloUOtCxXYUI2aNCg/v37v//++7NmzYKchQi0LHSgZTkJL2QsBHIWLtCy0IGW5SRUy3bu3ElXl3wglTP6WFRUFHbp8hFoWehAywDwAWhZ6EDLAPABaFnoQMsA8AFoWegEp2Xvzhn+ynkPj73+LM3rn74+bsrGD0jHe5feQCqnbv7ZjPE/DbsxAMgUvZbVrr7/OTImMRC2ebnVd60cd6BHRb9mjsDEeJGJjaCLiTPxRAq1c4Y/uyl53eV3GD7EAtKyd/lGtGg9oIz20P6180avqbH7INZJNYOT/QFALqLVMnp7P0G6nVtFrhp7yQ525ydpeeXCad3P3bWy//yqREjnIS+VtNtWOW/fVdIkgKbzux9UlLRzhlKhfK3ltNjYSQ4rm9YDrmy1pqZrfGR50tAcx38tY20qvgnEe3QS7bnE31Yf0Cfly/c5UmCSF3bLAJAGOi2jw2EmGTT4wHObCdn0lvUWHnuzJ/IYiakVEecBcYFLqWVEPS/bDS3LUMtiQra9I323+YR/b6HvPC82X5gQMlm87EkyyY9GB+ah0bKYZn00oIxqWXI4sCVL8+KH1TOvSWe/QrWPvZc7xoI3LZv+VuKF+IQAa0zf9sti7zxdd0ydTuJvLOKr7B3j3dVrm10fX3jGuvBn/+ecvgGQGyi1LHZXbyfk5/y8jKpYz4+nJCWmMzc0YmpFuu3fuJzE157OjbZM98swL/Pjc0z1YpOR2COw350SWoalJchNlFq2be3rhFStiK8x2bwsPihI7LYntfvPahZ7z3aKVOsBQ7pt3x2far075/7PBlrv6xnOy6Bl2WkZ36Y8yY2w2tWVr328n3Sd1mEz7a1rakbv6LAwNrXu2W37sx9fY3iLAyNJuV+276rYdOwj++Mvkngjt7aSk2rFokwizzne3TPcL8MaM1MtYyrWumVzOq8WJ1nJT5rjXdXTfvOJv3Wck5iX1ab4JgcAkcSDliWVa8pGElM0klhCktelfRXVnloqLZMnEK07dyT7m7OUMS/LEPWCMall2ypXkpIe+2J9QB/L2UTMjhL/oOClad3DbhkA0sBdyxLLkfvLE3th8T2WxETJmpfZH5HFtYx9Y8NKyMO8LPHnmOYr2JecaII7OrD9OGhZhshfdWFwX7YQ+gD7ZSC38aBlcdhOsbDlz/bL4uJFrF1mQq+ssadmqff+uc8KYirWvHh/VXrf0c1xQpiXxf/gtCz5XUHj1/PAYFJrmaxiDGs6Zi8/rYETn8qd6+n7ZaJacVs6jq+mmwt+jwmAD+D3mKEDLQPAB6BloQMtA8AHoGWhAy0DwAegZaEDLQPAB6BloQMtA8AHoGWhAy0DwAegZaEDLQPAB6BloQMtAwCYALQMAGAC0DIAgAlAywAAJgAtAwCYALQMAGAC0DIAgAlAywAAJhCUlh2uuiqWcuwfiT2yXJJP6EPjk374/Q6Ph119AIAhBKVlX/21/2nn3BBTL1IXky76GFMy+/HQRy81+fn6sKsPADCEwLTsL/1PO3egTshoyKEP1zW5GFoGAPCHoLTsn3/p//1zr9cJGX3y+Ucbmrpo2d6Krm1XDazePK6NM3xDacH0dnIwACDPCUzL3qZaNkAnZPTJ5x9uaHrJBm18aBkwg6rlY5fsjD87u9/Uu3/RXAjlAtVXJl446AyKUfOHR2Yc7DOvuKP6GlUWQkRdjnZ4p5GJ9BW1UhRJG658VV/CjAhKy77c1e/0ltfphIw+qf37y806b0g7XWgZyCWqlj/yaS82TmMjl8SlIaYlu34aH752oPbKtQc6deq082ALcbjT15aS4Xf/gqiuUWYhRKxR5Rh/vr6FXltSFIm+plMm56tuJcyMQLXsWp2Q0bVn7Yd/gJaBfCIpEoSfTzkmV+KVzTV/p7ymxiULpVZZgUmhSzVLUqQSj/rTFmt3KZVQeLUmZSOkTWBatpNq2dU6IYvPyzY26/J7bfzYGvPde+uf7B37gwpYn0rrpS7lSS2zw+2wWMSyLfHAkvWJ+ACEjzX7oE/evshNWqR5ivoaZ5AjwCULnZSxHJOKszbV2k9KJqFHF72dDOcmXopXUzZC+gSlZV/s6HvGeVfrhKy+7mjth683u3h1QeH31PFtLYsJFlnPqdo7TLf4GZp19d6K0nV9n4yHOeIBECrx9VULa93oMk3irrSQh7pTCsRrXLKQIzpyjG9hJTbJHGIkIhTJ+tMOdy4ihVe9zBXTJUgta9lfKWT0+ZcHdh4/9k3j77Y9vf1MdXxLnYRFpfWnc65GuKkZZmYgUsS1gji2vDVTEvHKJCq9E9dknuZlUkRF2bicXCRGN9dzn0LaT3NoXvaPP/c987x+SiGjIZ/9/bUmLbsc2rflB101y0wvWiZvnMVljDBRc6xSAQgHxb62ZmfLZQdcGOqp99g0WcizITFH53aZNy1je/rOl+3VqebVPgdnaLb3MiYwLdve58xWfZVCRh9rPniteesescdLX3ZEs76KQZRrTF6rhLVnKXnSIXzxS9tjXgbCRD1IuVDdosuJU1PUl2qv0c3K9GVLrAzTWWMqwlXRBQWUSpgVQWnZoe19mpzXW/cbppoPXm/eunvssVtKLXNu8Ze3L1vVTr+YtIO6lJSQSoJ5GQgT+4taCbitKDZZ6WR/E0J5ZTIZxyRG9Umjct/NkYUQUZtj6m+XER+0TFXC7Ch49c2tPbpeLIT6oGXb+jRp1Uv3G6ZPP/jjWa3/O/YoaBkAwJWMJzE+zX6iS8Hjy1Zc0Ka1IGfZa9nn2/o0bfUL3W+YPv3bG2ed3y32eBm0DADvQMq0xLSs6ZlnDOzfiw/1Qcu29k4sXuuT5/3wRwCR+gJSUFD43eZdXgi7BQAAJlBQe+gfVMuEUJzFCADILXzb++/Zs+euXbvCrg7IJS666KJXX3017FIAQ/BNy04//fRGjRp9+eWXYdcI5BJ1dXVhFwEYgm9aRoWMPn7xxRdh1wjkBmecEdvZgJYBv/BZy3BrAo/ghgH+EpSWwbsEuAMtA/4SlJbBuwS4Ay0D/hKYlsG7BLgCLQP+EpSWZetdkgNkehCHzsogQzaUFrx4jZdS+Jav6oiS9BOHlgF/CUzLsvQuyRzrl+j2WbOOYN8ONYOWZZV4vmhZvniXeDEiccbS1jdDgtKyoLxLUsANKf5MoEBcAtLSsuBOU3PXsiDy9ac180PL8sS7xJMRidO7pEqdexYEqmUBeJe44xi53MHZXYvJct/9TqBlWaWSH1rGY653iRcjEjdnE39+9x6YlmXoXcLG3nrSR1gQcuFd7LMYk4dkl9jzL25cJ8Zc33VUyga2LytTrDwt4teuH7iqT+z0s1hyJJF8/HriWEHZ6SqLKh+sxhWVJrecFCflJdVx3m61TlaEq7PnfImy9VjFyhMtpT9z3HFZIszWTF0PprhhzMdg7xJldhf+1c27RJl7dg0clJZl6l3CBg6nTYl1ojOc9zDhLmvrnIQkNKdoJh22iZjabZ342GbDlw1zYYhyc5GkeOiLqvBP4eZH/HwxxZxJrrVs12Jpmed8Na3HwivtikuHYvJtpb1M1ywpbhjDMdq7RJ0dp2UKZxNl7tkRpJZl4l0ijG/NuBdXOclXiWpeRrWMuzgZtdr5EQGfovI5/ySpHeqiJv9wzGW0mlLpmCkKH1xItVbYtVTzdfaUr671egtayRbmykJKlxFhXqZuFpcbxmDywrvEZaapdzbR1TczgtKyTL1LMtay+Iiq5sOTUdo6tss0mz0ptSyRh7BAVBS1rdI/RalldsSyLcq1r3utrZLb00RP+epar41Sy+RCQsvSIA+8S9w2z1ycTWr8WVnaBKZlmXmXOC1HuD/2SstH5yrJFpzkZc7AxMLSbY2ZQsviw/bd9uSddsu5fSS5qGr/FPUas6J63Dh7N1Ae8Ipai3YtlpZ5z1fbemqRkgqZWstUPZjihjGTfPEu0dVIf96/P9ZLDoLSsgy9S9iAaV9SWSlsHMujXbl7za+y+E3nlN8u86BlooK6FVX2T0mEOvfgUxVLqrXiwwLHmtdjvm57/9K8TCqkh3mZollS3DBmkj/eJcrsXLTMtb6ZEZiWZehdEmlXy0C+pmYaXnswL7QsAHDgv46gtCxT75IIa1mEixYloGWBAinTEpiWZehdElHB4L+nAVyBloFw8M0fE7cmSAvcMMBffPPHxK0J0gI3DPAX3/wx2a0JQFpAy4Bf+OaPecUVV2zatCns6oBcoqio6L333gu7FMAQfNv7BwCAEAlKy+BdAgBoSILSMniXAAAaksC0DN4lAIAGJCgtywPvkjg+H96fbVEi+DVjP6oVkRYGkSYwLQvLu0Q+eJV74Z1yv8dEhEYatCyS5It3ib6cusLYP0ePmHeJQEjeJRtKu74/abPibNWyLSUlJZXvmPzLcJO0zJi65JF3ia6cRFdfK0uffioaqJY1uHeJA/FUC9NPuTBm/BtWFwtzvUtcA9WFIR6OMUqTwLQsFO8SHumkeXct05wunaok9qFgauMPx7HX9NVV3KmH3qxSBJs85frZtenUFimqMPf0ibM6RDpdTulXIqcpdWUwliuRw2DvEmWgNRurURXmrN/rj6LNkKC0LBTvkt7OZITzTN20TDEP8FYS4fB+wdGjDV8y/hBr71YpfJD7fl86XiqK+iqNUYQsdM2uy1qZptCVwViuRE3NjPYuUQcmo8c8TNTOJqpMsyBILWt47xJ7xkHKVQfjOz1MBO8SwaHDW0kcI006bbXaWU71adSuVimkQnNIv1yFtLxUpPpqjVG4LKp1za7JmijTJLr3Da542VuuZHPz+oz53iWugdrCcJ8H9Guxi/SK6hozHO+SNoopmoWH/TLeoSNcLUs8owssu2IpSp+Wl4pU32oPu4naZtdrmSJNuQGDs1wJn7zwLnENdHU2sa4QJ4sZEJiWheJd4rpl7L7GlBw6vJXEXcvc1pjpWqXwSW2oqGg7TrVf5tVLZa/SkUQ2RpGbUGsZo2orZZratyU/LVciomX54l2iCrSjKwuTIqkMCErLwvEukRZKgn+Jy8xDcujwVpIUWuZwMhH3/lNYpUh7fmpbFk9NJ3uaKGxTUrmoa5vdxa9EkaZiEheE5UokyB/vEmU5LSmUC+P7t8sC1LKc9y4JoCTGfiskOr1mPjjwX0dQWpb73iW+lIQmMrNos+qzV6OITq8ZD6RMS2BalvPeJT6VhFtkRferT9kSnV4D+QvOYgQAmAC0DABgAtAyAIAJ+OaPCQAAIeKbPyYAAISIb/6YAvAuAQA0JL75YwrAuwQA0JDAuwQAYALwLsmOaB2Ylfhirv7XlAAYS354l3g5MDUzoqRl+PZ9FMkj7xJ9uDIjeJe4ovQuUQYaSPA/XYdapkueeJc4Xjtb9mdSZATvkjRQDm1jj6pokLpBy7LBdO+SpFfALjddSsargXdJFt4l2kAr41z2LuGagz8FW2gfoRmLZroVQ9BEp6WIwnOE6OsLjPcuSSjmRW/zJz9KRznyjQDvkoy9S9SB9ku57l3Cz8u8mYykLIZbMyk9R3T1zXtM9y6x/nSeYuuMzmekyzQL8sW7RAo0z7tEk7xL4T0Vw8UeRZrMbtDVN68x37uE+0MXRVE1eJfESNO7xPOOf057l7hrmdJkxMtR3ZreUXqOQMsk8sC7xP480kb+XJS4zLvgXeLRu8TLhrUJ3iWua0xxxSrFSFfL1J4jWGM6yTPvEiLmFo9OUuyGwbvEs3cJcTM0USSXq94lOgNQl2ZMV8s4S5HNfdepPEc09c1X8sy7hCi1rEaZEbxLGg54l6C+UQQH/uuAd4kOeJegvhEEUqYF3iU64F2C+oJcAmdkAwBMAFoGADABaBkAwASgZQAAE4CWAQBMICgtg3cJAKAhCcofE94lAICGJCh/THiXAAAakqD8MfPFuwQAEA2C8scMzbsEgEiRL94l+uxUVZPPCYruWYwheZcAECnyxLvELTtNIwhJZn9EtsneJQBECnO9S2pS1khbbOLXSYzR8y5x9RCRXEvw62WQMxjsXaLM7sK/unmX6CuSMRHzLknpIYKTZEAuYrR3iTo7WcsUVfNpeRknat4lqTxEcLwfyDXywrvEfaapq5qfUhY57xKG3kMEWgZyijzwLnHbPNNmlCr9DIiYd4nGQ0RwLXG38AAgKuSLd4muRu7eJT4fdRs17xKNhwi/hZbKwgOAqJA/3iXK7Ny8S3xeYJLoeZcAANzAgf86ouZdAgBwAVKmJWreJQAAkAk4ixEAYALQMgCACUDLAAAmAC0DAJgAtAwAYAJBadmKFSvqaNJ14gN9PPmkk3r37t20adOw6w4AMIegtOw3zz47eNAg9rw+8V+MVatW/uQnP9m2fXu/vn0hZwAAvwhKy5555pkhQ4Ycr6tj3yZLfLOMkBfWrO7Zs2dtbe22bduGDx8edvUBAIYQlJY9/fTTN9100/HjdQkRS/7vhTVrDhyI/Wyr8MQTx91xR7CVi/1yc9XAPD9VI4qNkPVpJ2lUiub14jX43W4eEJQ/5rJly2++eeix48djf9RbS8zEBK2wceMFjz9eNm5ssJWL4jBucKLYCPmkZfAucbwq/GR+Sarza9MgKH/MpUuX3lxcfJxqmS1kJGlfHtOyeQvmjy8r85aY4rRZEBgure1XRzTkKXThahm8S9irvz/r7uSxtUQ6tdbl5LZ0CMof89dPPTWseBjVMm4Fay1n6wsbF1bMmzdh/J3eEoOWNSTQsoCAd4nuvDZ/Tv8Jyh9zyZIlw4ePSKwxY1jb/zFFO6GwsLyiYuKE8YqYonmJfaAZEb1LupSXty9b1U48fVZ9jKPnWGKB4gNv/cBVfWKlihWJJFKyT/IWy+xYAnF/yK4r8cRpecqcCUotknBvsbNwhkuuLuJVYiPwefGByaIoSuPSES5NQYgi32q+1tx1coJyHbkmiUVL2TuR0TJ4l/CxPByrnS5B7f1XLl58y4hbjh0/FvtDWmZSLZszd+5dkyZK8fZWlK7r+2T8lrVPkOWHI3+ubHzckHIPWpZOLLFI8QHGRgYbayVCoVRltmce1nX8ZIQP7FNpJ6jcA3K6tzibRevqYl0mDHtVAZxeMB7nZcrUlN0nZ6GstSZBRx3lgqTsnWhoWZ57lyRParR2y7zMFdMlKC178snKkSNvOXbMsca0RO2Ewsaz58ydfNckZVyNrVz8fhRWJ9af7lqWVix+BieOMd1zuczJV4lDtfhq2jMUewAXk+XWoLQKIIiL5vRwcd2WfLWtawGKZkqrPfGdQ10SdXXaEOXEWsxig6LW1coEiVpY1QKtfB6+lsG7hI+V+Mggh+ZlCxctGjVqFNWyZACXT3194QmFs2bPnjJ5shiNmzM5Jj4NqmUCqUYLUZY58fJyUsz0SbNHpBrVqnlZRloWT41oGoEoYxGv8zJlasru865livbZm+taBu8Sdbwa71G8EpSWPbFwYUlJybGjsTUmnwHL7oQTCmfOnHXPlLvFaNzdGB8X7dNZYyYWaHZET2tMKZZLmZTPq5VlZoP03fbknXbLNwuLrvgfpXTu2tuzlvGpqpqFKNaYol7rCiB4wRDPa0wpNXX3yVloZ6NS8Zx1tPqL5IiWwbuEfdaR+BhTTF0qYVYEpWULHn/i1tLSo8eOcWF2VlTLHn1s5r33TJHi2QuULiUlpJLca/mX0FB7oZO4xN7F52LaEcVpl7dYYpFSjhZ1mYksj4p9cc/zsvYllZXOrX/FnCXV3r9yY17ygnG0trJ7xI5wZKZoCjELTa01CeawlsG7xNIt9iKfpBwlO4LSsvkLFoy+dXRCy6Q8qJY98uij902dmm3xM/twP8dMNrP7JgS+0GIWOPBfR1BaVjF//pjRo10ueOjhRx647970E6ZDc2bRZtUnd/7HighZqVEUv/YPMgdSpiUoLSuvmFdXH/uXPOmnvq5eCKj/n/vvyyRpbiXSxbskZRYrEmSqZYkVJ1xEQV6AsxgBACYALQMAmAC0DABgAtAyAIAJQMsAACbgv5Y9+OCD9PHCCy+sqqrq0KHD7t272SMNHDJkyPnnn5+4rq6u/NRT9n/97SxVAQAAIC3817L777+/S5cuvXr12rhx45VXXmk9btmypaCg4Nprr6XSRi+r+uNbLw268cuDH8+ElgEAssZ/LZs6deqMGTMWLVw4tHj4sqeW3DxsxNPLnhp0U/H8ijn33Xff9OnTqZyd3/aCpb+r+sOLKxbPm/qDpmeG3QgAgJzHfy2bMmXKww8/fLyurnGjRlbg0WPHH5oxnWoZfU7lbGr32S/s6vHJiVeXjRkWdgu4EP5xMQAAj/ivZXfddddjjz328WeHDn/zLR++ZvkSllffjrs7nPS/Wzcc61Z+tFGjwrBbwAVoGcgaeJfoqqb+xXnm+K9lEydOnDVrFn1Sp0q5UUFB/Z++8/afjn57wn91nrw72+IHC7QMZAm8S3SNwF3nl3eJ71p25513zp0759MvDh/66l/yq23/Nblu3/N0Uvbf5ccKChpnV/iggZYBH4F3CR+PP1jWn9+9+++POW7cuPLyuZ9/dejwEcWRPj96b/mfNx492HTw1WW/UcXW+XQQ9eFcXoxFrHSTZ4klD/0jOWN7AQwA3iXOqtmqqfAgyAT//TFvv/32+QsqdlW/fWLhn4WXir5YcuTjql2bjq0tHD979mxVbJ1Ph8aYI7V1hU3i1DL7hPscsb0ABpDn3iWqqnHbZf6Y/frvjzlmzJjHn5i/6o+/PeNHi/nw7zVu0Xnvb7dtOHpOv/JZv/1bRUWFKrbmbHuiMebonfJYUT5xpljWjC3aR5ICU4B3iSIjh1D6s2Hmvz9maWnpwkVPTF8x/YedN/LhN9RWH/7wH1W7vnP5I1/dccfYBQsWqGJ71zLrkHhoGYgu8C5RZpQbnnKjRo1aVLlw6KNDz+39vhXY+eTLz9vx4bdVL7zxo5GTShaOGX3bokWLVLF1Ph0aYw5PJkm20S4zRnIGQMtAYMC7RPysQ5GPb/My37VsxIgRi39d2Xlc59N72Z9jDiu49Dczt0wb2W7M1g/fqth6a8mtixcvVsXW+XQQt71/D1pWNNPSQkshCbQMBAu8S5h9nDIjrgAR/X7ZsGHDljy15NzBZ9f+s1Z+tdn3m33y3KcjR9yydOlSVWw4bQDgBg781+G/lg0dOpRqWWHj2Bf6C+g/J43iP2y6+eabn376aVVsaBkALkDKtASiZXV1de7XUEV75plnVK9AywAAmYCzGAEAJgAtAwCYALQMAGAC0DIAgAlAywAAJgAtAwCYALQMAGAC0DIAgAlAywAAJgAtAwCYALQMAGAC0DIAgAlAywAAJgAtAwCYALQMAGAC/w/Z7Z9UhnRsAQAAAABJRU5ErkJggg==)

#### [3]粘贴到我们自己工程目录下

这个工程（project）是我们事先在 IDEA 中创建好的。

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img016.1933c568.png)

------

![./images](data:image/png;base64,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)

#### [4]在 IDEA 中执行导入

![./images](data:image/png;base64,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)

------

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img019.772f07d3.png)

------

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img020.bb620847.png)

------

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img021.ac677293.png)

------

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img022.ac55e275.png)

#### [5]修改 pom.xml

刚刚导入的 module 的父工程坐标还是以前的，需要改成我们自己的 project。

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img023.4ffa60b5.png)

------

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img024.7585bfaa.png)

#### [6]最终效果

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img025.9e3d577f.png)

### ③导入 Web 类型模块

其它操作和上面演示的都一样，只是多一步：删除多余的、不正确的 web.xml 设置。如下图所示：

![./images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img026.8dad97d2.png)

# 其他核心概念

## 1、生命周期

### ①作用

为了让构建过程自动化完成，Maven 设定了三个生命周期，生命周期中的每一个环节对应构建过程中的一个操作。

### ②三个生命周期

| 生命周期名称 | 作用         | 各个环节                                                     |
| ------------ | ------------ | ------------------------------------------------------------ |
| Clean        | 清理操作相关 | pre-clean clean post-clean                                   |
| Site         | 生成站点相关 | pre-site site post-site deploy-site                          |
| Default      | 主要构建过程 | validate generate-sources process-sources generate-resources process-resources 复制并处理资源文件，至目标目录，准备打包。 compile 编译项目 main 目录下的源代码。 process-classes generate-test-sources process-test-sources generate-test-resources process-test-resources 复制并处理资源文件，至目标测试目录。 test-compile 编译测试源代码。 process-test-classes test 使用合适的单元测试框架运行测试。这些测试代码不会被打包或部署。 prepare-package package 接受编译好的代码，打包成可发布的格式，如JAR。 pre-integration-test integration-test post-integration-test verify install将包安装至本地仓库，以让其它项目依赖。 deploy将最终的包复制到远程的仓库，以让其它开发人员共享；或者部署到服务器上运行（需借助插件，例如：cargo）。 |

### ③特点

- 前面三个生命周期彼此是独立的。
- 在任何一个生命周期内部，执行任何一个具体环节的操作，都是从本周期最初的位置开始执行，直到指定的地方。（本节记住这句话就行了，其他的都不需要记）

Maven 之所以这么设计其实就是为了提高构建过程的自动化程度：让使用者只关心最终要干的即可，过程中的各个环节是自动执行的。

## 2、插件和目标

### ①插件

Maven 的核心程序仅仅负责宏观调度，不做具体工作。具体工作都是由 Maven 插件完成的。例如：编译就是由 maven-compiler-plugin-3.1.jar 插件来执行的。

### ②目标

一个插件可以对应多个目标，而每一个目标都和生命周期中的某一个环节对应。

Default 生命周期中有 compile 和 test-compile 两个和编译相关的环节，这两个环节对应 compile 和 test-compile 两个目标，而这两个目标都是由 maven-compiler-plugin-3.1.jar 插件来执行的。

## 3、仓库

- 本地仓库：在当前电脑上，为电脑上所有 Maven 工程服务
- 远程仓库：需要联网
  - 局域网：我们自己搭建的 Maven 私服，例如使用 Nexus 技术。
  - Internet
    - 中央仓库
    - 镜像仓库：内容和中央仓库保持一致，但是能够分担中央仓库的负载，同时让用户能够就近访问提高下载速度，例如：Nexus aliyun

建议：不要中央仓库和阿里云镜像混用，否则 jar 包来源不纯，彼此冲突。

专门搜索 Maven 依赖信息的网站：https://mvnrepository.com/

