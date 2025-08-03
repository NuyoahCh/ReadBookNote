<h1 id="mVojA"> 简介</h1>
<h2 id="VprJK">并发简史</h2>
早期计算机不包含操作系统，从头到尾只执行一个程序的方式过于浪费资源，随着 OS 的引入，使得计算机每次可以运行多个程序，主要目的是：

**1.资源利用率：**如果在等待的同时可以运行另外一个程序，无疑提高资源的利用率

**2.公平性：**不同的用户对于计算机资源有着同等使用权

**3.便利性：**计算多个任务时，应该编写多个程序，每个程序执行并发时需要通信

线程被称为轻量级进程，大多数现代操作系统以线程为基本调度单位，如果没有明确的**协同机制**，线程彼此独立进行，没有协同对共享数据进行访问，那么当一个线程正在使用某个变量时，另外一个线程也可能正在访问，造成不可预测的结果

<h2 id="INuPG">线程的优势</h2>
使用得当，降低程序开发和维护等成本，同时提高复杂应用程序的性能

线程还可以简化 JVM 的实现，垃圾收集器通常在一个或者多个专门的线程中运行

<h3 id="Wi8OH">发挥多处理器的强大能力</h3>
使用多线程助于单处理器上获取更高的吞吐量，如果程序单线程，当程序等待某个同步 I/O 操作完成，处理器处于空闲状态。而在多线程程序，等待 I/O 程序时，另外一个线程可以正常运行

<h3 id="FKvsm">建模的简单性</h3>
为了防止多线程多任务并发带来的复杂性，我们通过使用线程，可以将复杂并且异步的工作流进一步分解成为一组简单并且同步的工作流，每个工作流在一个单独的线程中运行，并在特定的同步位置进行交互

<h3 id="gv7dk">异步事件的简化处理</h3>
为降低开发难度，很多连接中都分配其各自线程并使用同步 I/O，但是存在线程被阻塞、所有请求停顿的问题，因此之前要求单线程必须使用非阻塞 I/O 避免此类问题，因此操作系统提供了一些高效的方法实现多路 I/O，例如：select、poll 和 epoll 等系统调用

但在现代操作系统中，线程数量得到了极大的提升，为每一个客户端分配一个线程优势和也是可行的

<h2 id="WUgd5">线程带来的风险</h2>
Java 对线程的支持是一把双刃剑。

Java 提供了丰富的语言和库，以及一种明确的跨平台内存模型，这些工具简化了并发应用程序的开发，但是同时提高了对开发人员的技术要求

<h3 id="gi3cd">安全性问题</h3>
线程安全性是十分复杂的，在没有充分同步的情况下，多个线程中的操作执行顺序是不可预测的

```java
@NotThreadSafe
public class UnsafeSequence {

    private int value;

    /**
     * 返回一个唯一的值
     */
    public int getNext() {
        return value++;
    }
}

```

单线程执行的正确性是毫无悬念的，就是很简单的初始化数值，调用方法，读取 `value`，将数值增加

