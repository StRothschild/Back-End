## Java 基础知识

- #### Java 以 .java 文件为编译单元
  ##### 1. .java 文件中可以有多个类，但最多只能有一个 public 类，并且如果 .java 文件中存在一个 public 类，则类名必须与文件名完全相同。
  ##### 2. 每个类在编译后都会输出一个 .class 文件，所以一个 .java 文件编译后可能输出多个 .class 文件。
  ```java
  /* Foo.java */
  public class Foo {
    public static void main(String[] args) {
      System.out.println("Hello World!");
    }
  }

  class Bar1 {}
  class Bar2 {}
  // foo.java 编译后输出 3 个 class 文件，分别是 Foo.class、Bar1.class 和 Bar2.class
  ```


- #### Java 中各个类型的默认值
  ```java
  byte(位)          0
  short(短整数)      0
  int(整数)          0
  long(长整数)       0L
  float(单精度)      0.0
  double(双精度)     0.0
  char(字符)        空
  boolean          flase
  对象              null
  ```


- #### Java 中的等于
  ```Java
  equals
  equalsIgnoreCase
  ==
  ===
  ```




- #### FileReader 和 FileInputStream
  ##### FileReader 用于读取字符数据，FileInputStream 用于读取二进制数据。
  
  
  
  
- #### Java8 中的 forEach、filter、map
  ##### 用 stream 方法可以获取当前 Collection 对象的流对象，结合 lambda 表达式，可以联合 forEach、filter、map 方法一起使用。




- #### super
##### 子类中的执行 super 方法可以调用执行父类的构造函数。
