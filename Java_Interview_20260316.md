# Java 每日面试题备份 (2026-03-16)


## --- 前天内容：集合与基础 ---

### 1. ArrayList 和 LinkedList 的区别？
- **ArrayList**：基于动态数组，随机访问快（O(1)），插入删除慢（需要移动元素）。
- **LinkedList**：基于双向链表，插入删除快（O(1)），访问慢（需遍历）。

### 2. 说说 Java 里的异常体系？
- **Throwable** 是顶层，分为 **Error**（系统级错误，如 OOM）和 **Exception**。
- Exception 分为 **编译时异常**（必须处理）和 **运行时异常**（RuntimeException，如 NullPointerException）。

### 3. == 和 equals() 的区别？
- **==**：比较基本类型是值，比较引用类型是内存地址。
- **equals()**：默认比较地址，但很多类（如 String, Integer）重写了它，用于比较内容是否相等。

### 4. String, StringBuilder, StringBuffer 的区别？
- **String**：不可变，适合少量操作。
- **StringBuilder**：可变，线程不安全，单线程下效率最高。
- **StringBuffer**：可变，线程安全（加了 synchronized 锁）。

### 5. 重载 (Overload) 和 重写 (Override) 的区别？
- **重载**：同名不同参，发生在一个类中。
- **重写**：同名同参，发生在子类对父类方法的覆盖。

## --- 昨天内容：并发与锁机制 ---

### 6. 线程的创建方式有哪些？
- 继承 `Thread` 类。
- 实现 `Runnable` 接口（推荐，解耦）。
- 实现 `Callable` 接口（有返回值，可抛异常）。
- 利用**线程池**创建。

### 7. synchronized 和 ReentrantLock 的区别？
- **synchronized**：关键字，自动加锁释放锁，不可响应中断。
- **ReentrantLock**：API 层面，手动加锁释放锁，支持公平锁、响应中断、多条件变量（Condition）。

### 8. 什么是死锁？如何预防？
- **死锁**：两个线程互相等待对方释放资源。
- **预防**：按顺序加锁、设置超时时间、尽量减少锁的嵌套。

### 9. volatile 关键字的作用？
- **可见性**：保证一个线程修改变量后，其他线程立即看到。
- **有序性**：禁止指令重排序。但它**不保证原子性**。

### 10. sleep() 和 wait() 的区别？
- **sleep()**：属于 Thread 类，**不释放锁**。
- **wait()**：属于 Object 类，**释放锁**，通常用于线程间通信（需在 synchronized 块中使用）。