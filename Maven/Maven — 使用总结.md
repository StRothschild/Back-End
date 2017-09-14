## Maven 使用总结
- #### Maven 的概念
  ##### Maven 主要有两个功能：依赖管理、打包管理
  http://blog.csdn.net/hjiacheng/article/details/57413933


---
- #### 将依赖手动添加入本地仓库
  ##### 一般来说依赖会通过 POM 的配置，从中央仓库同步到本地仓库中。以可用通过命令行手动添加依赖到本地仓库中。
  ```
  /* 通过命令行手动添加 D:\dubboCustomer.jar 到本地仓库中 */
  mvn install:install-file -Dfile=D:\dubboCustomer.jar -DgroupId=com.netease.newsadminweb -DartifactId=dubboCustomer -Dversion=1.0.0 -Dpackaging=jar -DgeneratePom=true -DcreateChecksum=true

  /* 该命令的各个参数意义如下 */
  -Dfile = 依赖所在路径  
  -DgroupId = 包名  
  -DartifactId = 项目名  
  -Dversion = 版本号  
  -Dpackaging = 依赖文件类型，一般是 jar  


  /* 通过 POM 将依赖引入 */
  <dependency>
    <groupId>com.netease.newsadminweb</groupId>
    <artifactId>dubboCustomer</artifactId>
    <version>1.0.0</version>
  </dependency>
  ```



---
- #### 直接在 Maven 项目中引用依赖
  ##### 如果依赖没有在中央仓库和本地仓库中，也可以通过配置 POM 来直接引用依赖
  ```

  ```



---
- #### Maven 属性
  ```
  /* Maven 的内置属性，可以在 POM 中直接使用 */
  ${basedir} 和 ${project.basedir} 表示项目根目录，即包含pom.xml文件的目录;
  ${version} 和 {project.version} 表示项目版本;
  ${project.baseUri} 表示项目文件地址;
  ${maven.build.timestamp} 表示项目构件开始时间;
  ${maven.build.timestamp.format} 表示属性 ${maven.build.timestamp} 的展示格式，默认值为 yyyyMMdd-HHmm



  /* POM 文件属性 */
  ${project.build.directory} 表示主源码路径;
  ${project.build.sourceDirectory} 表示主源码路径;
  ${project.build.sourceEncoding} 表示主源码的编码格式;
  ${project.build.finalName} 表示输出文件名称;



  /* settings 文件属性 */
  与 POM 属性同理，可以引用 settings.xml 文件中的XML元素值
  ${settings.localRepository} 表示本地仓库的地址;



  /* 自定义属性 */
  在 POM 文件的 <properties> 标签下也可以定义 Maven 属性
  <project>
    <properties>
      <test>test</test>
    </properties>
  </project>
  通过以上设置，就可以在其他地方使用 ${test} 引用该属性




  /* Java 系统属性 */
  所有的 Java 系统属性都可以使用 Maven 属性引用，使用 mvn help:system 命令可查看所有的 Java 系统属性，System.getProperties()可得到所有的Java属性;
  ${user.home} 表示用户目录;




  /* 环境变量属性 */
  使用 mvn help:system命令可查看所有环境变量
  ${env.JAVA_HOME} 表示 JAVA_HOME 环境变量的值;
  ```

http://www.cnblogs.com/xdouby/p/6502925.html
