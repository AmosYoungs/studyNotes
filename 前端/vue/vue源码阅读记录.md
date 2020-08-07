# 开始
## 1.前言
**之前不知道如何下手学习源码，这个学习记录也是看别人学习vue源码博客为加深印象而写，同时也是本菜鸟探索学习源码的方法之路，
重要的是这个博客也提供了学习vue源码的路线。**
## 2.学习路线
有学习路线才不会一头雾水，跟着下面这个学习路线走吧
**1.变化侦测篇**
学习Vue如何实现数据的响应式系统，从而达到数据驱动视图。
**2.虚拟DOM篇**
学习什么是虚拟DOM，以及Vue中的 DOM-diff原理。
**3.模板编译篇**
学习Vue内部是怎么把template模板编译成虚拟DOM，从而渲染出真实DOM。
**4.实例方法篇**
学习VUE中所有实例方法（即所有以$开头的方法）的实现原理。
**5.全局API篇**
学习VUE中所有全局API的实现原理。
**6.生命周期篇**
学习Vue中组件的生命周期实现原理。
**7.指令篇**
学习Vue中所有指令的实现原理。
**8.过滤器篇**
学习Vue中所有过滤器的实现原理。
**9.内置组件篇**
学习Vue中内置组件的实现原理。


# 变化侦测篇
## 1.综述
**1.1 前言** `Vue`的最大特点之一是数据驱动视图，那么什么是数据驱动视图呢？先看一个公式：
**UI = render(state)**

上述公式中：状态`state` 是输入，页面`UI`是输出，状态输入变化了，那么页面输出也随之变化，这种特性称之为数据驱动视图。
`state`和`UI`都是用户定的，不变的是`render()`,`Vue`就扮演了`render()`这个角色，当`Vue`发现`state`变化之后，经过一系列处理后，就会把这些变化反应在`UI`上。那么`Vue`是如何发现`state`变化的呢?这就需要学习一下`Vue`的变化侦测机制。

**1.2 什么是变化侦测呢**
变化侦测就是追踪状态，又或者说是监听数据的变化。当侦测到变化后就去更新视图。
在前端三大框架中都有变化侦测，在Angular中是通过脏值检查流程来实现变化侦测；在React是通过对比虚拟DOM来实现变化侦测；在Vue中也有变化侦测实现机制。
# 2.Object的变化侦测

**2.1 前言**
通过前面的了解，数据驱动视图的关键在于知道数据什么时候发生了变化，js提供了`Obejct.defineProperty`方法可以帮助我们知道数据什么时候被读取了什么时候被修改了。

**2.2 Object监测**
先看一个使用`Object.defineProperty`的`get()`和`set()`对对象的读写进行拦截的例子

```
let obj = {}
let value = 'val'
Object.defineProperty(obj,'name',{
    enumerable:true,
    configurable:true,
    get(){
        console.log('name属性被读取了');
        return value
    },
    set(val){
        console.log('name属性被修改了:',val);
        value = val
    }
})
console.log(obj.name)
obj.name = 123
console.log(obj.name)
// 输出:
// name属性被读取了
// val
// name属性被修改了: 123
// name属性被读取了
// 123

```
以上，对obj对象实现了观测，可以获取obj的读写情况。
那么如果要让一个对象的所有属性都变得可观测，我们定义一个observer类通过递归的方式把一个对象的所有属性都转换成可观测对象

```
export class Observer{
    constructor(value){
        this.value = value
         // 给value新增一个__ob__属性，值为该value的Observer实例
        //  相当于为value打上标记，标识已经被转换为响应式了，避免重复操作
        def(value,'__ob__',this)
        if(Array.isArray(value)){
        
        }else{
            this.walk(value)
        }
    }
    walk(obj:Object){
        const keys = Object.keys(obj)
        for(let i = 0;i<keys.length;i++){
            defineReactive(obj,keys[i])
        }
    }
}
/**
 * @description: 使一个对象转换成一个可观测对象
 * @param {Object} obj 被转换的对象
 * @param {String} key 对象的key
 * @param {Any} val 对象某个key的值
 * @return: 
 */
function defineReactive(obj,key,val){
    // 如果只传了obj key 则val = obj[key]
    if(arguments.length==2){
        val = obj[key]
    }
    // 如果val还是Object则递归使用Observer类处理
    if(typeof val ==='object'){
        new Observer(val)
    }
    Object.defineProperty(obj,key,{
        enumerable:true,
        configurable:true,
        get(){
            console.log(`${key}属性被读取了`)
            return val
        },
        set(newVal){
            console.log(`${key}属性被修改了`)
            val = newVal
        }
    })
}
```
上面代码中定义了一个`observer`类，这个类将一个正常的object转换成一个可观测的`object`。
并个每一个被转换的对象`value`新增一个`__ob__`属性，值为该`value`的`observer`实例。即对该对象进行标记表示已经转为响应式对象了，避免重复操作。
接着判断对象的数据类型，只有`value`为`Object`类型时才会调用`walk`，`walk`中遍历这个对象所有可枚举属性,并将这个对象及其自身所有可枚举属性作为参数传给`defineReactive`,`defineReactive`对于传入的属性获取其值，如果值为对象，则递归调用