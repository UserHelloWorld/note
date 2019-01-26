[ios重要资源](https://github.com/aozhimin/awesome-iOS-resource) 

[iOS抢红包软件](https://github.com/AsTryE/QQRedPackHelper)

[多target](https://www.jianshu.com/p/23cc84d40423)

[倒计时](http://www.cocoachina.com/ios/20161011/17722.html)

### [微信tableView索引](https://github.com/TalkingJourney/SCIndexView)

### 在工程文件夹如果是有两个相同类，没有导入也会报重复定义错误

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

[swift中文](http://special.csdncms.csdn.net/the-swift-programming-language-in-chinese/index.shtml)

# OC
### copy 与 mutableCopy
#### 集合类对象是指NSArray、NSDictionary、NSSet ...之类的对象。
#### 非集合类对象是指NSString、NSNumber ...之类的对象。

* 非集合对象
* 对于不可变对象copy,浅拷贝，mutableCopy深复制。
* 对于可变对象mutableCopy,copy,深拷贝。
* 集合对象
* 对于不可变对象copy，浅拷贝，mutableCopy深拷贝
* 对于可变集合对象,无论是mutableCopy或者Copy都是深拷贝

strong 和 Copy的区别。要把NSString类型字符串赋值时，两者没区别。NSMutableString，strong会跟着变化，Copy做了深拷贝不会变
[strong与copy区别](http://blog.csdn.net/itianyi/article/details/9018567)

### weak 和 assign的区别
* assign指针所指向的内存被释放掉（释放不等于抹除，只是引用计数为0），不会自动赋值nil,这样再引用self.assignPoint就会导致野指针操作，如果这个操作发生时内存还没有改变内容，依旧可以输出正确的结果，而如果发生时内存内容被改变了，就会crash。

### 分类
* 1. 分类只能增加方法,不能增加成员变量(添加成员变量使用会崩溃)
* 2.分类中写property只会生成方法声明
* 3.分类可以访问原来类中的成员变量
* 4.如果分类的方法与原有类的方法同名,主函数在执行的话会优先分类的方法,原来类中的方法会被忽略.主要看方法调用的优先级.一般式分类-原来类-父类.(可以自己调节)(一般在开发中我们不推荐)

总结：分类的属性只是set、get方法申明，并没有成员变量的赋值，而继承类的属性会自动有成员变量的赋值

#### property (属性)
用property声明的成员属性，相当于生成了setter getter方法，重写了set和get方法，与@property生命的成员属性就不是一个成员属性了，是另外一个实例变量，而这个实例变量需要手动声明。

是同时重写了set和get方法后就与@property声明的成员属性不是同一个属性了

```
类声明
@interface ViewController : UIViewController

@property (copy, nonatomic) NSString *last;

@end


类实现
@implementation ViewController
// 一定要合成，否则set get找不到成员变量
@synthesize last = _last;

- (NSString *)last {
return _last;
}

- (void)setLast:(NSString *)last {
_last = last;
}

```



# swift


### 字符串

```
// 把值转换成字符串的方法：把值写到括号中，并且在括号之前写一个反斜杠。
let a = 3
let b = 4
let str = "I have \(a) apples"
let str1 = "I have \(a + b) oranges"


var str = "hwww"
str = "abc"
print(str.count) // 字符串长度

let a = "abc"
let b = "ddd"

// 字符串拼接 \(变量名)
let c = "\(a)\(b)"
print(c)
let min = 3
let sec = 4

// 字符串拼接
let tStr = String(format: "%02d:%02d", min,sec)
print(tStr)


```

### 数组

```
// 方式1
//let array:Array <String> = ["abc"]
// 方式2
let array:[String]  = ["a","b"]
print(array)
// 方式3
var arr = Array <String> ()

arr.append("abc")
arr.append("abc")
print(arr)
arr.remove(at: 0)
print(arr)
// 下标和元素
for (index,item) in arr.enumerated() {
print(index,item)
}

let arr1 = ["abc","bbb"]
let arr2 = ["ds","dss"]
// 相同元素可以合并，不同元素不能合并
let arr3 = arr1 + arr2
print(arr3)

```

### 字典

```
// 字典使用

// 使用
let dict:[String:Any] = ["a":"b","age":14]

var dicM = [String:Any]()

print(dict,dicM)

// 增加元素
dicM["name"] = "abc"
dicM.updateValue(123, forKey: "name")
dicM.updateValue("abc", forKey: "ab")

print(dicM)
for value in dicM.values {
print(value)
}
for (key,value) in dicM {
print(key,value)
}

```

### 元组

```
// 元组
// 方式1
let tuple1 = ("abc",12)

// 方式2
let tuple2 = (name:"1",age:2,h:232)
print(tuple2.age,tuple2.name)

// 方式3
let (name,age,height) = ("abf",33,32)

print(name,age,height)
```

### 可选类型

```
// 方式1
var name: Optional <String> = nil
// 方式2
var name1:String? = nil // 简化方式1 等价的

// 可选赋值1
name = Optional("aaa")
// 可选赋值2
name1 = "a"
print(name,name1)

// name! 强制解包

// 可选绑定（固定格式）
if let name = name {
print(name)
}

```

### as 用法

```
// 将一种类型转换成另一种类型 as后接类型
let str:String = "abc"
let nsStr = str as NSString

// as? 转成可选类型
// as! 转成具体类型

let dict:[String:Any] = ["age":12,"name":"xiao"]

let tempName = dict["name"]

let name = tempName as? String

if let name = name { // 可选绑定
print(name)
}

// 可选绑定直接直接转
if let name = dict["name"] as? String {
print(name)
}


```


### for in 遍历
```
// 只遍历不需要第几次可以用'_' 过滤
for _ in 0...3 {
// 打印四次,0和3之间不能使用空格，必须不间断
}

for i in 0..<3 {
// 打印3次
}
```

### 函数
```

func test() -> Void {
print("test")

}
// 等同于（没有返回值可以省略->Void）
func test1() {
print("test")
}

// 多参数
func sum(numbers: Int...) -> Int {
var s = 0
for num in numbers {
s += num
}
return s
}

sum(10,20,30)
```

### 枚举

```
enum MType {
case get
case post
case put
case delete
}
// 创建枚举
let type:MType = MType.get

// 给枚举赋值
enum NumType : Int{
case east = 1
case west = 2
case north = 3
case south = 4
}
enum StrType : String {
case A = "ab"
case B = "bc"
case C = "dd"
}

// 直接定义
enum TestType {
case a,b,c,d,e
}

```


### 定义变量

格式

```
var 变量名: 类型 = 值

var a:Int = 12
var b:Bool = true

```
* 类型转换

```
let a : Double = 20.5
let b : Int = 10
// 类型后接括号
let c = Double(b) + a

```

### guard使用

```
// 使用方式
// 1 guard一般用在函数 
// 2 必须要有else语句

// 跟if 一样的判断
//    guard 条件判断 else {
//        return
//    }
let a = 20

func online() {

guard a > 10 else {
// 不满足条件 return
return
}
// 满足条件 
}
```

### switch 

```
let a = 10
switch a {
case 10:
print("a")
fallthrough // 穿透到下一次
case 11:
print(1)
fallthrough // 继续穿透到下一次
default:
print("a")
}

```

### 闭包 （closure）
* 语法

```
{ (参数) -> 返回类型 in 
}

例如：
let block = { (a: Int, b: Int) -> Int in
return a + b
}
let result = block(10,20)


// 逃逸闭包
/*
当一个闭包作为参数传到一个函数中，但是这个闭包在函数返回之后才被执行，我们称为闭包从函数中逃逸。当定义接受闭包作为参数的函数时，你可以在参数名之前标注@escaping,用来指明这个闭包是允许逃逸出这个函数的。
*/

var array:[()->Void] = []

func completionFunc(closure: @escaping ()->Void) {
array.append(closure)
}


```

### 结构体

```
// 1 定义结构体
struct Location {
// 成员属性
var x : Double
var y : Double
var z : Double
// 方法
func test() {
print("结构体方法")
}
// 改变成员属性，必须加上mutating(变化)
// 如果不想在调用方法提示参数名可以在前面加上 _
mutating func add(_ newValue:Double) {
x = newValue
print(x)
}
// 3 系统会为每一个结构体提供一个默认的构造函数，并且该构造函数要去给每一个成员属性进行赋值
// 构造函数以 init开头，并且不需要返回值
// 在构造函数结束时，必须保证所有的成员属性有被初始化
//    // 系统默认实现
//    init(x:Double,y:Double,z:Double) {
//        self.x = x
//        self.y = y
//        self.z = z
//    }
// 扩充构造函数
init(xyzStr:String) {
let array = xyzStr.components(separatedBy: ",")
let item1 = array[0]
let item2 = array[1]
let item3 = array[2]

// 先判断前面可选类型是否有值解包 否则使用后面的值
x = Double(item1) ?? 0
y = Double(item2) ?? 0
z = Double(item3) ?? 0
}

}
// 2 创建结构体
// 注意 如果创建了一个结构体的实例并将其赋值给一个常量，则无法修改该实例的任何属性，即使有属性被声明为变量也不行。（这种行为是由于结构体属于值类型，当值类型的实例被声明为常量的时候，它的所有属性也就成了常量） 
// 补充：引用类型不一样，把一个引用类型的实例赋值给一个常量后，仍然可以修改实例的变量属性。
// 使用系统构造函数
//var center = Location(x: 20, y: 30, z: 40)
var center = Location.init(xyzStr: "1,2,3")
center.test()
center.add(10)
print(center.x)

```


# 定义类 
```


class Person : NSObject{
var name: String = "" {
willSet(nw) {
print(name)
}
didSet {
print(name)
}
}
// 类属性
static var Count : Double?
// 自己定义构造函数防止覆盖系统的构造函数重写
override init() {

}
init(dict:[NSString:Any]) {
//        if let name = dict["name"] as? String {
//            self.name = name
//        }
super.init()
setValuesForKeys(dict as [String : Any])

}

}

格式
// 可以不继承
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

### copy 与 mutablCopy 
| 原对象 | 拷贝方法 | 副本对象类型 | 是否产生新对象 | 拷贝类型|
|:-:|:-:|:-:|:-:|:-:|:-:|
|NSArray|copy|NSArray|NO|浅拷贝|
|NSArray|mutableCopy|NSMutableArray|YES|深拷贝|
|NSMutableArray|copy|NSArray|YES|深拷贝|
|NSMutableArray|mutableCopy|NSMutableArray|YES|深拷贝|
