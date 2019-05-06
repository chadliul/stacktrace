
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
        ArrayList默认大小10，增长倍数1.5倍；Vector 默认10，默认增长倍数2倍；Vector可以设置capacityIncrement调整增长大小
              
5.浅拷贝 深拷贝 clone
   * 浅拷贝、深拷贝是指一个概念上的区别，在针对只有一个基础数据类型的对象拷贝时，用clone()获取的这个对象就是深拷贝，如果这个对象内部还有引用数据类型，使用clone就是一次浅拷贝，因为引用类型没有拷贝
   
6.类的实例化顺序    
   先静态 再实例化 再构造函数，有父类先父类
   
7.MAP
  * HashMap
    * 数据结构是数组和链表，默认初始容量16，装载因子0.75
    * 解决hash冲突通过判断链表中的值。
    * jdk 1.8中过长链表会转红黑树(TREEIFY_THRESHOLD = 8)
    * < 1 扩容，即两倍方式扩容
    
  * ConcurrentHashMap
  * HashTable
  * TreeMap
  * LinkedHashMap
  * WeekHashMap
  
8. jdk 中 % / 操作 比 & 操作 慢 10 倍： https://bugs.java.com/bugdatabase/view_bug.do?bug_id=4631373
