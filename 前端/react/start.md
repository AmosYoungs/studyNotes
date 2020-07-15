## 通过props传递数据

在react中父组件向子组件传递数据通过props来传递。

## 构造函数

**1.react组件的私有数据应该由this.state来保存，并通过组件的构造函数来初始化this.state。**

**2.在javascript class 中，每次定义其子类的构造函数时，都需要调用super方法。在所有含有构造函数的React组件中，构造函数必须以super(props)开头**

**3.当需要同时获取多个子组件数据时，或者两个子组件需要互相通讯的情况时，需要把子组件的state数据提升到共同的父组件中保存。父组件可以通过props将状态数据传递到子组件当中。**

## 函数组件

如果一个组件只包含一个render方法，不包含state。那么就可以不用定义继承于React.Component的类，可以定义一个函数，这个函数接收props作为参数，然后返回需要渲染的元素。

## 数据提升

1.父组件向子组件通过props传递数据，如果一个数据在多个兄弟组件中使用，则这个数据要提升到最近的父级组件

## 子组件触发父组件事件

```
function Children(props){
	return (
		<div onClick = {props.onClick}></div>
	)
}
class Father extends React.Component{
	function handClick(){
		//触发父组件方法
	}
	return (
	 <Children onClick = {()=>{this.handClick}}></Children>
	)
}
```

