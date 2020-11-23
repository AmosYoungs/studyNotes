# vue组件通信

## 父子组件通信：

- props: 子组件通过props接收父组件传递来的参数。

- $emit:子组件通过$emit()发送一个事件，父组件监听该事件并触发回调。

- $parent:子组件可以通过$parent 直接访问父组件实例。

- $children:获取父组件下的直接子组件实例数组。

- ref:父组件可以通过$ref访问子组件实例。
- $attrs:子组件可以访问到父作用域绑定到当前组件实例的属性绑定（不包含class,style,和props中声明过的）。
- $listeners:子组件可以访问到父作用域绑定到当前组件实例的事件监听器（不包含.native修饰过的）。

## 兄弟组件通信

- eventBus 通过在根实例上创建一个Vue实例``` Vue.prototype.eventBus = new Vue()```，可以在子组件任何地方使用```this.eventBus.$emit();this.eventBus.$on();```来实现通信。
- vuex :前者适用于小型项目，对于大型项目而言使用vuex更好。
- $root：可以访问到根实例对象，知道组件层级关系从而实现对兄弟组件通信。
- $parent：可以访问到最近父组件实例对象，通过父组件实例实现与兄弟组件的通信。

## 跨层级通信

- eventBus
- vuex
- provide/inject:通过provide在祖先组件中注入一个依赖，那么不管哪个位置的子组件都可以通过inject接收到