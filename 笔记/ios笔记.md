# static
```
一.修饰局部变量:
1)让局部变量只初始化一次;
2)局部变量在程序中只有一份内存;
3)并不会改变局部变量的作用域，仅仅是改变了局部变量的生命周期(只到程序结束，这个局部变量才会销毁)。
二.修饰全局变量:
全局变量的作用域仅限于当前文件。
```

http://www.cnblogs.com/allencelee/p/7169071.html

[ios 博客](http://blog.csdn.net/kmyhy/article/list/1)

[学英语](http://www.rupeng.com/Courses/Index/75?1801lianb)

[Xcode技巧](http://www.cocoachina.com/special/xcode/)
# swift
# 定义类 
```
格式
class 类名 : SuperClass {
	 // 定义属性和方法
}

class Student : NSObject {
	var age : Int = 0;
	var name : String?
	var money : Double = 0.0	
}

// 使用类
let stu = Student() // 创建对象
stu.age = 10;
stu.name = "who"
stu.money = 9999.9
```
### 定义变量
格式

```
var 变量名: 类型 = 值
```

### ? !的使用
声明变量时在类型后添加？或者！，就是告诉编译器这是一个Optional的变量，如果没有初始化，你就将其初始化位nil。

```
var a: String?  // a位nil
var b: String?  // b为nil
```

声明变量时用？只是单纯的告诉Swift这是Optional,如果没有初始化就默认为nil,而通过！，则之后对该变量操作的时候都会隐式的在操作前添加一个！。

 * 问号？
   * 声明时添加？，告诉编译器这个是Optional,如果声明时没有手动初始化，就自动初始化为nil。
   * 在对变量值操作前添加？，判断如果变量是nil,则不响应后面的方法。
  
 ```
var a: String? // 声明时加？ 初始化为nil
var b: String = "aa"
a = b?
```


 * 叹号！
  * 声明时添加！，告诉编译器这个是Optional,并且之后对该变量操作的时候，都隐式的在操作前添加！。
  * 在对变量操作前添加！，表示默认为非nil,直接解包进行处理。

[绘制画线教程](https://www.jianshu.com/p/bf7ebe563469)

#多线程 GCD
###1.任务
任务就是执行操作的意思，换句话说就是你在线程中执行的那段代码。在GCD中是放在block中的。执行任务有两种方式：同步执行和异步执行。两者的主要区别是：是否具备开启新线程的能力。

* 同步执行：只能在当前线程中执行任务，不具备开启新线程的能力。
* 异步执行：可以在新的线程中执行任务，具备开启新线程的能力。

###2.队列
这里的队列指任务队列，即用来存放任务的队列。队列是一种特殊的线性表，采用FIFO（先进先出）的原则，即新任务总是被插入到队列的末尾，而读取任务的时候总是从队列的头部开始读取。每读取一个任务，则从队列中释放一个任务。在GCD中有两种队列：串行队列和并行队列。

* 并行队列(concurrent dispatch queue)：可以让多个任务并行（同时）执行（自动开启多个线程同时执行任务）
  * 并行功能只有在异步（dispatch_async）函数下才有效
* 串行队列：(serial dispatch queue)让任务一个接着一个执行（一个任务执行完毕后，再执行下一个任务）
