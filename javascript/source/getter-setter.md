> 对象rose拥有N个属性，如何在不修改源代码的情况下获取到对象rose的所有属性

```javascript
var foo = (function () {
    var rose = {
        petals: 30,
        color: 'red',
        /*更多属性*/
    };

    return function (key) {
        return rose[key];
    }
})();

```

**题目分析**
 
明显的一点，foo是一个立即执行的匿名函数，执行后返回一个匿名函数，此函数是一个闭包，可以访问到包含作用域内的变量rose。我们可以通过 `foo('petals')` 这种方式来获取rose对象某个属性的属性值，但是却无法取得rose对象的属性，因为我们无法通过闭包的函数对象取出闭包捕获的变量，除非其主动返回出来。请看下面的代码：

```javascript
var qux = (function () {
    var obj = {
        name: 'Vic',
        age: 12
    };

    return function () {
        return obj.age;
    }
})();

console.log(qux()); // 12
```

上述代码中，我们只能获取到闭包主动暴露出来的数据 `obj.age`，至少在js层面，我们是无法获取到 `obj.name` 这条数据的。

这时候，我们该如何思考呢？

Hi，Bro，看这里，看这里。

![img](www.baidu.com)

变量 rose 这个切入点我们不是还没有思考吗？
