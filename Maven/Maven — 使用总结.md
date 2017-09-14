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
