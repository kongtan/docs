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

### 小拓展

> 既然提到了with及new Function，那么就初步说明下他们的风险点

#### with 存在的数据泄漏

```javascript
const obj={a:1}
with(obj){
    b=2
}
console.log("obj.b:",obj.b) //obj.b: undefined
console.log("window.b:",window.b) //window.b: 2
```

可以发现obj对象并没有新增b属性，因为with在对obj对象进行属性查询时没有发现该属性，则会向上层作用域查询、如果最后还是没有查询到、则会在全局作用域新建b属性并赋值，故此window.b为2

#### new Function 内作用域为全局作用域

```javascript
const val = 1
const fnc = ()=>{
    const val = 2;
    new Function(`console.log('val:',val)`)();
}
fnc()
// val: 1
```

可以发现最后输出的val为全局的val，故此在使用new Function时需要注意作用域的影响

**有关`with`及`new Function`的使用存在一些风险点、可自行查阅文章学习，本系列文章在之后有时间也会补充**