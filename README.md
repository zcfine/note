##### 1.下面的值被转换为`false,`所有其他值都认为是`true`

* undefined, null
* Boolean: false
* Number: -0, +0, NaN
* String: ''

可以使用 Boolean 来测试,eg:`Boolean(undefined)`

##### 2.当需要将对象转换成数字时

```js
//调用 valueOf(),否则调用 toString(),若对象结果不是原始值，抛出一个类型错误
//eg：
> function returnObject() { return 5 }
> undefined
> 3 * { valueOf: returnObject, toString: returnObject }
> 15
//eg：
> function returnObject() { return {} }
> undefined
> 3 * { valueOf: returnObject, toString: returnObject }
> VM121:1 Uncaught TypeError: Cannot convert object to primitive value
    at <anonymous>:1:3
//如果把对象转换成字符串时，则转换操作的第一步和第二步的顺序会调换： 
//先尝试 toString() 进行转换，如果不是原始值，则再尝试使用 valueOf()。
```

![](/assets/import.png)

