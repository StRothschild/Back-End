## Java 多线程

```java
public class TestCallable {
    public static void main(String[] args) {
        ExecutorService exec = Executors.newCachedThreadPool();   //工头
        Future<String> result = exec.submit(new CallableTask());  //submit返回一个Future，代表了即将要返回的结果
        try {
            // 主线程挂起1秒,期间Callable子线程会继续执行
            Thead.sleep(1000);
            // 1秒后主线程继续执行
            if (result.isDone()) {
                System.out.println(result.get());
            }
         } catch (Exception e) {
              System.out.println(e.toString());
         }
    }
}

// 实现 Callable 接口
public class CallableTask implements Callable<String> {
    public String call() {
        return "result of CallableTask!";
    }
}
```
