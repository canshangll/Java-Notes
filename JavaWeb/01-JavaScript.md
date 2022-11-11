# JavaScript

浏览器支持就可以使用得语言

**语法**

```js
<script type="text/javascript" src="1.js">
	....//编写逻辑代码   //如果src 已经引用则只会用 1.js里面的逻辑代码
</script>
```

## JS变量

**变量类型**

- 数值类型:number
- 字符串类型:string
- 对象类型:object
- 布尔类型:boolean
- 函数类型:function

**特殊的值**

- undefined:未定义,所有js变量未赋于初始值的时候，默认值都是undefined
- null:空值
- NAN:全称是:Not a Number.非数字，非数值。

**定义变量**

- var 变量名;
- var 变量名=值;

## 关系(比较)运算符-常用

等于: == 等于是简单的做字面值的比较
全等于: === 除了做字面值的比较之外,还会比较两个变量的数据类型

## 逻辑运算符

在JavaScript语言中,所有的变量,都可以做为一个boolean类型的变量去使用.
0、null、undefined、""(空串) 都认为是false

- &&且运算: (有两种情况)
  - 第一种:当表达式全为真的时候。返回最后一个表达式的值。
  - 第二种:当表达式中,有一个为假的时候.返回第一个为假的表达式的值
- ||或运算
  - 第一种情况:当表达式全为假时,返回最后一个表达式的值
  - 第二种情况:只要有一个表达式为真.就会把回第一个为真的表达式的值

并且&&与运算 和 ||或运算 有短路
短路就是说,当这个&&或||运算有结果之后。后面的表达式不在执行

## 数组

JavaScript数组的定义:
	var 数组名 = [];//空数组
	var 数组名 = [1,'abc',true];//定义数组同时赋值元素

## 函数

函数有两种定义方式

- **第一种,可以使用function关键字来定义函数**
  - 语法：
    	function 函数名(形参列表){
            函数体
        }
- **第二种**
  - 语法：
    	var 函数名 = function (形参列表){
            函数体
        }

注：在Java中允许函数重载。但在JavaScript中函数的重载会直接覆盖掉上一次的定义.

隐形参数arguments(只在function函数内)

在function函数中不需要定义,但却可以直接用来获取所以参数的变量，叫隐形参数。
隐形参数特别像java基础的可变长参数一样。
public void fun(Object ...args);
可变长参数其实是一个数组
JavaScript中的隐形参数也跟java的可变参数一样。操作类似数组

## 自定义对象

**Object形式的自定义对象**

对象的定义:
	var 变量名 = new Object();	//对象实例(空对象)
	变量名.属性名 = 值	//定义一个属性
	变量名.函数名 = function(){}	//定义一个函数
对象的访问:
	变量名.属性 / 函数名();

**花括号形式自定义对象**

对象的定义:
	var 变量名 = {	//空对象
        属性名 : 值,	//定义一个属性
        属性名 : 值,	//定义一个属性
        函数名 : function(){}	//定义一个函数
    };	
对象的访问:
	变量名.属性 / 函数名();

## 事件

**常用的事件**

- onload加载完成事件:	页面加载完成之后,常用于做页面js代码初始化操作
- onclick单击事件:	常用于按钮的点击响应操作
- onblur失去焦点事件:	常用用于输入框失去焦点后验证其输入内容是否合法
- onchange内容改变事件:	常用于下拉列表和输入框内容发送改变后操作
- onsubmit表单提交事件:	常用于表单提交前,验证所有表单项是否合法

**事件的注册(静态注册和动态注册)**

静态注册事件:通过HTML标签的事件属性直接赋于事件响应后的代码,这种方式叫静态事件
动态注册事件:是指先通过js代码得到标签的dom对象,然后再通过dom对象.事件名 = function(){} 这种形式赋于事件响应后的代码,叫动态注册
	动态注册基本步骤:
		1、获取标签对象
        2、标签对象.事件名 = function(){}

## DOM模型

DOM 全称 Document Object Model 文档对象模型
把文档中的标签，属性，文本，转换成对象来管理

- Document它管理了所有的Html的文档内容
- document它是一种树结构的文档。有层级关系
- 它让我们把所有的标签都对象化
- 我们可以通过document访问所有的标签对象

```java
<body>
    <div id="div01">
        div01
    </div>
</body>
模拟对象化，相当于
class Dom{
	private String id; //id属性
    private String tagName; //表示标签名
    private Dom parentNode; //父亲
    private List<Dom> children; //孩子结点
	private String innerHTML; //起始标签和结束标签中间的内容
}
```

### Document对象中的方法介绍

- document.getElementById(elementId)
  通过标签的id属性查找标签dom对象,elementId是标签的id属性值
- document.getElementsByName(elementName)
  通过标签的name属性查找标签dom对象,elementName 标签的name属性值
- document.getElementsByTagName(tagname)
  通过标签名查找标签dom对象.tagname是标签名
- document.createElement(tagName)
  通过给定的标签名,创建一个标签对象.tagName是要创建的标签名

//注：
document 对象的三个查询方法，如果有id属性，优先使用getElementById方法来进行查询
如果没有id属性，则优先使用 getElementsByName方法来进行查询
如果id属性和name属性都没有最后再按标签名查询getElementsByTagName
以上三个方法，一定要在页面加载完成之后执行，才能查询到标签对象

**属性**

- childNodes属性,获取当前节点的所有子节点
- firstChild属性,获取当前节点的第一个子节点
- lastChild属性,获取当前节点的最后一个子节点
- parentNode属性,获取当前节点的父节点
- nextSibling属性,获取当前节点的下一个节点
- previousSibling属性,获取当前节点的上一个节点
- className属性,用于获取当前节点的上一个节点
- innerHTML属性,表示获取/设置起始标签和结束标签中的内容
- innerText属性,表示获取/设置起始标签和结束标签中的文本