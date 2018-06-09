# BEM 简介

## 什么是 BEM

BEM代表块（Block），元素（Element），修饰符（Modifier）。
命名约定的模式如下：

``` css
.block { }
.block__element { }
.block--modifier { }
```

### Block(块)

一个块是一个独立有意义的实体。块可以包含其他块。

- 仅使用 class 为一个块命名。
- 块名称可以由字母、数字和`-`组成。

``` html
<div class="block">...</div>
```

``` css
.block { color: #042; }
```

### Element(元素)

元素是块的一部分，并依赖所在的块，没有独立意义。

- 仅使用 class 为一个元素命名。
- 元素名称可以由字母、数字、`-`和`_`组成。
- 元素名称需要加`${块名}__`前缀。
``` html
<div class="block">
  ...
  <span class="block__element"></span>
</div>
```

``` css
/* bad */
.block .block__elem { color: #042; }

/* good */
.block__elem { color: #042; }
```

### Modifier(修饰符)

修饰符作为块/元素的一种属性，代表这个块或这个元素在外观或是行为上的改变。

- 修饰符的名称可以由拉丁字母、数字、`-`和`_`组成。
- 修饰符是添加到块/元素DOM节点的额外类名。只向其修改的块/元素添加修饰类，并保留原始类。
- 修饰符需要加`${块名|元素名}--`前缀。

``` html
<div class="block block--mod">...</div>
<div class="block block--size-big">...</div>
```

``` css
.block--hidden { }
.block--mod .block__elem { }
.block__elem--mod { }
```

## Example

``` html
<button class="button">Normal button</button>
<button class="button button--state-success">
  Success button
</button>
<button class="button button--state-danger">
  Danger button
</button>
```

``` css
.button {
  display: inline-block;
  border-radius: 3px;
  padding: 7px 12px;
  border: 1px solid #d5d5d5;
  background-image: linear-gradient(#eee, #eee);
  font: 700 13px/18px Helvetica, arial;
}
.button--state-success {
  color: #fff;
  background: #569e3d linear-gradient(#79d858, #569e3d) repeat-x;
  border-color: #4a993e;
}
.button--state-danger {
  color: #900;
}
```

``` html
<form class="form form--theme-xmas form--simple">
  <input class="form__input" type="text" />
  <input
    class="form__submit form__submit--disabled"
    type="submit"
  />
</form>
```

``` css
.form { }
.form--theme-xmas { }
.form--simple { }
.form__input { }
.form__submit { }
.form__submit--disabled { }
```