## 基本语法

* 判断input里面是不是数字：

  ```javascript
  <input id="demo" type="text" >
  <script>
      function myFunction(){
          var x = document.getElementById("demo").value;
          if(x=="" || isNaN(x)){  // 此处无法判别多个空格
              alert("not a number!");
          }
  	}
  </script>
  ```

* 获取HTML元素之间的内容

  ```javascript
  var text = document.getElementsByTagName("h1")[0].innerHTML;
  ```

* javascript脚本可以放在body和head中，或者页面底部，或者外部JS文件中（此时不能包含<script>标签）

* 在标签中填写onclick调用JS函数时，不是onclick=函数名，而是onclick=函数名+()

* javascript显示数据

  * window.alert()警告框
  * document.write()将内容写到HTML中
  * innerHTML写入到HTML元素中
  * console.log()写入到浏览器控制台

* JavaScript大小写敏感

* 在JavaScript中用分号结束语句是可选的

* 在文本字符串中使用“\”对代码进行换行

* 数据类型

  * 基本类型：字符串（String）、数字（Number）、布尔（Boolean）、空（Null）、未定义（Undefined）、Symbol（ES6引入的一种新的原始数据类型，表示独一无二的值）
  * 引用数据类型：对象（Object）、数组（Array）、函数（Function）

* JavaScript拥有动态数据类型，相同的变量可用作不同的类型

  ```javascript
  var x;  // x为undefined
  var x = 5;  // x 为number
  var x = "prince"; // x为String 
  ```

* 字符串可以用单引号或双引号

* 创建数组

  ```javascript
  var arr = new Array();
  arr[0] = "aaa";
  arr[1] = "bbb";
  // 或者
  var arr = new Array("aaa", "bbb");
  // 或者
  var arr = ["aaa", "bbb"];
  ```

* 创建对象

  ```javascript
  var person = {
      firstname: "tom",
      lastname: "Diu",
      id: 555,
      fullName: function(){
          return this.firstname + " " + this.lastname;
      }
  };
  // 获取对象的值有两种方式
  name = person.firstname;
  fullname = person.fullname();  // 调用函数
  name = person["firstname"];
  ```

* 局部变量与全局变量

  ```javascript
  function myFunction() {
      carName = "oooh";  // 全局变量，在函数外面也可以访问
      var carName = "ohoho"; // 局部变量，函数外不能访问
  }
  ```

* 变量生命周期：局部变量在函数执行完毕后销毁，全局变量在页面关闭后销毁

* 常见的HTML事件：

  * onchange：HTML元素改变
  * onclick：点击HTML元素
  * onmouserover：在一个HTML元素上移动鼠标
  * onmouserout：从一个HTML元素上移开鼠标
  * onkeydown：按下键盘
  * onload：浏览器完成页面的加载

* 字符串可以是对象，不用创建String对象，会拖慢运行速度

  ```javascript
  var x = "hello";   // 类型为string
  var y = new String("hello"); // 类型为object
  ```

* ===为绝对相等，即数据类型和值都必须相等

* undefined变量声明但是没有赋值，null表示一个空对象引用，二者值相等（null==undefined），但是类型不等

* NaN的类型是number

* JavaScript中变量可以先使用后声明

* 变量提升：函数声明和变量声明总是会被解释器悄悄地被"提升"到方法体的最顶部

* 关于JavaScript中的this关键字

  * 在方法中，this表示该方法所属的对象
  * 如果单独使用，this表示全局对象
  * 在函数中，this表示全局对象
  * 函数中的严格模式下，this是未定义的（undefined）
  * 在事件中，this表示接收事件的元素
  * 类似call()和apply()方法可以将this引用到任何对象

* ECMAScript 6 新增关键字：

  * let：声明的变量只在let命令所在的代码块内有效
  * const：声明一个只读的常量，一旦声明，值就不能改变

* 使用var声明的变量不具有块级作用域，在{}在依然能访问；ES6之后，可以用let声明变量，let变量只在{}内有效

* JavaScript:void(0)：不返回任何值

* href="#"与href="javascript:void(0)"的区别：

  * "#"包含一个位置，默认的锚是"#top"，也就是网页的顶端，在页面很长时可以用"#"+id定位页面具体位置
  * javascript:void(0)仅表示一个死链接

## JS函数

* 函数可以存储在变量中

  ```javascript
  var x = function(a, b) {return a * b};  // 这里其实是一个匿名函数，通过变量来调用
  // 调用
  var z = x(4, 3)
  ```

* ES6新增箭头函数

  ```javascript
  const x = (x, y) => { return x * y };
  // 如果函数体只有一个语句，可以省略return和大括号，如下：
  const x = (x, y) => x * y
  ```

* ES6函数可以自带参数

  ```javascript
  function myFunc(x, y=10){...}
  ```

* JavaScript函数有个内置的arguments对象，它是一个函数调用的参数数组

  ```javascript
  x = findMax(1, 123, 500, 115, 44, 88);
  function findMax() {
      var i, max = arguments[0];
      
      if(arguments.length < 2) return max;
   
      for (i = 0; i < arguments.length; i++) {
          if (arguments[i] > max) {
              max = arguments[i];
          }
      }
      return max;
  }
  ```

