#### HTMLHint 使用指南

#### 一、使用（命令行）

1.1 安装**HTMLHint**所需的依赖包

> npm install htmlhint -g

检测htmlhint版本使用如下命令

> htmlhint -V

如需其他帮助使用如下命令

> htmlhint —help

(**help前面是两个短横线)

1.2 配置文件

将文件夹中的`.htmlhintrc` 文件拷贝到你的项目根目录下

1.3 让HTMLHint运行起来

使用如下命令进行HTML代码检测

> htmlhint www
> 
> htmlhint www/test.html
> 
> htmlhint www/\**/\*.xhml
> 
> htmlhint www/\**/\*.{htm,html}

举个栗子，检测结果格式如下：

``` javascript
test.html
      L5 |    </head>
              ^ <title> must be present in <head> tag. (title-require)
      L8 |    </body>
              ^ Tag must be paired, missing: [ </div> ], start tag match failed [ <div> ] on line 7. (tag-pair)

2 errors in 1 files
```

#### 二、Rules

2.1 Standard

- [tagname-lowercase](https://github.com/yaniswang/HTMLHint/wiki/Tagname-lowercase)

**定义**：所有的标签需要小写。

**警告级别**：`error`

正确写法：

``` html
<span><div>
```

错误写法

``` html
<SPAN><DIV>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



- [attr-lowercase](https://github.com/yaniswang/HTMLHint/wiki/Attr-lowercase)

**定义**：所有的属性名需要小写

**警告级别**：`error`

正确写法：

``` html
<img src="test.png" alt="test">
```

错误写法

``` html
<img SRC="test.png" ALT="test">
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



- [attr-value-double-quotes](https://github.com/yaniswang/HTMLHint/wiki/Attr-value-double-quotes)

**定义**：属性值需要使用双引号包围

**警告级别**：`error`

正确写法：

``` html
<a href="" title="abc">
```

错误写法

``` html
<a href='' title=abc>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



- [attr-value-not-empty](https://github.com/yaniswang/HTMLHint/wiki/Attr-value-not-empty)

**定义**：属性值不能为空，也就是说所有的属性都需要设置一个属性值

**警告级别**：`warning`

正确写法：

``` html
<input type="button" disabled="disabled">
```

错误写法

``` html
<input type="button" disabled>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则

​	

- [attr-no-duplication](https://github.com/yaniswang/HTMLHint/wiki/attr-no-duplication)
  
  **定义**：标签内的属性不能够重复
  
  **警告级别**：`error`
  
  正确写法：
  
  ``` html
  <img src="a.png" />
  ```
  
  错误写法
  
  ``` html
  <img src="a.png" src="b.png" />
  ```
  
  **配置选项**
  
  `true`:激活该规则
  
  `false`: 禁止使用该规则
  
  ​
  
- [doctype-first](https://github.com/yaniswang/HTMLHint/wiki/Doctype-first)

**定义**：Doctype 必须写在最前面

**警告级别**：`error`

正确写法：

``` html
<!DOCTYPE HTML><html>
```

错误写法

``` html
<!--comment--><!DOCTYPE HTML><html>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



- [tag-pair](https://github.com/yaniswang/HTMLHint/wiki/Tag-pair)

**定义**：标签需要成对出现

**警告级别**：`error`

正确写法：

``` html
<ul><li></li></ul>
```

错误写法

``` html
<ul><li></ul>
<ul></li></ul>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



- [tag-self-close](https://github.com/yaniswang/HTMLHint/wiki/Tag-self-close)

**定义**：空标签需要自闭合

**警告级别**：`warning`

正确写法：

``` html
<br />
```

错误写法

``` html
<br>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



- [spec-char-escape](https://github.com/yaniswang/HTMLHint/wiki/Spec-char-escape)

**定义**：特殊字符需要转义

**警告级别**：`error`

正确写法：

``` html
<span>aaa&gt;bbb&lt;ccc</span>
```

错误写法

``` html
<span>aaa>bbb<ccc</span>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



- [id-unique](https://github.com/yaniswang/HTMLHint/wiki/Id-unique)

**定义**：整个HTML文档ID值必须唯一，也就是说ID值不能够重复

**警告级别**：`error`

正确写法：

``` html
<div id="id1"></div><div id="id2"></div>
```

错误写法

``` html
<div id="id1"></div><div id="id1"></div>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



- [src-not-empty](https://github.com/yaniswang/HTMLHint/wiki/Src-not-empty)

**定义**：src属性不能够为空，包含src属性的标签有`img` `script` `link` .

**警告级别**：`error`

正确写法：

``` html
<img src="test.png" />
<script src="test.js"></script>
<link href="test.css" type="text/css" />
<embed src="test.swf">
<bgsound src="test.mid" />
<iframe src="test.html">
<object data="test.swf"> xxxxxxxxxx <span><div>
```

错误写法

``` html
<img src />
<script src=""></script>
<script src></script>
<link href="" type="text/css" />
<link href type="text/css" />
<embed src="">
<embed src>
<bgsound src="" />
<bgsound src />
<iframe src="">
<iframe src>
<object data="">
<object data>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



- [title-require](https://github.com/yaniswang/HTMLHint/wiki/title-require)

**定义**：tittle标签需要写在head标签内部

**警告级别**：`error`

正确写法：

``` html
<html><head><title>test</title></head></html>
```

错误写法

``` html
<html><head></head></html>
<html><head><title></title></head></html>
<html><title></title><head></head></html>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则

2.2 Performance

- [head-script-disabled](https://github.com/yaniswang/HTMLHint/wiki/Head-script-disabled)

**定义**：script标签不能够放在head标签内部

**警告级别**：`warning`

正确写法：

``` html
<body><script type="text/javascript" src="test.js"></script></body>
```

错误写法

``` html
<head><script type="text/javascript" src="test.js"></script></head>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则

2.3 Accessibility

- [alt-require](https://github.com/yaniswang/HTMLHint/wiki/alt-require)

**定义**：`img` `input` `area` 变迁内部的`alt`属性不能省略

**警告级别**：`warning`

正确写法：

``` html
<img src="test.png" alt="test">
<input type="image" alt="test">
<area shape="circle" coords="180,139,14" href ="test.html" alt="test" /> xxxxxxxxxx <html><head><title>test</title></head></html>
```

错误写法

``` html
<img src="test.png">
<input type="image">
<area shape="circle" coords="180,139,14" href ="test.html" />
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



2.4 Specification

- [doctype-html5](https://github.com/yaniswang/HTMLHint/wiki/Doctype-html5)

**定义**：必须使用html5的Doctype

**警告级别**：`warning`

正确写法：

``` html
<!DOCTYPE HTML><html>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



- [id-class-value](https://github.com/yaniswang/HTMLHint/wiki/Id-class-value)

**定义**：ID值或者class值需要匹配一些规则：underline、dash、hump

**警告级别**：`waring`

正确写法：

``` html
underline: <div id="aaa_bbb">
dash: <div id="aaa-bbb">
hump: <div id="aaaBbb">
```

错误写法

``` html
<html><head></head></html>
<html><head><title></title></head></html>
<html><title></title><head></head></html>
```

**配置选项**

`underline`:采用下划线的蛇形命名（aaa_aa）

`dash`: 采用短线连接的方式命名（aaa-aa）

`hump`:采用驼峰命名（aaaBaa）

`false`:禁止使用该规则



- [style-disabled](https://github.com/yaniswang/HTMLHint/wiki/Style-disabled)

**定义**：禁止使用`style`标签

**警告级别**：`warning`

错误写法

``` html
<head><style type="text/css"></style></head>
<body><style type="text/css"></style></body>
<html><title></title><head></head></html>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



- [inline-style-disabled](https://github.com/yaniswang/HTMLHint/wiki/inline-style-disabled)

**定义**：禁止使用行内标签

**警告级别**：`warning`

错误写法

``` html
<div style="color:red"></div>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



- [inline-script-disabled](https://github.com/yaniswang/HTMLHint/wiki/inline-script-disabled)

**定义**：禁止使用行内脚本

**警告级别**：`warning`

错误写法

``` html
<img src="test.gif" onclick="alert(1);">
<img src="javascript:alert(1)">
<a href="javascript:alert(1)">test1</a>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



- [space-tab-mixed-disabled](https://github.com/yaniswang/HTMLHint/wiki/space-tab-mixed-disabled)

**定义**：禁止混用空格和`tab`两种缩进方式

**警告级别**：`warning`

正确写法：

``` html
 →   →<img src="tab.png" />
········<img src="space.png" />
```

错误写法

``` html
  →····<img src="tab_before_space.png" />
····   →<img src="space_before_tab.png" /> xxxxxxxxxx <html><head></head></html><html><head><title></title></head></html><html><title></title><head></head></html>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



- [id-class-ad-disabled](https://github.com/yaniswang/HTMLHint/wiki/id-class-ad-disabled)

**定义**：ID值和class值禁止使用`ad`关键字，

**警告级别**：`warning`

正确写法：

``` html
<div id="adcontainer"></div>
```

错误写法

``` html
<div id="ad-container"></div>
<div id="ad_container"></div> xxxxxxxxxx <html><head></head></html><html><head><title></title></head></html><html><title></title><head></head></html>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



- [href-abs-or-rel](https://github.com/yaniswang/HTMLHint/wiki/href-abs-or-rel)

**定义**：href属性可以使用相对路径和绝对路径

**警告级别**：`warning`

正确写法：

``` html
abs: <a href="http://www.alibaba.com/">test1</a> <a href="https://www.alipay.com/">test2</a>
rel: <a href="test.html">test1</a> <a href="../test.html">test2</a>
```

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



- [attr-unsafe-chars](https://github.com/yaniswang/HTMLHint/wiki/attr-unsafe-chars)

**定义**：属性值内禁止包含不安全字符

**regexp**: `/[\u0000-\u0009\u000b\u000c\u000e-\u001f\u007f-\u009f\u00ad\u0600-\u0604\u070f\u17b4\u17b5\u200c-\u200f\u2028-\u202f\u2060-\u206f\ufeff\ufff0-\uffff]/`

**警告级别**：`warning`

正确写法：

``` html
<li><a href="https://vimeo.com/album/1951235/video/56931059">Sud Web 2012</a></li>
```

错误写法

``` html
<li><a href="https://vimeo.com/album/1951235/video/56931059‎">Sud Web 2012</a></li>
```

**不安全字符出现在错误写法中的href属性的尾部

**配置选项**

`true`:激活该规则

`false`: 禁止使用该规则



