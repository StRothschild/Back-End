## Java 与 JavaScript 的异同

### 不同点
- #### Java 是强类型语言， JavaScript 是弱类型语言
  ##### Java 既是一种静态语言，也是一种强类型定义的语言（类型安全的语言）。静态语言的数据类型是在编译其间检查的，也就是说在声明变量时，必须表明其数据类型。而数据类型一旦声明，除非进行强制转换，不然是不会改变的。


---
- #### Java 是编译执行， JavaScript 是解释执行



---
- #### Java 方法的参数数量必须和定义时的完全匹配， JavaScript 方法的参数数量不必完全匹配（默认为 null）




---
- #### 两者的变量默认值不同
```
/* Java 中的变量默认值 */
Byte、Short、Int、Long      // 0
Float f;                   // 0.0f
Double d;                  // 0.0d
Char c;                    // "" 或者 /u0000
Boolean b;                 // false
int[] a;                   // null
引用类型                    // null


/* JavaScript 中的变量默认值 */
所有 JavaScript 中的变量，默认值都为 undefined。
```




```
```
### 相同点
- #### 类名（Java）和 构造函数（JavaScript）均以大写开头
  ##### Java 中的类名 和 JavaScript 中的构造函数名，按照编码规范，都应该以大写字母开头（不强制）。
