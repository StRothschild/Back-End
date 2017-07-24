## JavaBean 的概念
- #### JavaBean 本质就是一个类。

- #### JavaBean 是符合特定规则的类：
  #####  1. 这个类中所有的数据属性都是 private 的私有属性，每一个私有属性都有两个 public 的方法，分别是 getter 和 setter 方法，用于获取和更改属性。
  #####  2. 提供一个缺省（默认）的 public 构造函数。
  #####  3. 可序列化，实现serializable接口。

- #### 所以 JavaBean 不是一种技术，而是一种规范。符合这种规范可以使得类被其他程序或者框架使用，所以每个 JavaBean 都是一个可重用的软件构件。

```Java
/* 标准的 Java Bean */
package test.pojo;

public class Foo {
  private Stirng name;
  private int age;

  public String getName() {
    return name;
  }
  public void setName(String name) {
    this.name = name;
  }

  public int age() {
    return age;
  }
  public void setName(int age) {
    this.age = age;
  }
}
```




---
#### 1. JavaBean 的第一个用途就是为了给 jsp 页面传递数据，简化交互过程。
```jsp
/* 标准的 Java Bean */
<jsp:useBean id="user" scope="page" class="test.pojo.Foo"/>

<jsp:getProperty property="name"/>
<jsp:getProperty property="age"/>

<jsp:setProperty property="name"/>
<jsp:setProperty property="age"/>
```


---
#### 2. JavaBean 的第二个用途就是映射数据库中的表结构。
##### 类似于 POJO，JavaBean 可以广泛的用于分层开发的数据交换。
```
