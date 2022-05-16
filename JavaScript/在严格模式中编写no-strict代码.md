## 在严格模式中编写no-strict代码

> 先前在做JS沙箱时其中一环便是需要使用到with，但是相信大家和我一样现在都是使用的`严格模式`，而严格模式是不允许使用with的，下面将会用`魔法`来破除这个限制

### new Function

**new Function 构造一个函数时他的`作用域是在顶部全局的`,属于`global作用域`、默认情况下是`no-strict`模式的**

```javascript
const sandbox={}
new Function('window',`
with(window){
    console.log(1)
    // todo
}`)(sandbox)
// 1
// 绕过strit检测、成功运行
```

可以看到通过使用`new Function`后成功绕过了严格模式检测、此处只是已with举例、也可使用arguments、callee等严格模式所不允许的功能

**`with`及`new Function`的使用存在一些风险点、可自行查阅文章学习，本系列文章在之后有时间也会补充**