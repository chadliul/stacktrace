
# 基础数据类型

| type| bit|
|:----: | :-----:| 
|byte  | 8位|
|short | 16位|
|int   |32位 |
|long  | 64位|
|float |  32位|
|double|  64位|
|char  |  16位|
|boolean|  1位|

# 常用包

* java.lang  核心类String  Math System 和 Thread类等

* java.util  常用工具类，concurrent包着重注意

* java.net 网络通信

* java.io  io,File Read Write

* java.sql jdbc相关

## 相关知识点

1.String类有final修饰，不可变，不能被继承
   
2.final修饰的类不能被继承， final修饰的方法不能被覆盖， final 修饰的变量不可改， static final 修饰的是唯一不可改
   
3.String StringBuffer StringBuilder
  * String 操作都是在重新生成字符串
  * StringBuffer 操作是在原字符串后添加，添加synchronized
  * StringBuilder 非线程安全
  
4.List, ArrayList, LinkedList, Vector
   
  * 数据结构
    * ArrayList Vector数组，删除操作需要移位
    * LinkedList 双向链表
    * 数据结构决定效率，中间插入时LinkedList效率O(n)，查询都是O(n)
  * 线程安全
    * ArrayList, LinkedList都不是线程安全的，多并发使用建议使用Collections中synchronizedList() 调用
    * Vector线程安全，基本操作有synchronized
  * 扩容机制
    * ArrayList Vector 都是数组，增加元素数组长度不够时会扩容
    * ArrayList默认大小10，增长倍数1.5倍；Vector 默认10，默认增长倍数2倍；Vector可以设置capacityIncrement调整增长大小
              
5.浅拷贝 深拷贝 clone
   * 浅拷贝、深拷贝是指一个概念上的区别，在针对只有一个基础数据类型的对象拷贝时，用clone()获取的这个对象就是深拷贝，如果这个对象内部还有引用数据类型，使用clone就是一次浅拷贝，因为引用类型没有拷贝
   
6.类的实例化顺序    
   先静态 再实例化 再构造函数，有父类先父类
   
7.MAP
  * HashMap
    * 数据结构是数组和链表，默认初始容量16，装载因子0.75
    * 解决hash冲突通过判断链表中的值。
    * jdk 1.8中过长链表会转红黑树(TREEIFY_THRESHOLD = 8)
    * << 1 扩容，即两倍方式扩容
    
  * ConcurrentHashMap
    * 数据结构是数组和链表，默认初始容量是16，装载因子0.75
    * 1.7 数组segment继承ReentrantLock, 其中HashEntry volatile修饰，保证获取时的可见性。此方案使其有分段锁的能力，不会和HashTable一样put、get都是同步操作。且支持CurrencyLevel(Segment数量)的并发，每个线程占用锁访问segment时不会影响其他Segment，未解决遍历链表慢问题
    * 1.8 放弃segment，采用cas + synchronized保证并发
    * 链表长度超过TREEIFY_THRESHOLD = 8 转红黑树
     
  * HashTable
    * 数组和链表，默认出事容量11，装载因子0.75
    * 线程安全，操作中都有synchronized
  * TreeMap
    * 数组和红黑树
    * 以key大小顺序存储
  * LinkedHashMap
    * 数组和链表 转红黑树，继承 HashMap
    * 保证插入顺序
  * WeekHashMap
    * 特点：WeakReference 会被jvm 做gc时 删除entry
    * 使用场景：缓存
  
8.jdk 中 % / 操作 比 & 操作 慢 10 倍： https://bugs.java.com/bugdatabase/view_bug.do?bug_id=4631373

9.transient 关键字
   * transient 只能修饰变量，不能修饰方法、类
   * 被修饰变量不再是对象持久化的一部分
   * 被修饰的变量不在被序列化
   
10.Abstract Interface
   * 抽象类可以有默认方法，interface 在java8之前没有，java8后有了default
   * 继承抽象类使用extends，实现interface使用implement
   * 子类不是抽象类的需要实现父类抽象类，子类实现interface父类时需要实现所有方法
   * 子类可以实现多个interface，子类只能继承一个抽象类
   
11.继承 实现 聚合 组合 
   * 子类继承父类功能，并可以扩展其他能力  extends
   * 实现：指class 实现interface相关功能
   * 依赖：是指A用到了B，关系较弱
   * 关联：A与B有领域间关联关系，如1对多、多对多关系，关系较强
   * 聚合：强调整体与部分、拥有的关系即has - a关系
   * 组合：强聚合，提现的是contain - a关系 

12.泛型
   * 泛型设计原则，只要编译期没有出错，就不会报classNotFund错误
   * 把类型明确的工作推迟到创建对象或者调用方法的时候确认的特殊类型
   * 早起java中使用Object来作为任意类型传递，但是向下强转是有问题的
   * 作用：代码简洁、增加可读性和稳定性

13.反射
   * 在运行状态中，对于任何一个类，我们都可以获取到其方法和属性，对于任何一个对象我们都可以获取其方法和属性进行调用。动态获取对象信息并且和调用对象方法的功能称为反射机制
   * 反射本质就是获取类的字节码文件，也就是.class文件
   * 反射创建类实例：Class.forName() 找不到会报ClassNotFundException;.getClass() 该方法已知道类，无卵用；.class方式需要导入依赖
   
14.动态代理  静态代理  cglib

15. exception error 
 
             
