## Java 的安装与环境配置
1. #### JRE 与 JDK
   ##### JRE（Java Runtime Environment）指的就是 Java 运行环境。主要有两个部分，JVM 和 Java 类库的 class 文件。JVM 就是 Java虚拟机，提供了运行 class 文件的运行环境，屏蔽了不同硬件平台之间的差异，实现 Java 跨平台运行的能力。Java 类库的 class 文件都在 lib 目录下，并且都已经打包成了 jar 包。需要注意的是，JER 只提供运行环境，无法编译。所以无法用于开发调试。  

   ##### JDK（Java Development ToolKit）指的就是 Java 开发工具套装。它不但包涵了 JRE（jre文件夹下），还包括了编译器（javac.exe）、从源码注释中提取文档的文档生成器（javadoc.exe）、将相关的类文件打包成一个文件的打包工具（jar.exe）、性能跟踪工具（jconsole.exe）以及更多的类库（如 dt.jar、tools.jar）。JDK 提供的是一套完整的 Java 编译和运行环境，可以用于开发。

  ![JDK结构](https://github.com/StRothschild/Back-End/blob/master/resource/Java%20%E2%80%94%20JDK%20%E7%BB%93%E6%9E%84.png?raw=true)
  
  ![JRE&JDK关系](https://github.com/StRothschild/Back-End/blob/master/resource/Java%20%E2%80%94%20JRE&JDK.jpg?raw=true)



---   
2. #### 下载 JDK
  ##### https://www.java.com/zh_CN/

---   
3. #### 安装 JDK
  ##### 在安装 JDK 时，会有两次安装，分别是 JRE 的安装和 JDK 的安装。安装地址一般默认，也可以自定义。这个安装地址需要配置环境变量，所以不能搞错。

---   
4. #### 配置环境变量
  ##### 安装完 JDK 后，需要对系统的环境变量进行配置，帮助命令（比如 javac）可以被正确的查找。

  - ##### 在环境变量中先配置一个变量 JAVA_HOME，用于定义 JDK 的安装路径，例如：JAVA_HOME = 'C:\Program Files\Java\jdk1.8.0_152'

  - ##### 配置完变量 JAVA_HOME 之后就可以在别的变量值中引用，例如 %JAVA_HOME%

  - ##### 环境变量 PATH 的作用就是指定命令的搜索路径。为了使得 Java 的命令执行程序可以被找到，需要在 PATH 变量的值中添加 "%JAVA_HOME%\bin;"  因为包括 javac 命令的执行程序 javac.exe 在内的以及其他的一些 Java 命令执行程序都放在 bin 目录下。

  - ##### 环境变量 CLASSPATH 的作用就是指定类的搜索路径。要使用类（class），就需要配置 CLASSPATH 来指定查找的目录。如果 CLASSPATH 没有配置，Java 会在默认在"当前路径"查找，如果设置了 CLASSPATH 则会按照 CLASSPATH 值来寻找。所以在 CLASSPATH 变量的值中添加 ".;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;" 其中的 "dt.jar" 和 "tools.jar" 都是第三方的类库，而第一个点代表了是"当前路径"，非常重要，不能漏掉。
