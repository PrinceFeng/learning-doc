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

* javascript脚本可以放在body和head中，或者页面底部

* 









