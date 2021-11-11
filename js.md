### javascript的原始数据类型有哪些？

* strIng

* number

* boolean

* null

* undefined

* symbol

  > 其中symbol是es6新增数据类型，代表创建后唯一且不可修改的数据类型，主要是为了解决全局变量冲突

### typeof和instanceof的区别

* **typeof** 可以判断原型数据类型，在判断引用型数据时除function以外其他都为object
* **instanceof**是通过原型链判断，缺点是无法判断原始类型

instanceof 实现：

```js
function instance_of(left, right) {
  var r_prototype = right.prototype;
  var l_proto = left.__proto__;
  while (true) {
    // null 为最顶层，轮训到此结束
    if (l_proto == null) {
      return false;
    }
    if (r_prototype === l_proto) {
      return true;
    }
    // 继续向上查
    l_proto = l_proto.__proto__;
  }
}
```

### js哪些数据为false

undenfined、null、NaN、0、-0、''

### 函数中的this指向

1. **箭头函数内调用**：指向包裹它的函数

2. **bind、call、apply**：指向第一个参数，如果第一个参数为空则指向window

3. **普通函数**：取决于函数如何被调用。

   * new：指向它的实例；

   * 没有new：1.对象内部调用，this指向对象；2.直接调用，指向最终调用的对象；3.异步调用，指向window;

