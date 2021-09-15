---
title: css派生选择器
tags: 
  - CSS
categories: 
  - 前端
comment: true
date: 2021-06-25 15:01:05
updata: null
permalink: /pages/dd9287/
---

# 派生选择器学习总结

派生选择器：依据元素在其位置的上下文关系来定义样式。

派生选择器一共分为三种：后代选择器、子元素选择器、相邻兄弟选择器。

## 后代选择器

后代选择器能选择作为某元素后代的元素。

如果一个元素出现在文档层次结构中另一个元素的上层，则称前者是后者的父元素。

父子关系是祖先-后代关系的特例。这二者之间有一个区别：在树视图中，如果一个元素是另一个元素的直属上一层，即直接包含，它们就有父子关系。如果从一个元素到另一个元素的路径上要经过两层或以上层数，那它们则有祖先-后代关系，而不是父子关系（父子关系一定属于祖先-后代关系，父子关系是祖先-后代关系的子集）

定义后代选择器

```css
/* css */ 
h1 em {
    color: red
}
```

则在h1标签包含内所有em标签中的字符都变为红色。

## 子元素选择器

与后代选择器相比，子元素选择器只能选择作为某元素子元素的元素，即只针对父子关系中的子元素生效。

如果您不希望选择任意的后代元素，而是希望缩小范围，只选择某个元素的子元素，请使用子元素选择器。

定义子元素选择器

```css
/* css */ 
h1 > em {
    color: red
}
```

则在下面的HTML代码中，is是红色，而Child Selector不受影响

```html
<!-- html -->
<h1>
    This <em>is</em> <strong><em>Child Selector</em></strong>
</h1>
```

## 相邻兄弟选择器

相邻兄弟选择器可选择具有相同父元素且紧接在 + 左边元素后的元素。

实例：如果要增加紧接在 h1 元素后出现的p元素的字体大小，可以这样写：

```css
/* css */
h1 + p { font-size: 21px }
```

***注意*** :

请看下面的选择器：

```css
/* css */
li + li { font-weight: bold }
```

上面这个选择器只会把下面列表中的第二个和第三个列表项变成粗体。第一个列表项不受影响

```html
<!-- html -->
<div>
  <ul>
    <li>List item 1</li>
    <li>List item 2</li>
    <li>List item 3</li>
  </ul>
  <ol>
    <li>List item 1</li>
    <li>List item 2</li>
    <li>List item 3</li>
  </ol>
</div>
```

运行结果：

![image-20210625160415128](C:/Users/b1205/AppData/Roaming/Typora/typora-user-images/image-20210625160415128.png)

结合其他选择器：

```html
<!-- html -->
html > body table + ul { margin-top: 20px }
```

这个选择器解释为：选择紧接在 table 元素后出现的所有兄弟 ul 元素，该 table 元素包含在一个 body 元素中，body 元素本身是 html 元素的子元素。
