## Tomcat 的概念

- #### Artifact 的概念
  ##### Artifact 可以理解为 tomcat 用于部署的一个包。主要有两种模式 war 和 war explorded。war 模式：将 WEB 工程以包的形式上传到服务器。war exploded 模式：将WEB工程以当前文件夹的位置关系上传到服务器。

  ##### 1. war 模式这种可以称之为是发布模式，就这是先打成 war 包，然后放到 Tomcat 中发布；

  ##### 2. war exploded （破裂）模式是直接把文件、jsp页面、class 等内容拷贝到 Tomcat 部署文件夹里面，进行加载部署。这种方式支持热部署，一般在开发的时候也是用这种方式。



---
- #### 三种 Connector

  ##### HTTP Connector
  ##### HTTPS Connector
  ##### AJP Connector

  http://blog.csdn.net/u010297957/article/details/50782212




---
- ####  Tomcat 配置 URL 访问地址
  ##### Tomcat 安装路径下有一个 webapps 目录，在这个目录下放置的项目，可以通过 Tomcat 直接访问。如果项目不在该目录下，可以通过配置 server.xml 来添加一个虚拟地址与实际地址的映射来实现项目的访问。
  ##### Tomcat 的 webapps 目录中，以文件夹的方式来区分各个项目，在访问这些项目时，就是通过项目所在的文件夹名称作为 url 路径的一部分，例如：主机地址 + 项目文件夹名称 + 项目根路径。但有一个例外，就是 ROOT 文件夹下面的项目，可以直接使用 "主机地址 + /" 的方式来访问。
  ##### 除此之外，还可以通过配置 server.xml 来实现项目的访问。在 <Host> 标签中，添加 <Context path="" docBase="D:/myApp/webapp"/>，这样也可以通过 "主机地址 + /" 来访问到指定的项目。

  
http://blog.csdn.net/qq_33189295/article/details/50513935
http://www.linuxidc.com/Linux/2011-12/48939.htm
https://www.zhihu.com/question/54757013
