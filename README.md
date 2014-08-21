CSS-Guidelines-Chinese
原文来自 http://cssguidelin.es/
版权所有 Harry Roberts
======================

CSS Guidelines 中文版

####简介

虽然易学好用，但 CSS 不是一门美妙的语言。无论在何种情况下很快它就会出差错。虽然我们无法改变 CSS 如何运作，但却可以改变自己的工作方式来适应它。

大型持久的项目通常有几十个不同的开发者，每个人能力和专长都不同，所以所有人用统一的方式协调工作便很重要

* 使样式表可维护。
* 使代码透明、正常和可读。
* 使样式表可扩展

有各种各方的方式可以满足这些目标，CSS Guideline 列出了一些建议和方法来帮助我们实现它们。

####风格指南的重要性

风格指南对于以下这种团队来说是一个宝贵的工具：

* 项目已经开工了一段时间
* 有技能多样化的开发者
* 一个组内有许多不同的开发者
* 经常有新人加入
* 有一些经常需要修改的代码

虽然风格指南更适用于对于大项目和持续长期运转的项目，在这些项目中，每一位开发者都应该尽力的标准化自己的代码。

当我们遵循一份好的风格指南的时候

* 为这个代码库设定标准
* 统一代码库的风格
* 给开发者一种熟悉感
* 提高生产力
 
风格指南必须透过各种方式透彻的被理解，并且应用到每一个项目中，无论何时何地。任何违反指南的都需要纠正。

####免责声明

CSS 指南是只是多种风格指南中的一个，其中和方法、技巧和小贴士，我会真诚的推荐给我的客户和团队。当然是你个人的洗好和面临的情况可能不同，请自取所需。

虽然这些指南参杂个人的看法，但是它们在多年里在大小项目中被反复的试错和精炼过。

================

####语法和格式
最简单的风格指南含有一系列的语法和格式。借助标准来写 CSS 意味着对团队所有成员来说，代码看上去和感觉上会很熟悉。

而且，看上去干净的代码感觉也干净，这意味着更好的工作环境，并且也让团队的成员们来一起维护好这个环境。丑陋的代码会带来不好的习惯。

在非常高的层级上，我们希望：At a very high-level, we want

* 4 空格缩进，不用 tab。
* 每行 80 字符宽
* 多行 CSS
* 合理使用空格

但是，这些都不是重要的，重要的是持之以恒。

####多文件Multiple Files

随着预处理器的流行，开发者越来越经常把 CSS 分割成多个文件。

即使不使用预处理器，把代码分割成独立的区块后再重组也是个好注意。

无论什么原因，假如你不用多个文件，下一章的内容需要做些许调整来满足你的习惯。

####目录Table of Contents

虽然打理目录需要花费较多的精力，但是它带来的好处大大超过复旦。细心的开发者不断更新文档，这是值得的。一份最新的目录能够告诉团队，这个 CSS 项目里有什么，做什么，次序如何。

一份简单的目录能够按顺序指出不同的栏目做什么，并给出一份总结，例如

```CSS
/**
 * CONTENTS
 *
 * SETTINGS
 * Global...............Globally-available variables and config.
 *
 * TOOLS
 * Mixins...............Useful mixins.
 *
 * GENERIC
 * Normalize.css........A level playing field.
 * Box-sizing...........Better default `box-sizing`.
 *
 * BASE
 * Headings.............H1–H6 styles.
 *
 * OBJECTS
 * Wrappers.............Wrapping and constraining elements.
 *
 * COMPONENTS
 * Page-head............The main page header.
 * Page-foot............The main page footer.
 * Buttons..............Button elements.
 *
 * TRUMPS
 * Text.................Text helpers.
 */
```
每一个项目对应一个章节

大的项目，目录的内容自然就大，但是仍然可以给开发者提供一个非常清晰的视觉：这是做啥的？以及为什么要用他。

####80字符宽

尽可能的限制 CSS 的行宽在 80 字符之内，原因是：

* 方便并列展示多个文件。
* 在 Github 等网站或终端中查看 CSS。
* 评论在这种宽度下看起来较合适

```CSS
/**
 * I am a long-form comment. I describe, in detail, the CSS that follows. I am
 * such a long comment that I easily break the 80 character limit, so I am
 * broken across several lines.
 */
```
像 URL，渐变语法等必须要保持在一行中，我们不必担心这种情况。

####标题

CSS 项目中的每一个主要栏目都需要附上标题：
```CSS
/*------------------------------------*\
    #SECTION-TITLE
\*------------------------------------*/

.selector {}
```
栏目的标题以#号起头，以便我们更好的搜索（例如用 grep 命令）：因为直接搜索标题会出来许多结果，而用了#号则只会返回你搜索的那个标题。

在标题和下一行代码间加入回车（无论那行代码是评论，Sass 或者 CSS）

如果这个项目中，每个栏目都有自己的文件，那么标题应该在每个文件的顶部。如果一个文件内有几个栏目，每个标题前应插入 5 个回车。额外空格和标题让寻找变得更加简单。

```CSS
/*------------------------------------*\
    #A-SECTION
\*------------------------------------*/

.selector {}





/*------------------------------------*\
    #ANOTHER-SECTION
\*------------------------------------*/

/**
 * Comment
 */

.another-selector {}
```

####规则的解析
开始动手前，先让我们熟悉相关名词的含义
```CSS
[selector] {
    [property]: [value];
    [<--declaration--->]
}
```

例如：
```
.foo, .foo--bar,
.baz {
    display: block;
    background-color: green;
    color: red;
}
```

从以上的例子我们可以看到：

* 相关的 selector 在同行，不相关的 selector 换行
* 大括号（{）前有一个空格
* 属性和值在同一行
* 分割属性和值的冒号（:）后有一个空格
* 每个声明占一行
* 开大括号和最后一个 selector 在同一行
* 第一个声明在开大括号的后一行
* 闭大括号自起一行。
* 每一个声明缩进 4 个空格
* 最后一个声明包含单冒号
这个格式几乎已经成为标准（除了空格数不同，有些开发者喜欢用两个空格）

因此，下面的是错误的
```
.foo, .foo--bar, .baz
{
	display:block;
	background-color:green;
	color:red }
```
错误的问题有：

* 使用 tab 而不是空格
* 不相同的 selector 在同一行上
* 开大括号自起一行
* 闭大括号没有自起一行
* 最后一个声明尾部的半冒号缺失。
* 冒号后无空格。
