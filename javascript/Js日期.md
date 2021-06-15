#  Js 日期

##  创建Dtae对象

Date 对象由Date()构造函数创建。

有4种方法创建日期对象：

###  new Dtae()

```javascript
var date = new Date();//用当前日期和时间创建新的日期对象
console.log(date);//Tue Nov 10 2020 17:49:18 GMT+0800 (中国标准时间)
```

###  new Date(year,month,day,hours,minutes,seconds,milliseconds)

用指定的日期和时间创建新的日期对象:

月份从0开始到11，表示12个月：

7个数字代表年，月，日，时，分，秒，毫秒

```javascript
var date = new Date(1998,9,25,0,0,0,0);//1998年10月25日，0点
```

6个数字代表年，月，日，时，分，秒

```javascript
var date = new Date(1998,9,25,0,0,0);//1998年10月25日，0点
```

5个数字代表年，月，日，时，分

```javascript
var date = new Date(1998,9,25,0,0);//1998年10月25日，0点
```

4个数字代表年，月，日，时

```javascript
var date = new Date(1998,9,25,0);//1998年10月25日，0点
```

3个数字代表年，月，日

```javascript
var date = new Date(1998,9,25);//1998年10月25日
```

2个数字代表年份和月份

```javascript
var date = new Date(1998,9);//1998年10
```

不能省略月份，如果只提供一个参数，则将其视为毫秒

一位数和两位数的年份将被表示为上个世纪，即19xx年

```javascript
var date = new Date(99,9,25);//2000年10月25日0点
```

```javascript
var date = new Date(9,9,25);//1910年9月25日0点
```

###  new Date(dateString)

从日期字符串创建一个日期对象

```javascript
var date = new Date("1998-10-25");
```

**JavaScript 将日期存储为毫秒**

JavaScript 将日期存储为自 1970 年 1 月 1 日 00:00:00 UTC（协调世界时）以来的毫秒数。

零时间是 1970 年 1 月 1 日 00:00:00 UTC。

###  new Date(Milliseconds)

创建一个零时加毫秒的日期对象

```javascript
var date = new Date(100000000);
```

负值代表零时(1970年1月1日)之前的日期

##  Js 日期获取方法

###  getFullYear()

获取四位的年：

```javascript
var date = new Date();
var year = date.getFullYear();//年份
```

###  getMonth()

获取月(0-11):

```javascript
var date = new Date();
var year = date.getFullYear();//月份，为0-11的数字，代表12个月
```

###  getDate()

获取天(1-31):

```javascript
var date = new Date();
var year = date.getDate();//返回天
```

###  getDay()

获取周名：0-6，其中0代表周日，1-6代表周一至周六

```javascript
var date = new Date();
var year = date.getDay();//返回周名
```

###  getHours()

获取小时(0-23):

```js
var date = new Date();
var year = date.getFullYear();//返回小时0-23
```

###  getMinutes()

获取分钟(0-59):

```js
var date = new Date();
var year = date.getMinutes();//返回分钟0-59
```

###  getSeconds()

获取秒(0-59):

```js
var date = new Date();
var year = date.getSeconds();//返回秒0-59
```

###  getMilliseconds()

获取毫秒(0-999):

```js
var date = new Date();
var year = date.getFullYear();//返回毫秒数0-999
```

###  getTime()

获取总的毫秒数：1970年1月1日以来的毫秒数

```js
var date = new Date();
var year = date.getTimer();//返回小时0-23
```

##  Js 设置日期

