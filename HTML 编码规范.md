# HTML 编码规范

## 语法
- 缩进使用两个空格。
- 嵌套元素应当缩进一次（即两个空格）。
- 对于属性的定义，确保全部使用双引号。
- 不要在自闭合（self-closing）元素的尾部添加斜线。
- 不要省略可选的结束标签（closing tag）。

``` html
<!DOCTYPE html>
<html>
  <head>
    <title>Page title</title>
  </head>
  <body>
    <img src="images/company-logo.png" alt="Company">
    <h1 class="hello-world">Hello, world!</h1>
  </body>
</html>
```

## HTML5 doctype

为每个 HTML 页面的第一行添加标准模式（standard mode）的声明，这样能够确保在每个浏览器中拥有一致的展现。

``` html
<!DOCTYPE html>
<html>
  <head>
  </head>
</html>
```

## 语言属性

根据 HTML5 规范：
> 强烈建议为 html 根元素指定 lang 属性，从而为文档设置正确的语言。这将有助于语音合成工具确定其所应该采用的发音，有助于翻译工具确定其翻译时所应遵守的规则等等。
更多关于 `lang` 属性的知识可以从此[规范](http://w3c.github.io/html/semantics.html#the-html-element)中了解。

``` html
<html lang="en-us">
  <!-- ... -->
</html>
```

## 字符编码

通过声明字符编码，能够确保浏览器快速并容易的判断页面内容的渲染方式。通常采用 UTF-8 编码。

``` html
<head>
  <meta charset="UTF-8">
</head>
```

## 引入 CSS 和 JavaScript 文件
根据 HTML5 规范，在引入 CSS 和 JavaScript 文件时一般不需要指定 `type` 属性，因为 `text/css` 和 `text/javascript` 分别是它们的默认值。

``` html
<!-- 外部 CSS -->
<link rel="stylesheet" href="code-guide.css">

<!-- 内联 CSS -->
<style>
  /* ... */
</style>

<!-- JavaScript -->
<script src="code-guide.js"></script>
```

## 布尔（boolean）型属性
布尔型属性可以在声明时不赋值。HTML5 规范不需要。

``` html
<input type="text" disabled>
<input type="checkbox" value="1" checked>
<select>
  <option value="1" selected>1</option>
</select>
```

## 减少标签的数量
编写 HTML 代码时，尽量避免多余的父元素。很多时候，这需要迭代和重构来实现。请看下面的案例：

``` html
<!-- bad -->
<span class="avatar">
  <img src="...">
</span>

<!-- good -->
<img class="avatar" src="...">
```