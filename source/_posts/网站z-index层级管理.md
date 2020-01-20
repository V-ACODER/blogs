---
title: 网站z-index层级管理
date: 2019-03-03 14:44:34
tags: CSS
categories: 前端
---

理论上来说，网页中设置CSS的z-index，都没必要超过2。如果超过了，甚至出现999，9999或者20000这样的想占据最高层叠水平（stacking level）的数值，那肯定有问题，面壁反思吧。

我们知道，CSS世界的层叠规则不止z-index，所有元素都有层叠水平。比如普通元素之间，后面节点的元素会覆盖在前面元素上边。那不普通的元素呢？所有元素的层叠顺序如下图所示：

![stacking order](/images/zindex.jpg)

<!-- more -->

在层叠世界，有一个和BFC类似的概念，叫层叠上下文（stacking context），具备这个特性的元素，设置z-index的正负值才会生效，z-index: auto等同于z-index: 0，并且自成体系，每个层叠上下文和兄弟元素独立。最常见的层叠上下文包括：

1，  position值不为static

2，  html根元素

3，  flex布局元素

4，  opacity值不为1

5，  其他一些CSS3属性…

我们可以充分利用层叠上下文内部元素受制于外部元素层叠水平的特性，和相同特性元素后来居上的原则，使z-index的值不超过2。

更多内容请参考张鑫旭的《CSS世界》的第7章“CSS世界的层叠规则”。