* JavaScript闭包，闭包是可访问上一层函数作用域里变量的函数，即便上一层函数已经关闭

  ```javascript
  var add = (function () {
      var counter = 0;
      return function () {return counter += 1;}
  })();
   
  add();
  add();
  add();
  ```

  

## JavaScript HTML DOM

* 通过JavaScript操作HTML元素有三种方式：

  * 通过id找到HTML元素

    ```javascript
    var x = document.getElementById("idname");
    ```

  * 通过标签名找到

    ```javascript
    var y = document.getElementsByTagName("p");
    ```

  * 通过类名找到

    ```javascript
    var z = document.getElementsByClassName("clsName");
    ```

* JS改版HTML样式

  ```javascript
  document.getElementById("idname").style.color = "red";
  ```

* onload和onunload事件会在用户进入或离开页面时被触发，onload 事件可用于检测访问者的浏览器类型和浏览器版本，并基于这些信息来加载网页的正确版本

* onchange事件常结合对输入字段的验证来使用

* onmouseover和onmouseout事件用于鼠标移到HTML元素上或移出时触发

* onmousedown、onmouseup，点击鼠标时触发onmousedown事件，释放鼠标时触发onmouseup事件

* onfocus当输入字段获得焦点时触发

* addEventListener()方法用于向指定元素添加事件

  ```javascript
  element.addEventListener(event, function, useCapture);
  ```

   第一个参数是事件的类型 (如 "click" 或 "mousedown")

   第二个参数是事件触发后调用的函数

   第三个参数是个布尔值用于描述事件是冒泡还是捕获。该参数是可选的

  **注意不要使用"on"前缀，如使用"click"，而不是"onclick"**

* 事件冒泡或事件捕获，在冒泡中，内部元素的事件先被触发，然后再触发外部元素；在捕获中，先触发外部元素的事件，然后才触发内部元素；

  ```javascript
  // useCapture默认值为false，即冒泡传递，当为true时，使用捕获传递
  addEventListener(event, function, useCapture);
  ```

* removeEventListener()移除由addEventListener()添加的事件

## JavaScript高级特性

* 在JavaScript中，数字不分为整数类型和浮点型类型，所有的数字都是浮点型
* Boolean中的false：0、-0、null、“”、false、undefined、NaN
* Number对象
* String
* Date日期
* Array数组
* Math
* RegExp正则

## JS 浏览器对象模型

* window.screen对象包含用户屏幕的信息，使用时可省略window

  ```javascript
  <script>
  document.write("可用宽度: " + screen.availWidth);
  </script> 
  ```

* window.location获得当前页面的地址信息

* window.history 浏览器历史

* window.navigator有关访问者浏览器信息（得到的信息不可靠）

* cookie以键值对形式存储于用户电脑上的文本文件中

## ES6的一些新特性

* let不允许在相同的作用域内，重复声明同一个变量

* const只在声明所在的块级作用域内才有效

* 数组的解构赋值，ES6允许以下赋值：

  ```javascript
  // 这里可以按照对应位置给对应变量赋值，称为解构，如果解构不成功，值就为undefined
  let [a, b, c] = [1, 2, 3];
  ```

* 解构赋值允许指定默认值

  ```javascript
  let [foo = true] = [];
  foo // true
  
  let [x, y = 'b'] = ['a']; // x='a', y='b'
  let [x, y = 'b'] = ['a', undefined]; // x='a', y='b'
  ```

  注意，只有当一个数组成员严格等于undefined，默认值才会生效

  ```javascript
  let [x = 1] = [undefined];
  x // 1
  
  let [x = 1] = [null];
  x // null
  ```

* 对象的解构赋值

  ```javascript
  let { bar, foo } = { foo: "aaa", bar: "bbb" };
  foo // "aaa"
  bar // "bbb"
  
  let { baz } = { foo: "aaa", bar: "bbb" };
  baz // undefined
  ```

  对象的解构与数组有一个重要的不同。数组的元素是按次序排列的，变量的取值由它的位置决定；而对象的属性没有次序，变量必须与属性同名，才能取到正确的值。 

* 由于数组本质是对象，可以对数组进行对象属性的解构

  ```javascript
  let arr = [1, 2, 3];
  let {0 : first, [arr.length - 1] : last} = arr;
  first // 1
  last // 3
  ```

* 字符串的解构赋值

  ```javascript
  const [a, b, c, d, e] = 'hello';
  a // "h"
  b // "e"
  c // "l"
  d // "l"
  e // "o"
  // 类似数组的对象都有一个length属性，因此还可以对这个属性解构赋值。
  let {length : len} = 'hello';
  len // 5
  ```

* 函数参数得解构

  ```javascript
  [[1, 2], [3, 4]].map(([a, b]) => a + b);
  // [ 3, 7 ]
  
  // 函数参数的解构也可以使用默认值。
  function move({x = 0, y = 0} = {}) {
    return [x, y];
  }
  
  move({x: 3, y: 8}); // [3, 8]
  move({x: 3}); // [3, 0]
  move({}); // [0, 0]
  move(); // [0, 0]
  ```

* 
* 
* 
* 





3，9，15  19   20    23  24



