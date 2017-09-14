## Maven 使用总结
- #### Maven 的概念
  ##### Maven 主要有两个功能：依赖管理、打包管理
  http://blog.csdn.net/hjiacheng/article/details/57413933






---
- #### Maven 仓库的配置和生效顺序

1.pom.xml里的repositories元素，里面可以包含多少repository(至少默认包含了中央仓库，仓库id为central，可以写个id为central的mirror或者repository覆盖默认的中央仓库，该仓库总是在effective-pom里repositories元素的最后一 个子元素),每个repository都有一个id(此id非常重要)，命令行执行：mvn help:effective-pom可以验证


2.maven获取真正起作用的repository集合流程：首先会获取pom.xml里的repository集合，然后在settings.xml里找mirrors元素，如果repository的id和mirror的mirrorOf的值相同，则该mirror替代该repository，如果该repository找不到对应的mirror，则使用其本身，依此可以得到最终起作用的repository集合


3.关于maven如何查找pom.xml里dependencies里配置的插件，暂且不考虑本地仓库的存在（笔者注：应该是先查找本地的仓库，如果本地仓库查找不到，再通过repository里面配置的仓库进行查找），maven会根据最终的repository集合里依次查找，如果查到了就从该仓库下载，并且停止对后续repository的查找(找到了就停)。所以可以看出用户在pom.xml里配置repository时，repository的顺序还是挺重要的。


4.注：从超级父pom里继承来的中央repository在effective-pom里总是为最后一个repository.

5.对于寻找reposiotry的mirror的一些理解：
在settings.xml里配置mirror里，应该将<mirrorOf></mirrorOf>放在最后一个最好这么做





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






---
- #### POM 中的 exclusions
  ##### 由于 Maven 会根据依赖自动加载依赖的依赖，实现了依赖的自动管理。但有些时候会引入同一依赖的不同版本，这可能会造成了包冲突而导致编译失败。这时就可以通过 exclusions 的设置来避免某些依赖的加载。
  ```
  /* 通过以下方式可以避免 */
  <exclusions>
      <exclusion>
          <groupId>javassist</groupId>
          <artifactId>javassist</artifactId>
      </exclusion>
  <exclusions>
  ```
