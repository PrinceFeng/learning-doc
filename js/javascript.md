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

* (JavaScript字符串)



