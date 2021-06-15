#  对象(Object)

##  创建对象

###  通过字面量创建

```javascript
var obj1 = {};//创建一个空对象
var obj2 = {
    name: 'zhangsan',
    sex: '男',
    age: 18
}// 创建并初始化
```

###  通过new关键字创建

```javascript
var obj = new Object();//创建一个空对象
obj.name = 'zhangsan';
obj.age = 18;//为对象添加属性并给属性赋值
```

###  通过构造函数创建对象

```javascript
function Person(pname,sex,age) {
    this.pname = pname;
    this.sex = sex;
    this.age = age;
};
var obj = new Person('lisi','男',18);
```

##  访问对象

###  通过`.`访问

```javascript
var obj2 = {
    name: 'zhangsan',
    sex: '男',
    age: 18
};
console.log(obj2.name);//'zahngsan'
```

###  通过`[]`访问

```javascript
var obj2 = {
    name: 'zhangsan',
    sex: '男',
    age: 18
};
console.log(obj2['name']);//'zhangsan'
```

##  遍历对象

通过for...in....遍历：

```javascript
var obj2 = {
    name: 'zhangsan',
    sex: '男',
    age: 18
};
for(var key in obj2) {//key为对象中所有的属性
    console.log(obj2[key]);
}
//'zahngsan'   '男'   18
```

