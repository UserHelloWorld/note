
# python 是强类型的动态语言

## 1 运算符
```
print(3 ** 5) // 幂运算
print(5 // 2) // 整除运算
print(5 / 2) 
print(not 1) // False
print(0 and False) // 0
print(1 and True) // True
print(True and 1) // 1
print(True or 1) // True
print(1 or True) // 1
// or先判断前面，符合不做后面的判断
// and 记录最后一次判断的答案

```

## 2 输出格式化

```
print("%d %d" % (12,23))
print("%(ms)d,%(es)d" % {"ms":123,"es":343}) // key值的方式
```

## 3 列表推导式
```
nums = [1, 2, 3, 4, 5]
results = [n for n in nums]
results2 = [n for n in nums if n % 2 != 0]

```

[王顺子](https://github.com/wangshunzi/Python_code)

[廖雪峰](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000)

[斗图](http://md.itlun.cn/a/gif/26876.html)
[各国首脑出场](http://url.cn/5ub3xn0)

### 代码块
* 当语句以冒号:结尾时，缩进的语句视为代码块。

### Python  if语句
格式：

```
if 判断条件:
	执行语句...
else:
	执行语句...
```
```
if 判断条件1:
	执行语句1...
elif 判断条件2:
	执行语句2...
elif 判断条件3:
	执行语句3...
else:
	执行语句4...
```
### 循环
* while循环
	* 格式为
	
	```
	while 判断条件:
	执行语句...
	
	```
	```
	count = 0
	while (count < 9):
		print count
		count = count + 1
	```

* for循环
	* 格式为
	
	```
	for iten in sequence:
		
	```

### 函数
* 函数代码块以def关键词开头，后接函数标识符名称和圆括号()。
* 任何传入参数和自变量必须放在圆括号中间，圆括号之间可以用于定义参数。
* 函数的第一行语句可以选择性的使用
* 定义格式:

```
	def 函数名(参数):
	print ("133")	
```

* 闭包

```
def test():
	def test2():
		print(123)
	return test2

funcName = test() # 返回了一个函数名
funcName() # 函数使用
```
* 装饰器

```
def test(func):
	def inner():
		print("abc")
		func()
	return inner
@test #等效于 start = test(start)
def start():
	print("123")
start()

# 带参数装饰器
# 返回一个装饰器
def getzsq(a):
	def test(func):
		def inter():
			func()
			print(a)
			print("123")
		return inter
	return test
# @getzsq(333) # 等效于 star = getzsq(333)(star)
def star():
	print(1)
star()
```

* 递归函数

```
# 功能：如果不直接知道结果的数据，进行分解
# 知道结果就返回
# 递归一定有传递和回归,要不然会死循环
def jiecheng(n):
    if n == 1: # 递归函数的结束条件
        return 1
    return  n * jiecheng(n - 1)
print(jiecheng(5))
```

### 字符串
* 原始字符串
```
str = r"\n\b\ddsdsldssd"
```
* 拼接字符串

```
# 1 
a = "abc" + "abc"
print(a)
# 2
b = "%s%s"%("abc","bcd") 
print(b)
#3
c = "sz\t"*10
print(c)
```
* 切割字符串

```
name = "abcdefg"
print(name[4:1:-3])
print(name[::-1]) 
# 步长默认为1 起始默认值为0 结束len(name)长度
# 每次加上步长，正数加正数，负数加负数
print(name[0:len(name):2]) # 步长为2 步长大于0 从左到右，否则右到左

```

### 类
* 创建类
class 类名(可写继承类):

```
class Person:
	pass
	
p = Person() # 创建对象
p.age = 10 # 给对象添加属性
```


