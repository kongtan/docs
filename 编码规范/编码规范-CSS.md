---
title: 无线Hybrid编码-CSS
date: 2017-01-11 14:02:40
tags: 规范
categories: Native转H5系列培训
---
>## 引言
>编码规范是相当于是一个团队中编写代码的一种协议，大家应该有意识的去遵守,类似于成员之间的一种暗号，能够使代码风格保持一致，增加代码可读性和可维护性，减少维护成本。

## CSS
### 一、命名

###### 1)名字较长或是词组是使用中横线"-"来命名,如：header-pic

###### 2)不建议使用"_"下划线来命名,主要是浏览器兼容问题如_header在IE6下是无效的

```
/*错误的写法*/
.headerpic {
    color: #666;
}
.header_pic {
    color: #666;
}

/*正确的写法*/
.header-pic {
    opacity: .8;
}
```

###### 3)最重要的一点是一定要让人一眼就知道你表达的是什么意思

### 二：书写顺序
>###### 书写顺序按下列从上而下顺序书写
1. `位置属性`(position, top, right, z-index, display, float等)
1. `大小`(width, height, padding, margin)
1. `文字系列`(font, line-height, letter-spacing, color, text-align等)
1. `背景`(background, border等)
1. `其他`(animation, transition等)

```
/*错误的写法*/
.example {
    color: red;
    z-index: -1;
    background-color: #9e0;
    display: inline-block;
    font-size: 16px
}
/*正确的写法*/
.example {
    z-index: -1;
    display: inline-block;
    font-size: 16px;
    color: red;
    background-color: #9e0;
}
```


### 三、缩写
>###### 一些属性是可以缩写的，即可以减少代码量也可以增加可读性，如padding,margin,font等

```
/*错误的写法*/
.list-box {
    border-top-style: none;
    font-family: serif;
    font-size: 100%;
    line-height: 1.6;
    padding-bottom: 20px;
    padding-left: 10px;
    padding-right: 10px;
    padding-top: 0;
}
/*正确的写法*/
.list-box {
    border-top: none;
    font: 100%/1.6 serif;
    padding: 0 10px 20px;
}
```


>###### 小数点前的0可以去除

```
/*错误的写法*/
.header {
    opacity: 0.8;
}
/*正确的写法*/
.header {
    opacity: .8;
}
```


>###### 类名的简写需要让别人一眼就能看懂

```
/*错误的写法*/
.navigation {
    color: #fff;
}
.atr {
    color: #e6e6e6;
}
/*正确的写法*/
.nav {
    color: #fff;
}
.author {
    color: #e6e6e6;
}
```


>###### 16进制颜色代码缩写

```
/*错误的写法*/
#nav {
    color: #ffffff;
}
/*正确的写法*/
#nav {
    color: #fff;
}
```


### 四、注意点
- [x] 一律小写，尽量用英文

- [x] 尽量不缩写，除非一看就明白

- [x] 使用Media query时将其统一写在一起并放置在头部，使其可以被别人一开始就发现，切记不要放在底部

- [x] 使用缩进时使用四个空格，不要使用tab字符，因为不同编译器对tab的定义不一致

- [x] 在编写css时统一在外部套一层自己页面特有的类名，以防影响同项目中其他页面的层叠样式

- [x] 一个属性占用一行，类名与'`{}`'间需要一个空格，'`:`'与属性值之间需要一个空格

```
/*错误的写法*/
.header{ 
    font-size:16px; 
}
/*正确的写法*/
.header {
    font-size: 16px;
}
```

- [x] 一个类名中在写多个样式时不要都写在一行，一个样式占用一行

```
/*错误的写法*/
.header { font-size: 16px;  color: #666; }
/*正确的写法*/
.header {
    font-size: 16px;
    color: #666;
}
```

- [x] 使用sass和less或者自己直接写的时候层级尽量不要超过三层,如：

```
/*错误的写法*/
.header .navigation .list p{
    color:blue;
}
/*正确的写法*/
.header .list p{
    color:blue;
}
```

- [x] 编写css时尽量将一个元素的样式在一个类名中写完，不要分散在多个类名中去渲染：

```
/*错误的写法*/
.class-one {
    font-size: 12px;
}
.class-two {
    color: #666;
}
/*正确的写法*/
.class {
    font-size: 12px;
    color: #666;
}
```
