## Input 输入限制数字问题

输入框设置只能输入数字，一般浏览器都正常识别number，不过能输入e，因为 e在数学上代表2.71828

1、有的人这么解决：

```js
<input type='number' onkeypress='return( /[\d]/.test(String.fromCharCode(event.keyCode) ) )' />
```

2、由于火狐里面没有 input type ="number" 这个设置，所以可以随机输入英文，

看了其他的文章用了第一个方法，火狐居然出现无法输入，并且使用中文状态可以输入任意字符，但是无法删除的问题.....
--------------------- 

```js
使用 onkeypress='return( /[\d]/.test(String.fromCharCode(event.keyCode||event.which) ) )'
```

可以兼容火狐，但是同时所有其他浏览器也可以通过使用中文状态来输入任意字符了，跟没有这个操作一样。



最后使用普通input 然后用正则去校验数据。

```js
      let reg = /^[0-9]*$/; // 非负整数
	  let reg = /^-?[0-9]*$/; // 整数
      let reg1 = /^\d+(\.\d+)?$/; // 非负数
```



直接使用表达式的方式赋值会出现没有响应的问题

在vue中使用elment-ui，直接给对象或者数组赋值可能无法引起页面或者组件的重新渲染，使用this.$set方法赋值