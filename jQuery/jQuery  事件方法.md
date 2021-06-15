#  jQuery  事件方法

##  on()向元素添加事件处理程序

###  定义及用法

on() 方法在被选元素及子元素上添加一个或多个事件处理程序。

**注意：**使用 on() 方法添加的事件处理程序适用于当前及未来的元素（比如由脚本创建的新元素）。

**提示：**如需移除事件处理程序，请使用 <u>off()</u>方法。

**提示：**如需添加只运行一次的事件然后移除，请使用 <u>one()</u>方法。

###  语法

```javascript
$(selector).on(event,childSelector,data,function);
```

| 参数          | 描述                                                         |
| ------------- | ------------------------------------------------------------ |
| event         | 必需。规定要从被选元素添加的一个或多个事件或命名空间。由空格分隔多个事件值，也可以是数组。必须是有效的事件。 |
| childSelector | 可选。规定只能添加到指定的子元素上的事件处理程序（且不是选择器本身，比如已废弃的 delegate() 方法）。 |
| data          | 可选。规定只能添加到指定的子元素上的事件处理程序（且不是选择器本身，比如已废弃的 delegate() 方法）。 |
| function      | 可选。规定只能添加到指定的子元素上的事件处理程序（且不是选择器本身，比如已废弃的 delegate() 方法）。 |

###  实例

------

####  添加单个事件处理程序

```javascript
$(document).ready(function(){
  $("p").on("click",function(){
    alert("段落被点击了。");
  });
});
```

####  添加多个事件处理程序

```javascript
$(document).ready(function(){
  $("p").on("mouseover mouseout",function(){
    $("p").toggleClass("intro");
  });
});
```

####  使用map参数添加多个事件处理程序

```javascript
$(document).ready(function(){
  $("p").on({
    mouseover:function(){$("body").css("background-color","lightgray");},  
    mouseout:function(){$("body").css("background-color","lightblue");}, 
    click:function(){$("body").css("background-color","yellow");}  
  });
});
```

####  在元素上添加自定义事件处理程序

```javascript
$(document).ready(function(){
  $("p").on("myOwnEvent", function(event, showName){
    $(this).text(showName + "! What a beautiful name!").show();
  });
  $("button").click(function(){
    $("p").trigger("myOwnEvent",["Anja"]);
  });
});
```

####  向函数传递数据

```javascript
function handlerName(event) {
  alert(event.data.msg);
}

$(document).ready(function() {
  $("p").on("click", {msg: "You just clicked me!"}, handlerName)
});
```

####  向未来元素添加事件处理程序

```javascript
$(document).ready(function(){
  $("div").on("click","p",function(){
    $(this).slideToggle();
  });
  $("button").click(function(){
    $("<p>This is a new paragraph.</p>").insertAfter("button");
  });
});
```

####  移除事件处理程序

```javascript
$(selector).off(event);
//$('p').off('click');
```

##  off()移除通过 on() 方法添加的事件处理程序

###  定义和用法

通常用于移除通过 on() 方法添加的事件处理程序。

**注意：**如需移除指定的事件处理程序，当事件处理程序被添加时，选择器字符串必须匹配 on() 方法传递的参数。

###  语法

```javascript
$(selector).off(event,selestor,function(eventObj),map);
```

| 参数               | 描述                                                         |
| ------------------ | ------------------------------------------------------------ |
| event              | 必需。规定要从被选元素移除的一个或多个事件或命名空间。由空格分隔多个事件值。必须是有效的事件。 |
| selector           | 可选。规定添加事件处理程序时最初传递给 on() 方法的选择器。   |
| function(eventObj) | 可选。规定当事件发生时运行的函数。                           |
| map                | 规定事件映射 (*{event:function, event:function, ...})*，包含要添加到元素的一个或多个事件，以及当事件发生时运行的函数。 |

###  实例

####  移除所有通过on() 添加的click 事件处理程序

```javascript
function changeSize(){
	$(this).animate({fontSize:"+=10px"});
}
function changeSpacing(){
	$(this).animate({letterSpacing:"+=5px"});
}
$(document).ready(function(){
	$("body").on("click","p",changeSize);
	$("body").on("click","p",changeSpacing);
	$("button").click(function(){
		$("body").off("click","p");
	});
});
```

####  移除一个通过on() 添加的指定的事件函数

```javascript
function changeSize(){
	$(this).animate({fontSize:"+=10px"});
}
function changeSpacing(){
	$(this).animate({letterSpacing:"+=5px"});
}

$(document).ready(function(){
	$("p").on("click",changeSize);
	$("p").on("click",changeSpacing);
	$("button").click(function(){
		$("p").off("click",changeSize);
		alert("移除 changeSize，字体不会变大，但是字体的间距依然点一次变宽一次。");
	});
});
```

####  移除使用 event 对象的事件处理程序

```javascript
$(document).ready(function(){
    var x=0;
    $("p").click(function(event){
        $("p").animate({fontSize:"+=5px"});
        x++;
        if (x>=2)
        {
            $(this).off(event);
        }
    });
});
```

