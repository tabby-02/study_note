# 1.XML定义

XML 指可扩展标记语言（EXtensible Markup Language）。
XML 是一种很像HTML的标记语言。
XML 的设计宗旨是传输数据，而不是显示数据。
XML 标签没有被预定义。您需要自行定义标签。

```xml
<?xml version="1.0" encoding="UTF-8"?><!--不必需-->
<?xml-stylesheet type="text/css" href="xxxx.css"?><!--使用css样式表显示xml--不必需-->
<?xml-stylesheet type="text/xsl" href="xxxx.xsl"?><!--使用xsl样式表显示xml--不必需-->
<!DOCTYPE xxx SYSTEM "xxxx.dtd"><!--DTD验证--不必需-->
<根元素>
    <xxx></xxx>
    </根元素>
```

# 2.语法

0.XML 文档必须有一个**根元素**

1.XML 标签对大小写敏感

2.所有的 XML 元素都**必须有一个关闭标签**。（声明不是 XML 文档本身的一部分，它没有关闭标签。）

3.属性值**必须加引号**（单/双），属性值不能包括 <,>,&，如果一定要包含，也要使用实体

4.在 XML 中，有 5 个预定义的实体引用：

| &lt;   | <    | less than      |
| ------ | ---- | -------------- |
| &gt;   | >    | greater than   |
| &amp;  | &    | ampersand      |
| &apos; | '    | apostrophe     |
| &quot; | "    | quotation mark |

5.注释：<!-- This is a comment -->

6.在 Windows 应用程序中，换行通常以一对字符来存储：回车符（CR）和换行符（LF）。
在 Unix 和 Mac OSX 中，使用 LF 来存储新行。
在旧的 Mac 系统中，使用 CR 来存储新行。
**XML 以 LF 存储换行**。

# 3.元素命名

## XML 命名规则

XML 元素必须遵循以下命名规则：

- 名称可以包含字母、数字以及其他的字符
- 名称**不能以数字或者标点符号开始**
- 名称**不能以字母 xml（或者 XML、Xml 等等）开始**
- 名称**不能包含空格**

# 4.验证

## 1.DTD

DTD 的目的是定义 XML 文档的结构。用法：引用外部dtd文件/直接写在xml中

```xml
<!DOCTYPE 根元素名 SYSTEM "DTD文件名.dtd">
```

```xml
<!DOCTYPE note [
  <!ELEMENT note (to,from,heading,body)>
  <!ELEMENT to      (#PCDATA)>
  <!ELEMENT from    (#PCDATA)>
  <!ELEMENT heading (#PCDATA)>
  <!ELEMENT body    (#PCDATA)>
]>
```



## 2.Schema

W3C 支持一种基于 XML 的 DTD 代替者

# 5.XML JS

## 1.XMLHttpRequest 对象

xmlhttp=new XMLHttpRequest();	// code for IE7+, Firefox, Chrome, Opera, Safari

xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");	// code for IE6, IE5

## 2.XML DOM

### 1.加载XML文件

xmlhttp=new XMLHttpRequest();	生成对象（非IE）
xmlhttp.open("GET","xxxx.xml",false);	打开文件
xmlhttp.send();	发送数据
xmlDoc=xmlhttp.responseXML;	接收数据
xmlDoc.getElementsByTagName("to")[0].childNodes[0].nodeValue	返回xml数据

```js
//创建xmlhttp对象
if (window.XMLHttpRequest)
{// code for IE7+, Firefox, Chrome, Opera, Safari
xmlhttp=new XMLHttpRequest();
}
else
{// code for IE6, IE5
xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
}
//通过xmlhttp对象打开xml并保存到xmlDoc
xmlhttp.open("GET","xxxx.xml",false);
xmlhttp.send();
xmlDoc=xmlhttp.responseXML;
//使用xmlDoc中的xml数据
document.getElementById("to").innerHTML=
xmlDoc.getElementsByTagName("to")[0].childNodes[0].nodeValue;
document.getElementById("from").innerHTML=
xmlDoc.getElementsByTagName("from")[0].childNodes[0].nodeValue;
document.getElementById("message").innerHTML=
xmlDoc.getElementsByTagName("body")[0].childNodes[0].nodeValue;
```

### 2.加载XML字符串

txt="xml格式的内容";	创建xml字符串
parser=new DOMParser();	
xmlDoc=parser.parseFromString(txt,"text/xml");	接收数据(非IE)
xmlDoc.getElementsByTagName("to")[0].childNodes[0].nodeValue;	返回xml数据

```js
txt="<note>";
txt=txt+"<to>Tove</to>";
txt=txt+"<from>Jani</from>";
txt=txt+"<heading>Reminder</heading>";
txt=txt+"<body>Don't forget me this weekend!</body>";
txt=txt+"</note>";

if (window.DOMParser)// code for Firefox, Chrome, Opera, Safari
{
parser=new DOMParser();
xmlDoc=parser.parseFromString(txt,"text/xml");
}
else // code for Internet Explorer
{
xmlDoc=new ActiveXObject("Microsoft.XMLDOM");
xmlDoc.async=false;
xmlDoc.loadXML(txt);
}

document.getElementById("to").innerHTML=
xmlDoc.getElementsByTagName("to")[0].childNodes[0].nodeValue;
document.getElementById("from").innerHTML=
xmlDoc.getElementsByTagName("from")[0].childNodes[0].nodeValue;
document.getElementById("message").innerHTML=
xmlDoc.getElementsByTagName("body")[0].childNodes[0].nodeValue;
```

# 6.XML进阶

## 1.XML命名空间