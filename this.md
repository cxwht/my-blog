# 指向法则： **谁调用了函数，谁就是this**

- 全局下调用的函数: 函数的this指向 `window / global`

- 对象里调用的函数：函数的this指向 `Object`

- new 后调用的函数：函数的this指向`实例` 
比如Vue 中data的数据在methods或其他函数中调用需要使用`this.msg`
- bing后调用的函数：函数的this指向`bind的第一个参数`

- Arrow Function 调用的函数：函数的this指向`包裹Arrow Function的第一个普通函数`
因为箭头函数没有this 会不断的向父级寻找this，直到找到为止。
在微信小程序等框架中，箭头函数很好使用，有些需要定义一个例如`let that = this` 的方法，并且在需要使用this的情况下使用that即可(这个自己随便定义)，但是使用了箭头函数之后，就不需要使用这样的方法，简单而且高效。