![画板](https://cdn.nlark.com/yuque/0/2025/jpeg/45054063/1753938396991-01be82e8-90f6-4230-b22d-ced8f510e1a5.jpeg)

但是多线程调用这个方法的时候，不同线程的调用返回了相同的数值

这是一种常见的并发安全问题，也称为竞态条件，在多线程环境下，`getValue`是否会返回唯一的值，要取决于运行时线程中操作的交替执行方案，目前并不是我们想要看到的

```java
@ThreadSafe
public class Sequence {

    @GuardedBy("this")
    private int value;

    /**
     * 返回一个唯一的值
     */
    public synchronized int getNext() {
        return value++;
    }
}
```

`synchronized`关键字，对于多线程并发安全起到了重大作用

<h3 id="h3dBs">活跃性问题</h3>
在开发并发代码的时候，一定要注意线程安全性是不可破坏的

安全性不仅仅对于多线程并发问题十分重要，对于单线程问题 也应该同样重视，比如活跃性问题

活跃性问题的形式之一就是无意造成的无限循环，从而使循环之后的代码无法得到正确执行，也就是我们说的死锁

<h3 id="sz5fS">性能问题</h3>
设计良好的并发应用程序中，线程能够有效的提升程序的性能，但是无论如何，线程总会带来某种程序的运行时开销，多线程程序中，当线程调度器临时挂起活跃线程并转而运行另外一个线程恢复，会频繁出现上下文切换，带来极大的性能开销，丢失局部性，CPU 时间更多的花在线程调度而不是线程运行上

<h2 id="nt9En">线程无处不在</h2>
即使程序中没有显示的创建线程，但是框架中也可能会进行线程的创建

JVM 启动时，将 JVM 的内部任务创建后台线程，并创建主线程来运行 mian 方法

<h1 id="j2RCf">线程安全性</h1>
编写线程安全的代码时，核心在于对状态访问操作进行管理，特别是对共享和可变的状态的访问

+ 共享意味着变量可以由多个线程同时进行访问
+ 可变意味着变量值在其生命周期内发生变化

一个对象是否需要是线程安全的，取决于它是否被多个线程进行访问

Java 中的主要同步机制的关键字 `synchronized`，它提供了一种独占的加锁方式，同步这个术语还包括 `volatile` 类型的变量，显式锁（`Explicit Lock`）以及原子变量

:::tips
如果多个线程访问同一个可变的状态变量时，没有使用合适的同步，那么程序就会出现错误，有三种方式可以修复这个问题：

+ 不在线程之间共享该状态变量
+ 将状态变量修改为不可变的变量
+ 在访问状态变量时使用同步

:::

如果在设计的时候就没有考虑并发安全的问题，那么采用上述方法可能需要对设计进行重大的修改；如果一开始就设计一个线程安全类，那么比在以后再将这个类修改为线程安全的要容易的多

:::tips
当设计线程安全的类时，良好的面向对象技术、不可修改性，以及明晰的不变性规范都能起到一定的帮助作用

:::

有时候，面向对象中的抽象和封装会降低程序的性能（尽管很少有开发人员相信）

编码的正确方式就是：首先保证代码正确运行，再去提高代码的速度

**Java8 源码实例：**

```java
    /**
     * The array buffer into which the elements of the ArrayList are stored.
     * The capacity of the ArrayList is the length of this array buffer. Any
     * empty ArrayList with elementData == DEFAULTCAPACITY_EMPTY_ELEMENTDATA
     * will be expanded to DEFAULT_CAPACITY when the first element is added.
     */
    transient Object[] elementData; // non-private to simplify nested class access
```

+ ArrayList 源码中的 elementData 数组就是 Object[] 类型，并没有封装成一堆对象。这样做是为**性能让步，牺牲了封装性**。

```java
    /**
     * Basic hash bin node, used for most entries.  (See below for
     * TreeNode subclass, and in LinkedHashMap for its Entry subclass.)
     */
    static class Node<K,V> implements Map.Entry<K,V> {
        final int hash;
        final K key;
        V value;
        Node<K,V> next;

        Node(int hash, K key, V value, Node<K,V> next) {
            this.hash = hash;
            this.key = key;
            this.value = value;
            this.next = next;
        }

```

+ Java 的 HashMap 实现中，Node<K,V> 是静态内部类而非接口，减少了动态分派。



**Java21 源码实例：**

```java
    /**
     * The array buffer into which the elements of the ArrayList are stored.
     * The capacity of the ArrayList is the length of this array buffer. Any
     * empty ArrayList with elementData == DEFAULTCAPACITY_EMPTY_ELEMENTDATA
     * will be expanded to DEFAULT_CAPACITY when the first element is added.
     */
    transient Object[] elementData; // non-private to simplify nested class access
```

```java
    /**
     * Basic hash bin node, used for most entries.  (See below for
     * TreeNode subclass, and in LinkedHashMap for its Entry subclass.)
     */
    static class Node<K,V> implements Map.Entry<K,V> {
        final int hash;
        final K key;
        V value;
        Node<K,V> next;

        Node(int hash, K key, V value, Node<K,V> next) {
            this.hash = hash;
            this.key = key;
            this.value = value;
            this.next = next;
        }
```

尽管很少有开发人员相信的原因：

1. **现代 JVM 足够智能**（JIT 编译器会做逃逸分析、方法内联、锁消除等优化）；
2. **现代计算资源足够强**，大多数 OOP 带来的性能损耗**不会成为瓶颈**；
3. **大部分程序瓶颈都在 I/O、网络、数据库，而不是 CPU 内部函数调用**；
4. **软件工程更关注可维护性、可扩展性、团队协作能力**，这才是 OOP 真正解决的问题。

如果你必须打破封装，那么并非不是不可以，仍然可以实现线程的安全性，只是对于更加困难

<h2 id="pEJh1">什么是线程安全性</h2>
在线程安全性的定义中，最核心的概念就是正确性

当多个线程访问某个类时，这个类始终都能表现出正确的行为，那么这个类就是线程安全的

:::tips
当多线程访问某个类时，不管运行时环境采用何种方式调度方式或者是这些线程将如何交替执行，并且在主调代码中不需要任何额外的同步或者协同，这个类都能表现出正确的行为，那么就称为这个类是线程安全的

:::

```java
public class StatelessFactorizer implements Servlet {
    public void service(ServletRequest request, ServletResponse response) {
        // No state is maintained, so this method can be called concurrently
        // by multiple threads without synchronization.
        BigInteger i = extractFromRequest(request);
        BigInteger[] factors = factor(i);
        encodeIntoResponse(response, factors);
    }
}
```

