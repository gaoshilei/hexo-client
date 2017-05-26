---
title: Hexo-编辑：在Next主题中插入表格的正确方法
date: 2017-05-20 14:36:50
tags:
- 教程
- Hexo
categories:
- 教程
- Hexo
---

每次按照markdown语法规范插入表格的时候都容易不起作用，应该是Next主题本身的解析有问题吧，插入表格有一定的技巧，有几个注意事项，将在本文中说明。

下面先把正确的示例代码贴出：

```
（必须是空行或者标题（就是带#的标题））
|Tables|Are | Cool |
|:-:|:-:|:-:|
| col 3 is | right-aligned | 1600|
|col2is|centered|12 |
| zebra stripes | are neat | $1 |
```
有以下几个注意事项：
* **第一行必须有一行是空行或者标题！！！**
* 第二行每个项目的前后空格可要可不要
* 第三行的冒号是用来指明左对齐还是右对齐的，示例中的是居中对齐。如果想要左对齐，冒号就放在左边；右对齐亦然。
* 推荐使用VS Code来编辑markdown表格，如果使用Typora，由于其具有自动预览的功能，导致编辑起来会很麻烦。

<!--more-->效果如下：

|    Tables     |      Are      | Cool |
| :-----------: | :-----------: | :--: |
|   col 3 is    | right-aligned | 1600 |
|    col2is     |   centered    |  12  |
| zebra stripes |   are neat    |  $1  |