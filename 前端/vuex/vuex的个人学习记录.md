[TOC]



## 一、vuex是一个专为vue.js应用程序开发的状态管理模式。

### 什么是状态管理

状态自管理包含以下几个部分：

- **state**，驱动应用的数据源
- **view**，以声明方式将**state**映射到视图
- **actions**，响应**view**上用户输入导致的状态变化

概念示意图：

<img src="../assets/state_flow.png" style="zoom: 33%;" />

以上是组件自己内部状态管理的示意，当遇到**多个组件共享状态**，单项数据流的简洁性容易遭到破坏：

- 多个视图依赖于同一状态
- 来自不同视图的行为需要变更同一状态

针对问题一：传参的方式对于多层嵌套的组件会非常繁琐，并且解决兄弟组件的状态传递能力。

针对问题二：我们通常会采用父子组件直接引用或者通过事件来变更和同步状态的多份拷贝。

以上方法都不佳，会导致代码混乱难以维护。



因而要把共享状态抽离出来，以一个**全局单例模式管理**，在这种模式下，组件树构成了一个巨大的"视图"，

不管组件在哪个位置，都可以获取状态和触发行为。这就是vuex背后的思想，为此设计了vue.js的状态管理库vuex，这个设计解决了多组件共享状态问题。

### vuex和单纯的全局对象的不同

1. Vuex的状态存储是响应式的，当vue组件从store中读取状态的时候，若store中的状态发生变化，相应的组件也会得到更新。
2. 不能直接修改store中的状态，必须通过显示的提交**（commit）mutation**来修改。方便追踪每一个状态的变化。

## 二、Vuex的使用

### 创建一个store

```
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment (state) {
      state.count++
    }
  }
})
```

为了更好的使用store，我们通常在根组件注册，这样子组件也可以访问到store。

```
new Vue({
  el: '#app',
  store: store,
})
```

### 修改store

```
store.commit('increment')

console.log(store.state.count) // -> 1
```

### 在vue组件中获取vuex状态

**1、通过计算属性获取**

```
computed: {
    count () {
      return this.$store.state.count
    }
  }
```

**2、通过mapState获取**

```
// 在单独构建的版本中辅助函数为 Vuex.mapState
import { mapState } from 'vuex'

export default {
  // ...
  computed: mapState({
    // 箭头函数可使代码更简练
    count: state => state.count,

    // 传字符串参数 'count' 等同于 `state => state.count`
    countAlias: 'count',

    // 为了能够使用 `this` 获取局部状态，必须使用常规函数
    countPlusLocalState (state) {
      return state.count + this.localCount
    }
  })
}
```

当映射的计算属性的名称与 state 的子节点名称相同时，我们也可以给 `mapState` 传一个字符串数组。

```
computed: mapState([
  // 映射 this.count 为 store.state.count
  'count'
])
```

**`mapState` 函数返回的是一个对象。我们如何将它与局部计算属性混合使用呢？通常，我们需要使用一个工具函数将多个对象合并为一个，以使我们可以将最终对象传给 `computed` 属性。但是自从有了[对象展开运算符 ](https://github.com/tc39/proposal-object-rest-spread)[ ](https://github.com/tc39/proposal-object-rest-spread)，我们可以极大地简化写法：**

```
computed: {
  localComputed () { /* ... */ },
  // 使用对象展开运算符将此对象混入到外部对象中
  ...mapState({
    // ...
  })
}
```

