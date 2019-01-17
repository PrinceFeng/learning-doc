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
  var x = function(a, b) {return a * b};
  // 调用
  var z = x(4, 3)
  ```

  



