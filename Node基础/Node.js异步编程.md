##  同步API，异步API

同步API：只有当前API执行完成后，才能继续执行下一个API

异步API：当前API的执行不会阻塞后续代码的执行

###  同步和异步的区别

1. 同步APi可以从返回值中拿到API执行的结果，但是异步API不可以。

2. 同步API从上到下依次执行，前面代码会阻塞后面代码的执行。

3. 先执行同步API然后执行异步API

###  解决回调嵌套

####  promise

```javascript
let promise = new promise((resolve,reject) => {
    setTimeout(() => {
        if(true) {
            resolve(success);
        }else{
            reject(error);
        }
    });
});
promise.then((success) => {
    console.log(success);
})
.catah((error) => {
    console.log(error);
})
```

####  异步函数

异步函数是异步编程语法的终极解决方案，它可以让我们将异步代码写成同步的方式，让代码不再有回调函数嵌套，使代码变得清晰明了。

```javascript
//在普通函数的定义前面加上async关键字普通函数就变成了异步函数
//异步函数默认的返回值是promise对象
//throw关键字抛出异常
async function fn() {
    throw 'error';
    return 123; 
}
console.log(fn());//Promise { 123 }
fn().then(function(data) {
    console.log(data);//123
}).catch(function(err) {
    console.log(err);//error
});
```

**await关键字**
只出现在异步函数中，暂停异步函数向下执行，直到promise对象返回结果，再向下执行

```javascript
async function p1() {
    return 'p1';
}
async function p2() {
    return 'p2';
}
async function p3() {
    return 'p3';
}
async function run() {
    let r1 = await p1();
    let r2 = await p2();
    let r3 = await p3();
}

```

**Node.js中应用异步函数**

```javascript
const fs = require('fs');
//改造现有异步函数的API 让其返回promise对象 从而支持异步函数的语法
const promisify = require('util').promisify;
//调用promisify方法改造API
const readFile = promisify(fs.readFile);
async function run() {
    let r1 = readFile('./1.txt','utf8');
    let r2 = readFile('./2.txt','utf8');
    let r3 = readFile('./3.txt','utf8');
    console.log(r1);
    console.log(r2);
    console.log(r3);
}
```

