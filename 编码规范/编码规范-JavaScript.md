---
title: 无线Hybrid编码-JavaScript
date: 2017-01-11 14:03:46
tags: 规范
categories: Native转H5系列培训
---
>## 引言
>编码规范是相当于是一个团队中编写代码的一种协议，大家应该有意识的去遵守,类似于成员之间的一种暗号，能够使代码风格保持一致，增加代码可读性和可维护性，减少维护成本。

## JavaScript

### 一、命名
>###### 变量命名
1)采用匈牙利法命名：
开头字母用变量类型的缩写，其余部分用变量的英文或英文的缩写，要求单词第一个字母大写。
- [x]  s：表示字符串。例如：sName，sHtml；
- [x]  n：表示数字。例如：nPage，nTotal；
- [x]  b：表示伯尔。例如：bChecked，bHasLogin；
- [x]  a：表示数组。例如：aList，aGroup；
- [x]  r：表示正则表达式。例如：rDomain，rEmail；
- [x]  f：表示函数。例如：fGetHtml，fInit；
- [x]  o：表示以上未涉及到的其他对象，例如：oButton，oDate；
- [x]  g：表示全局变量，例如：gUserName，gLoginTime；

2)建议在块级作用域内如方法的私有变量的命名前面加上'`_`'，这样能够一目了然的明确该变量的作用域。

>###### 函数的命名
- [x] 统一使用动词或者`动词+名词形式` ---- fnInit()
- [x] 对象方法命名使用`fn+对象类名+动词+名词形式`   fnAnimateDoRun() 
- [x] 某事件响应函数命名方式为`fn+触发事件对象名+事件名或者模块名`  fnDivClick()

##### 常用的动词列表如下：

### 二、注释
>###### 注释要尽量简单，清晰明了。着重注释的意思，对不太直观的部分进行注解

>###### 此外，JavaScript 的注释有两种"//" 和"/* .... */"，

```
"//"用作代码行注释;
console.log('Hello World!'); //在控制台输出Hello World

"/* .... */"形式用作对整个代码段的注销，或较正式的声明中，如函数参数、功能、文件功能等的描述中
/*输出三个Hello World!*/
console.log('Hello World!');
console.log('Hello World!');
console.log('Hello World!');
```

>###### 对方法的注释如下

```
/**
 * 测试方法
 * @param name 姓名
 */
function test(name){
    console.log(name);
}
```


==`复制粘贴应注意注释是否与代码对应。`==

### 三、变量与函数的声明
变量和函数都需要`在使用之前申明`，即可以使结构更加清晰也符合es6的写法
内部函数应在 var 声明内部变量的语句之后声明，可以清晰地表明内部变量和内部函数的作用域。

 此外，函数名紧接左括号'`(`'之间，而右括号'`)`'和后面的'`{`'之间要有个空格，以清楚地显示函数名以其参数部分，和函数体的开始。若函数为匿名 / 无名函数，则 function 关键字和左括号'`(`'之间要留空格，否则可能误认为该函数的函数名为 function。
 
 >###### 当声明多个变量的写法如下

```
/*错误的写法*/
var sReqUrl = 'https://www.ly.com';
var nCount = 5;
var bIsTc = true;
/*推荐的写法----good----*/
var sReqUrl = 'https://www.ly.com',
    sCount = 5,
    bIsTc = true;
/*推荐的写法----better----*/
var oGlobalData = {
    sReqUrl: 'https://www.ly.com',
    nCount: 5,
    bIsTc: true
}
/*推荐的写法----best----*/
function index() {
    this.sReqUrl= 'https://www.ly.com';
    this.nCount= 5;
    this.bIsTc=true;
}
var Index=new index();
```


### 四、注意点
>###### 语句结束后一定要写分号';'

>###### 使用缩进时使用四个空格，不要使用tab字符，因为不同编译器对tab的定义不一致

>###### return如果用表达式的执行作为返回值，请把表达式和 return 放在同一行中，以免换行符被误解析为语句的结束而引起返回错误。return 关键字后若没有返回表达式，则返回 undefined。构造器的默认返回值为 this。

>###### 对于自执行函数，我们采用最前最后加括号的写法，如：(function(){alert(1);}()); 
==这样写的好处是，能提醒阅读代码的人，这段代码是一个整体。 
例如，在有语法高亮匹配功能的编辑器里，光标在第一个左括号后时，最后一个右括号也会高亮，看代码的人一眼就可以看到这个整体。== 

```
尽量不要写
(function(){alert(1);})();
!function(){alert(1);}();
void function(){alert(1);}();
等写法
```

>###### 单行代码超过80个字符时注意换行

>###### 单个方法超过100行时注意拆解成多个方法调用

>###### if-else执行简单方法的时可以缩写成

```
if(true) console.log(1);
else console.log(2);
不过类似的表达式建议写成三元表达式：
true?console.log(1):console.log(2);
```

>###### 多个if-else时应编写可维护代码

```
var a = 'one'
/*错误的写法*/
if (a == 'one') {
    console.log(1);
}
else if (a == 'two') {
    console.log(2);
}
else {

}
/*正确的写法*/
var fnc={
    one:function(){
        console.log(1);
    },
    two:function(){
        console.log(2);
    }
}
fnc[a]&&fnc[a]();
```

>###### 复制数组


```
var aArray=[1,2,3],aArrayCopy=[];
/*错误的写法*/
for (var i=0;i<aArray.length;i++){
    aArrayCopy.push(aArray[i]);
}
/*正确的写法*/
aArrayCopy=aArray.slice();
```

>###### 遍历数组拼接字符串

```
var aList=[1,2,3];
/*错误的写法*/
var sListDom='<ul>';
for(var i=0 ,length=aList.length;i<length;i++){
    sListDom+='<li>'+aList[i]+'</li>';

}
sListDom+='</Ul>'
/*正确的写法*/
sListDom='<ul><li>'+aList.join('</li><li>')+'</li></ul>'
```


>###### 用js改变元素css时应注意以下几点，防止CSS多次重排或重绘
==多次改变样式的代码合并成一次操作==
```
/*错误的写法*/
$('.element').css('font-size','12px');
$('.element').css('color','#666');
/*正确的写法*/
$('.element').css({'font-size':'12px','color':'#666'});
```



>###### 尽量不使用或者不用eval()
**主要有几点**:

- [x] 性能比较慢;   
- [x] 不易调试;   
- [x] 使用不当会引起xss攻击