## Object.keys与for...in的区别
> Object.keys()返回对象自身的可枚举属性组成的数组，
与for...in 的区别在于for...in 会遍历原型链上的可枚举属性

```
 let obj1 = {
     a:'test'
 }
 let obj2 = Object.create(obj1)
 obj2.b = 'b'

 console.log(Object.keys(obj2))
 // ['b']
 for(let key in obj2){
     console.log(key)
 }
// b 
// a

```