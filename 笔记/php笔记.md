[php官方文档](http://php.net/manual/zh/langref.php)

[W3CPHP语法](http://www.w3school.com.cn/php/php_syntax.asp)

##语法
php脚本可放置于文档中的任何位置

PHP脚本以<?php开头， 以?>结尾

```
<?php 
	// 此处写PHP代码
?>
```

PHP文件默认文件扩展名是 .php。
PHP文件通常包含HTML标签以及一些PHP脚本代码。

```
<!DOCTYPE html>
<html>
<body>
<?php 
	echo 'hello world';
?>
</body>
</html>
```

### php大小写敏感
在PHP中，所有用户自定义的函数、类和关键词（例如if、else、echo等等）都对大小写不敏感。

```
<!DOCTYPE html>
<html>
<body>
<?php 
	ECHO "hello world";
	echo "hello world";
	EcHo "hello world";	
?>
</body>
</html>

运行的结果都一样
```

不过在PHP中，所有变量都对大小写敏感。


## 变量
PHP没有创建变量的命令

变量会在首次为其赋值时被创建

```
例如：
<?php 
	$txt = "hello world";
	$x = 5; 
	$y = 10.6
?>
```

php是一门类型松散的语言

* 在上面的例子中，请注意我们不必告知PHP变量的数据类型。
* PHP根据它的值，自动把变量转换为正确的数据类型。
* 在诸如c语言之类，必须在变量声明前声明它的类型


### PHP变量作用域
* 在PHP中，可以在脚本的任意位置对变量进行声明。
* 变量的作用域指的是变量能够被引用/使用的那部分脚本。
* PHP有三种不同的变量作用域：
	* local （局部）
	* global （全局）
	* static （静态）


local和global 作用域
函数之外声明的变量拥有global作用域，只能在函数之外进行访问。
函数内部声明的变量拥有local作用域，只能在函数内部进行访问。

```
<?php 
	$x = 5; // 全局作用域（global）
	function myTest () {
		$y = 10; // 局部作用域（local）
		echo $x;
		echo $y;
	}
	myTest();
	echo $x;
	echo $y;
?>

运行的到的结果为 函数内部会报一个未定义x，打印y = 10;
函数外可以打印x,报未定义y通知

```

#### PHP global关键词
global 关键词用于函数内访问全局变量

要做到这一点，请在（函数内部）变量前面使用global关键词

```
<?php 
	$x = 5;
	$y = 10;
	function myTest () {
		global $x,$y;
		$y = $x + $y;
	}
	myTest();
	echo $y; // 输出15；
?>
```

#### php static 关键词
通常，当函数完成/执行后，会删除所有变量。不过，有时我需要不删除某个局部变量。实现这一点需要更进一步的工作。要完成这一点，声明变量时使用static关键词。

```
<?php 
	function myTest() {
		static $x = 0;
		echo $x;
		$x++;
	} 
	myTest();
	myTest();
	myTest();
	myTest();
	myTest();
	
?>

结果为 0 ，1 ，2, 3, 4
```


#### PHP字符串
字符串可以是引号内的任何文本。您可以使用单引号或者双引号。

```
<?php 
	$x = "hello world";
	echo $x;
	$x = 'hello world';
	echo $x;
?>
打印结果都是一样
```

#### PHP函数
PHP的真正力量来自它的函数：它拥有超过1000个内建的函数。

PHP用户自定义函数

* 除了内建的函数，我们可以创建自己的函数。
* 函数是可以在程序中重复的语句块。
* 页面加载时函数不会立即执行。
* 函数只有在被调用时才会执行。

用户自定义的函数声明以‘function’开头：

```
语法 
function 方法名() {
   // 被执行的代码
}
```

多参数

```
<?php 
	function test($name,$year) {
		echo "$name $year";
	}
	test("li","1324");
?>
```

PHP默认参数值

```
<?php 
	function setHeight($height=50) {
		echo "$height";
	}
	setHeight(350);
	setHeight(); // 默认值为50
?>
```

PHP函数返回值

```
<?php 
	function sum($x,$y){
		$z = $x + $y;
		return $z;
	}
   echo sum(5,10);
?>
```


#### PHP数组
数组能够在单独的变量名中存储一个或多个值

```
<?php
	$car = array("aaa","bbb","ccc");
	echo $car[0].$car[1].$car[2];
?>
输出为aaabbbccc
```

PHP创建数组

```
在PHP中，array（）函数用于创建数组
array();
```

* PHP三种数组类型
 * 索引数组 - 带有数字索引的数组
 * 关联数组 - 带有指定键的数组
 * 多维数组 - 包含一个或多个数组的数组
 
PHP索引数组
  
  1）自动分配（索引从0开始）
  
  ```
  $cars = array("aaa","bbb","ccc");
  ```
  
  2) 手动分配索引
  
  ```
  $cars[0] = "aaa";
  $cars[1] = "bbb";
  $cars[2] = "ccc";
  ```
  
获得数组的长度 - count()函数

```
<?php 
	$cars = array("aaa","bbb","ccc");
	echo count($cars);
?>
结果为3
```

PHP关联数组

```
$age = array("peter"=> "35","ben"=>"37","joe"=>"42");
```

或者

```
$age['peter'] = "35";
$age['ben'] = "37";
$age['joe'] = "42";
```

遍历关联数组

```
遍历关联数组使用foreach循环
<?php 
	$ages = array("bill"=>"34","steve"=>"32,"peter"=>"33");
	foreach($ages as $x=>$x_value) {
		each "key = ".$x.".Value=".$x_value;
	}
?>

```




## 类
### class
每个类的定义都以关键字class开头，后面跟着类名，后面跟着一对花括号，里面包含有类的属性与方法的定义。

一个类可以包含有属于自己的常亮，变量（称为属性）以及函数(称为方法)。

```
<?php 

	class MyClass {
	
	// 属性声明
	pubulic $abc = 'a default value';
	// 方法声明
	public function testMethod () {
		echo $this ->abc;
	}
	
	}

?>
```

### new
要创建一个类的实例，必须使用new关键字。当创建新对象时该对象总是被赋值，除非该对象定义了构造函数并且在出错时抛出了一个异常。类应用在被实例化之前定义（某些情况下则必须这样）。

```
<?php 
	$instance = new MyClass();
	// 也可以这样做
	$className = 'Foo';
	$instance = new $className(); // Foo()
?>
```

### null
null无，表示没有值，null不表示空格，也不表示0；以下情况，则认为是null:

* 没有设置为任何预定义的变量;
* 明确的赋值为null;
* 使用函数unset()清除;


### 双引号可以解析变量

```
<?php 
	$love = "I love you";
	$string1 = "xxx,$love"; // 双引号
	$string2 = 'xxx,$love'; // 单引号
	$string3 = 'xxx,{$love}'; // 加花括号更加好看明确
	echo $string1;  // 输出 xxx, I love you
	echo $string2;  // 输出 xxx, $love
	echo $string3;  // 输出 xxx, I love you
?>
```






# 基础语法
```
<?php 
   // 此处是PHP代码
?>
```

* 注释

```
	# 这是单行注释（脚本注释）
	// 单行注释
```

* PHP变量
 * 变量以$符号开头，其后是变量的名称；
 * 变量名称必须以字母或下划线开头；
 * 变量名称不能以数字开头；
 * 变量名称对大小写敏感
 
 ```
 <?php
    $text = "hello world";
    $x = 5;
    $y = 10.4;
 ?>
 ```
 
### PHP字符串
字符串可以是引号内的任意文本。用单引号或双引号都行。

```
<?php 
	$str = "hello world";
	echo $str;
	echo "</br>"
	$str = 'hello world';
	echo $str;
	echo strlen("aabbccdd123"); // 返回字符串的长度
?>
```


### php数组
在PHP中，array()函数用于创建数组。

```
<?php 
	$arr = array("aa","bb","cc");
	echo $arr[0]
?>
```

### PHP函数定义
语法格式

```
function functionName() {
	// 被执行的代码
}
多参数的函数
<?php 

	function familyName($name) {
	echo "$name.<br>";
	}
	familyName("xiao");
?>
返回值的函数
<?php 
	function sum($x,$y) {
		$z = $x + $y;
		return $z;
	}
   echo sum(2,5);
?>

```


### 使用关键字static修饰的方法，成为静态方法，静态方法不需要实例化对象，可以通过类名直接调用，操作符为双冒号::。
```
class Car {
	public static function getName() {
		return '汽车';
	}
}
echo Car::getName(); // 结果为'汽车'
```


#### 域运算符号(::) this self parent三个关键字
[详细](http://blog.csdn.net/skynet001/article/details/7518164)