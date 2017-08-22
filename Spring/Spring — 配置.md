## Spring 的配置

---
- #### 配置文件中的通配符 *
```javascript
/* 配置文件中的通配符 * 和 ** 代表了不同含义 */

// 单个 * 只匹配路径下的所有文件，例如 /resources/test.html   但是不会匹配目录
<mvc:resources mapping="/resources/*" location="/resources/" />

// 两个 ** 可以同时匹配路径下的所有文件和目录，例如 /resources/folder 和 /resources/test.html
<mvc:resources mapping="/resources/**" location="/resources/" />
```
