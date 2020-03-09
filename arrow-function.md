# 箭头函数

什么是箭头函数？

箭头函数是在ECMAScript2015 即 ES6 发布的新语法糖

其定义为
```javascript
let func = value => value
相当于↓
let func = function (value) {
    return value
};

```
(传入的参数1, 参数2, 参数3...) =>{函数体} 
如果只有一个参数，可省略括号，如果直接有return的值，可以直接写，不用return
```javascript
let exp1 = (num1, num2) => num1 + 2 * num2 //箭头后指的可以是直接return的值
let num3 = exp1(3, 5)  // 在这里将操作辅赋值给了变量num3
console.log(num3) //  13
```

简洁，而且高效

## 箭头函数的特点
- 没有this
我们需要通过查找作用域链来确定 this 的值。这一点有好处也有坏处，当然，我们肯定需要在有好处的情况下使用它来优化代码，有些时候，一些数组的map或者reduce操作中的回调函数经常使用箭头函数，在定时器中也经常见到过它的影子。

- 没有 arguments
什么是arguments？ 
我们首先了解一下，什么是重载：
 重载就是一个函数定义多次，在我知道的编程语言中，Java是支持重载的，举个例子
 ```java
public static int foo(int a, int b) {
    return a + b
}

public static int foo(int a, int b, int c) {
    return a + b + c
}
 ```

 那么，在调用这个函数的时候，如果有两个int型的参数，则执行第一个函数，即返回两个数，如果有三个参数，就执行第二个参数。
 以上是Java的重载。
 但是呢，JS是一个没有重载的语言，那么，怎么判断传入的参数呢？ -- `arguments`

举个例子：
```javascript
function foo(arguments) {  // 其实一般这里的arguments是不用写的
    if(arguments.length === 2) {
        return arguments[0] + arguments[1]
    }
    else if(arguments.length === 3) {
        return arguments[0] + arguments[1] + arguments[2]
    }
}
```

根据这个例子，可以看到，argument就是传入的参数的数组对象。他的长度和值都是依靠传入的参数决定的。
------


在箭头函数中，没有arguments


- 不能通过 new 关键字调用
JavaScript 函数有两个内部方法：[[Call]] 和 [[Construct]]。
当通过 new 调用函数时，执行 [[Construct]] 方法，创建一个实例对象，然后再执行函数体，将 this 绑定到实例上。
当直接调用的时候，执行 [[Call]] 方法，直接执行函数体。
箭头函数并没有 [[Construct]] 方法，不能被用作构造函数，如果通过 new 的方式调用，会报错.
举个例子
```javascript
var Foo = () => {};
var foo = new Foo(); // TypeError: Foo is not a constructor
```

- 没有 new.target


因为没有new操作符， 所以没有new.target

- 没有原型

- 没有super


相关知识 this.md 作用域链.md(还没写呢) 重载.md (下次改)