# HTML 标签
* img标签
https://www.pornhub.com/view_video.php?viewkey=ph5a8cde569a4d2
```
img标签格式 <img src="">
src就是告诉img标签，需要显示的图片名称

<img scr="图片名称" height=“100” title="鼠标放在图片的描述文字" alt="没有图片的时候可以显示的内容">
```

* a标签 

a标签的作用,用于控制页面于页面之间跳转的

```
格式 <a href = "要跳转的网页">名称</a>
<a href="www.baidu.com"> 百度 </a>
```

* button 元素

```
<button type="button" onclick="alert('hello world')">click me</button>
```

# 文本格式
* <hi></hi> 1-6标题
* <p></p>段落
* <pre></pre>预定义文本

# 字符格式标签
* <b> </b> 加粗
* <i> </i> 斜体
* <big> </big> 放大

# 列表标签
* ul 无序列表
* ol 有序列表
* li list item


HTML 常见标签

* 标题: h1 h2 h3 h4 h5 h6
* 段落: p
* 换行: br
* 容器: div span(用来容纳其它标签)
* 表格: table tr td
* 列表: ul ol li
* 图片: img
* 表单: input输入框
* 链接: a




# CSS

## 外部样式

```
<link rel="stylesheet" href="index.css">
```

* style标签必须写在head标签的开始标签和结束标签之间（也就是和title标签是兄弟关系);
* style标签中的type属性其实可以不用谢，默认就是type=“text/css“;

1.规定文字样式的属性;
>默认为 font-style:normal;
>
>倾斜为 font-style:italic;

2.规定文字粗细的属性;
>font-weight:light;

>font-weight:bold;

3.规定文字的大小属性;
>font-size:30px;

4.规定文字的字体属性;
> font-family:"楷体";

> font-family:"微软雅黑";

>可以缩写为：
font:italic bold 40px "楷体";(size family不能省略否则没有效果)

* 1.文本装饰的属性
 
> text-decoration:underline; // 下划线
 
>text-decoration:through; // 删除线

> text-decoration:none; // 什么都没有 常用于超链接

* 2.文本对齐的属性

> text-align:center; // 居中

* 3.文本缩进的属性

> text-indent:2em;


# 标签选择器
* 作用：根据指定的标签名称，在当前界面中找到所有该名称的标签，然后设置属性。

```
格式 标签名称 {
	属性:值
}
 
<div>div1</div> // 红色

div {
color:red;
}

``` 

# id选择器 
* 每个HTML标签都有一个属性叫做id,也就是说每个标签都可以设置一个id；
* 在同一个界面中id的名称是不可以重复的；
* 在编写id选择器是一定要在id名称前面加上#；
* id的名称只能由字母、数字、下划线组成；
* id名称不能以数字开头；
* id的名称不能是HTML的名称

 ```
 #id名称 {
 	属性:值
 }
 
 <p id="first"> id选择器 </p> // 红色
 
 #first {
 color:red;
 }
 
 ```

# 类选择器
* 作用 根据指定的类名称找到对应的表情，然后设置属性。
 * 每个HTML标签都有一个属性叫做class;
 * 同一个界面的class名称可以重复；
 * 在编写class选择器时一定要class名称前面加上'.';
 * 类名就是专门给某个特定的标签设置样式的；
 * 在HTML中每个标签可以同时绑定多个类名；
 
 > 格式 class="类名1 类名2 ..."
 
```
.类名 {
属性：值
}

<p class="high"> 第一段文字 </p> // 红色
.high {
color:red;
}

```

# 并列选择器
```
<div class = "high"> 我是红色 </div>
div, .high {
	color:red;
}
```
凡是是容器的文字为红色 有high的为红色 二者皆有的也为红色

# 复合选择器
```
<div class = "yes"> div </div>
div.yes {
	color:red;
}
```
是容器必须也是yes类的文字才显示为红色

# 后代选择器
```
<div> 
	<p> div里的段落</p> // 显示红色
	<span> 
		<p>div里span里面的段落</p> // 显示红色
 	</span>
</div>
<p>外面的的段落</p> // 不为红色

div.p{
	color:red;
}
```

# 直接后代选择器
```
<div>
	<p>div里的段落</p> // 显示红色
	<span>
		<p>div里span里的段落</p> // 不为红色
	</span>
</div>
<p>外面的段落</p> //不为红色

div >p{
	color:red;
}

```

# 相邻兄弟选择器
```
<div>
	<p>div里面的段落</p> // 不为红色
	<span>
		<p>div里span里的段落</p> // 不为红色
	</span>
</div>
<p>外面的段落</p> // 红色
<p>外面的相邻的兄弟</p>  // 不为红色

div +p {
	color:red;
}
```

# 属性选择器
```
<div name="cjoe">属性选择器</div> // 红色
<div name="cj">属性选择器</div> // 红色

div[name]{
	color:red;
}

<div name="cjoe">属性选择器</div> // 红色
<div name="cj">属性选择器</div> // 不为红色

div[name="cjoe"] {
	color:red;
}
```

# 网页布局方式
* 标准流（文档流、普通流）排版方式
  * 浏览器默认的排版方式就是标准流的排版方式
  * 在css中将元素分为3类，分别是块级元素、行内元素、行内块级元素
  * 在标准流中有两种排版方式，一种是垂直排版，一种是水平排版。
     * 垂直排版，如果元素是块级元素，那么就会垂直排版。
     * 水平排版，如果元素是行内元素、行内块级元素，那么就会水平排版
   
* 浮动流排版方式
	* 半脱离标准流的排版方式
	* 只有一种排版方式，就是水平排版，它只能
* 定位流排版方式

