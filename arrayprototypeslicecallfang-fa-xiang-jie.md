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



