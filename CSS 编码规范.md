# CSS 编码规范

## 缩进
缩进使用两个空格。
``` css
.element {
  display: flex;
  justify-content: space-around;
}
```

## 分号
每个属性声明末尾都要加分号。
``` css
.element {
  width: 200px;
  height: 200px;
}
```

## 空格
以下几种情况需要空格：
- 属性值之前。
- 选择器前后。
- 选择器与声明块之间。
- !important 之前。
- 属性值的逗号（','）之后。
- 注释'/*'之后和'*/'之前。
以下几种情况不需要空格：
- 不要在 rgb()、rgba()、hsl()、hsla() 或 rect() 值的内部的逗号后面插入空格。

``` css
/* bad */
.element {
  display:flex;
}
/* good */
.element {
  display: flex;
}

/* bad */
.panel>.panel__header{
  padding: 5px 10px;
}
/* good */
.panel > .panel__header {
  padding: 5px 10px;
}

/* bad */
.element{
  display: flex;
}
/* good */
.element {
  display: flex;
}

/* bad */
.element {
  display: none!ipmortant;
}
/* good */
.element {
  display: none !important;
}
/* bad */
.element {
  font-family: arial,helvetica,sans-serif;
  background-color: rgba(0, 0, 0, .2);
}
/* good */
.element {
  font-family: arial, helvetica, sans-serif;
  background-color: rgba(0,0,0,.2);
}
```

## 空行
- 文件最后保留一个空行。

## 换行
以下几种情况需要换行
- '{'之后和'}'之前。
- 每个声明独占一行。
- 多个选择器之间需要换行。

``` css
/* bad */
.element { background-color: #f90; color: #ccc; }

/* good */
.element {
  background-color: #f90;
  color: #ccc;
}

/* bad */
.element, .selector {
  ...
}
/* good */
.element,
.selector {
  ...
}
```

## 注释
- 注释统一用'/* */'。
- 缩进与下一行代码保持一致。
- 可位于一个代码行的末尾，与代码间隔一个空格。

``` css
/* element style */
.element {
  ...
}
/*
 * element style
 * ...
 */
.element {
  /* 200px */
  width: 200px;
  height: 200px; /* 200px */
}
```

## 引号
- 统一使用双引号。
- URL 的内容需要用引号。
- 属性选择器中的属性值需要引号。

``` css
.element:after {
  content: "";
  background-image: url("logo.png");
}
.element[data-type="model"] {
  ...
}
```

## 命名
- 类名参考 BEM 命名规则。
- id 采用小写字母，多个字母用`-`连接

``` css
.block {
  ...
}
.block__element {
  ...
}
.block--modifier {
  ...
}

#logo {
  ...
}
#link-ofo {
  ...
}
```

## 颜色
- 使用16进制小些字母。
- 可用简写时用简写。

``` css
/* bad */
.element {
  color: #F90;
  background-color: #ffddcc;
}
/* good */
.element {
  color: #f90;
  background-color: #fdc;
}
```

## 媒体查询
尽量将媒体查询的规则靠近与他们相关的规则，不要将他们一起放到一个独立的样式文件中，或者丢在文档的最底部。

``` css
.element {
  ...
}
@media (min-width: 480px) {
  .element {
    ...
  }
}
```