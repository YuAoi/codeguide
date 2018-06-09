# git commit message

commit message 应该清晰明了，说明本次提交的目的。
目前有多种 commit message 的写法规范，我们推荐使用 Angular [规范](https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/edit#heading=h.greljkmo14y0)。

## 好的 commit message 的作用

1. 提供更多的历史信息，方便快速浏览
1. 可以分别查看某种类型的提交
1. 可以直接从 commit message 中生成 change log

## commit message 应该怎么写

标准格式如下
``` bash
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>

```

- commit message 包含三个部分：Header，Body 和 Footer。
- Header 是必须的，Body 和 Footer 可选。
- 每一行不能超过100个字符（或72个字符）。

### Header

Header 是必须的，并只允许一行。Header 包含三个字段：type（必须），scope（可选）和 subject（必须）。

1. type
   - feat (feature)
   - fix (bug fix)
   - docs (documentation)
   - style (formatting, missing semi colons, …)
   - refactor
   - test (when adding missing tests)
   - chore (maintain)
1. scope
   - scope 说明本次 commit 影响的范围
   - 如果没有合适的范围，可以写 *
1. subject
   - subject 是对本次 commit 的短描述
     - 以动词开头，使用第一人称现在时，比如 change，而不是 changed 或 changes
     - 第一个字母小写
     - 结尾不加句号（.）

### Body

Body 是对本次 commit 的详细描述，可以分成多行。

- 跟 subject 一样，以动词开头，使用第一人称现在时，比如 change，而不是 changed 或 changes
- 应说明代码变动的动机，以及与以前行为的对比。

### Footer

Footer 部分用于两种情况
1. 不兼容的变动
  - 如果更改的代码和上一个版本不兼容，则 Footer 部分以 BREAKING CHANGE 开头，后面是对变动的描述、以及变动的理由和迁移方法。

  ``` bash
    BREAKING CHANGE: isolate scope bindings definition has changed and
      the inject option for the directive controller injection was removed.
      
      To migrate the code follow the example below:
      
      Before:
      
      scope: {
        myAttr: 'attribute',
        myBind: 'bind',
        myExpression: 'expression',
        myEval: 'evaluate',
        myAccessor: 'accessor'
      }
      
      After:
      
      scope: {
        myAttr: '@',
        myBind: '@',
        myExpression: '&',
        // myEval - usually not useful, but in cases where the expression is assignable, you can use '='
        myAccessor: '=' // in directive's template change myAccessor() to myAccessor
      }
      
      The removed `inject` wasn't generaly useful for directives so there should be no code using it.
  ```
1. 关闭 issue（jira）

  - 当前 commit 关闭了某个 issue 或者 jira

  ```
    Closes #234
  ```
  - 也可以一次关闭多个
  ```
    Closes #234, #456
  ```


## Revert

还有一种特殊情况，如果当前 commit 用于撤销以前的 commit，则必须以revert:开头，后面跟着被撤销 Commit 的 Header。

```
revert:feat(pencil): add 'graphiteWidth' option

This reverts commit 667ecc1654a317a13331b17617d973392f415f02.

```