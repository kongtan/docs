---
title: 无线Hybrid编码-HTML
date: 2017-01-11 14:01:10
tags: 规范
categories: Native转H5系列培训
---
># 引言
>编码规范是相当于是一个团队中编写代码的一种协议，大家应该有意识的去遵守,类似于成员之间的一种暗号，能够使代码风格保持一致，增加代码可读性和可维护性，减少维护成本。

# HTML

## 一、通用
>### DOCTYPE
1)[`强制`]使用 HTML5 的 doctype 来启用标准模式，建议使用大写的 DOCTYPE。
2)[`建议`]在 html 标签上设置正确的 lang 属性。
有助于提高页面的可访问性，如：让语音合成工具确定其所应该采用的发音，令翻译工具确定其翻译语言等。

```html
'示例'：
简体中文:
<html lang="zh-cmn-Hans">
繁体中文:
<html lang="zh-cmn-Hant">
```

>### 编码
1)[`强制`] 页面必须使用精简形式，明确指定字符编码。指定字符编码的 meta 必须是 head的第一个直接子元素。
2)[`建议`] HTML 文件使用无 BOM 的 UTF-8 编码。

```
'解释'：UTF-8 编码具有更广泛的适应性。BOM在使用程序或工具处理文件时可能造成不必要的干扰。
```

>### CSS和JavaScript引入
1)[`强制`] 引入 CSS 时必须指明 rel="stylesheet"。

```
'示例'：<link rel="stylesheet" href="page.css">
```

2)[`建议`] 引入 CSS 和 JavaScript 时无须指明 type 属性。

```
text/css 和 text/javascript 是 type 的默认值。
```

3)[`建议`] 在 head 中引入页面需要的所有 CSS 资源。

```
在页面渲染的过程中，新的CSS可能导致元素的样式重新计算和绘制，页面闪烁。
```

4)[`建议`] JavaScript 应当放在页面末尾，或采用异步加载。

```
将 script 放在页面中间将阻断页面的渲染。出于性能方面的考虑，如非必要，请遵守此条建议。
```

>### head

1)[`强制`] 页面必须包含 title 标签声明标题。
2)[`强制`] title 必须作为 head 的直接子元素，并紧随 charset 声明之后。
3)[`建议`] 若页面欲对移动设备友好，需指定页面的 viewport。

>## 二、图片

[`强制`] 禁止 img 的 src 取值为空。延迟加载的图片也要增加默认的 src。

- [x] src 取值为空，会导致部分浏览器重新加载一次当前页面

[`建议`] 有下载需求的图片采用 img 标签实现，无下载需求的图片采用 CSS 背景图实现。

- [x] 产品 logo、用户头像、用户产生的图片等有潜在下载需求的图片，以 img 形式实现，能方便用户下载。
- [x] 无下载需求的图片，比如：icon、背景、代码使用的图片等，尽可能采用 css 背景图实现。

`项目中使用图片规范如下：`
- [x] 图片使用遵守原图与编写尺寸2:1的原则使用

- [x] 一般图片采用格式优先级为webp>png>jpg

- [x] 大图选择jpg>png

## 三、标签

[`强制`] 标签名必须使用小写字母。

[`强制`] 对于无需自闭合的标签，不允许自闭合。

==常见无需自闭合标签有input、br、img、hr等。==

```html
<!-- good -->
<input type="text" name="title">

<!-- bad -->
<input type="text" name="title" />
```

[`强制`] 对 HTML5 中规定允许省略的闭合标签，不允许省略闭合标签。
对代码体积要求非常严苛的场景，可以例外。比如：第三方页面使用的投放系统。

```html
<!-- good -->
<ul>
    <li>first</li>
    <li>second</li>
</ul>

<!-- bad -->
<ul>
    <li>first
    <li>second
</ul>
```

[`强制`] 属性名必须使用小写字母。

```html
<!-- good -->
<table cellspacing="0">...</table>

<!-- bad -->
<table cellSpacing="0">...</table>
```

[`强制`] 属性值必须用双引号包围。

[`建议`] 标签的使用应尽量简洁，减少不必要的标签。

```html
<!-- good -->
<img class="avatar" src="image.png">

<!-- bad -->
<span class="avatar">
    <img src="image.png">
</span>
```

[`建议`] 布尔类型的属性，建议不添加属性值。

```html
<input type="text" disabled>
<input type="checkbox" value="1" checked>
```

[`建议`] 为每个文本外层加上标签。

```html
<!--正确的写法-->
<div>
    <p>test</p>
    test
</div>
<!--正确的写法-->
<div>
    <p>test</p>
    <p>test</p>
</div>
```

## 四、代码风格
>### 缩进与换行
- [x] 使用缩进时使用四个空格，不要使用tab字符，因为不同编译器对tab的定义不一致
- [x] 每行不得超过 120 个字符。

==过长的代码不容易阅读与维护。但是考虑到 HTML 的特殊性，不做硬性要求。==

>### 命名
[`强制`] class 必须单词全字母小写，单词间以 - 分隔。
[`强制`] class 必须代表相应模块或部件的内容或功能，不得以样式信息进行命名。

```html
<!-- good -->
<div class="sidebar"></div>

<!-- bad -->
<div class="left"></div>
```

[`强制`] 元素 id 必须保证页面唯一。
[`建议`] id 建议单词全字母小写，单词间以 - 分隔。同项目必须保持风格一致。
[`建议`] id、class 命名，在避免冲突并描述清楚的前提下尽可能短。
[`强制`] 禁止为了 hook 脚本，创建无样式信息的 class。
==换句话说就是不允许 class 只用于让 JavaScript 选择某些元素，class 应该具有明确的语义和样式。否则容易导致 css class 泛滥。==