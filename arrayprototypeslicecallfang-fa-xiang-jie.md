# Array.prototype.slice.call\(\)方法详解

原文链接：[https://www.cnblogs.com/dingxiaoyue/p/4948166.htm](https://www.cnblogs.com/dingxiaoyue/p/4948166.html)

* Array.prototype.slice

slice从字面上的意思很容易理解就是截取， 这方法如何使用呢?

`arrayObj.slice(start, [end])`

很显然是截取数组的一部分。

* this总是指向调用某个方法的对象，但是使用call\(\)和apply\(\)方法时，就会改变this的指向。

```js
//把调用方法的参数截取出来
function test(a,b,c,d) { 
    var arg = Array.prototype.slice.call(arguments,1); 
    console.log(arg); 
} 
test("a","b","c","d"); //["b", "c", "d"]
```

* 多次用到 Array.prototype.slice.call\(arguments, 1\)，不就是等于 arguments.slice\(1\) 吗？

* 其实arguments并不是真正的数组对象，只是与数组类似而已，所以它并没有slice这个方法，而`Array.prototype.slice.call(arguments, 1)`可以理解成是让arguments转换成一个数组对象，让arguments具有slice\(\)方法。要是直接写arguments.slice\(1\)会报错。

```js
typeof arguments==="Object" //而不是 "Array"
```

* #### `Array.prototype.slice.call(arguments)`能将具有length属性的对象转成数组，除了IE下的节点集合（因为ie下的dom对象是以com对象的形式实现的，js对象与com对象不能进行转换）

```js
var a={length:2,0:'first',1:'second'};//类数组,有length属性，长度为2，第0个是first，第1个是second
console.log(Array.prototype.slice.call(a,0));// ["first", "second"],调用数组的slice(0);

var a={length:2,0:'first',1:'second'};
console.log(Array.prototype.slice.call(a,1));//["second"]，调用数组的slice(1);

var a={0:'first',1:'second'};//去掉length属性，返回一个空数组
console.log(Array.prototype.slice.call(a,0));//[]

function test(){
  console.log(Array.prototype.slice.call(arguments,0));//["a", "b", "c"]，slice(0)
  console.log(Array.prototype.slice.call(arguments,1));//["b", "c"],slice(1)
}
test("a","b","c");
```

* #### 将函数的实际参数转换成数组的方法

方法一：`var args = Array.prototype.slice.call(arguments);`

方法二：`var args = [].slice.call(arguments, 0);`

方法三：

```js
var args = []; 
for (var i = 1; i < arguments.length; i++) { 
    args.push(arguments[i]);
}
```

转成数组的通用函数：

```js
var toArray = function(s){
    try{
        return Array.prototype.slice.call(s);
    } catch(e){
        var arr = [];
        for(var i = 0,len = s.length; i < len; i++){
            //arr.push(s[i]);
               arr[i] = s[i];  //据说这样比push快
        }
         return arr;
    }
}
```



