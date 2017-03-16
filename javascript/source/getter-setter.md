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

![img](https://github.com/elegantspirit/interview/blob/master/javascript/source/assets/code.png)

变量 rose 这个切入点我们不是还没有思考吗？

变量rose是一个对象，打开chrome，F12，输入`Object.prototype`

![img](https://github.com/elegantspirit/interview/blob/master/javascript/source/assets/getter.png)

Object原型上的 `__defineGetter__` 方法可以将一个函数绑定到当前对象的指定属性上，当那个属性被读取时，便会触发绑定的函数

```javascript
var o = {};

o.__defineGetter__('name', function () {
    return 'reading';
});

console.log(o.name); // 'reading'
```

只是这个方法是非标准的，Web标准中也已经删除了这个方法，下面的写法是被推荐的

```javascript
var o = {};

Object.defineProperty(o, 'name', function () {
    get: function () {
        return 'reading';
    }
});
```

看到这里，不知道小伙伴们脑海里是否蹦出了灵感的火花？还是说，依然懵逼中？不啰嗦了，上代码

```javascript
var qux = Symbol();

Object.defineProperty(Object.prototype, qux, function () {
    get: function () {
        return this;
    }
});

var baz = foo(qux);
```

Object的原型上定义一个属性，且必须保证此属性在对象rose上是不存在的，这里我们用到了ES6新增加的基本数据类型 Symbol，然后调用题目中的自执行函数，
通过函数内的闭包，我们可以访问到对象rose上的qux属性，由于qux的唯一性，rose上是不会存在qux这个属性的。之后便顺着原型链，在Object这里找到了qux
属性，此时便触发了get函数，返回了this对象，也就是我们需要的rose对象。
