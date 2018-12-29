# Java核心技术 卷I 读书笔记

## 第一章 概述

Java 关键术语

* 简单
* 面向对象
* 分布式
* 健壮性
* 安全性
* 体系结构中立
* 可移植
* 解释型
* 高性能
* 多线程
* 动态性

## 第二章 Java程序设计

## 第三章 Java基本结构设计

* 强类型语言，八种基本数据类型：byte、short、int、long、float、double、char、boolean
* 使用equal判断两个字符串是否相等，而不要用“==”
* 大数值：java.math.BigInteger 任意精度的整数，BigDecimal任意精度的浮点数

## 第四章 对象与类

* 不要使用对象调用静态方法
* 类的默认无参构造器会把所有的实例域设置为默认值（数值类型为0，bool类型为false，对象设置为null）
* 好的设计习惯：在构造器中显示对域初始化
* 使用代码块初始化域，无论调用哪个构造器，都会先执行代码块，然后才运行构造器内主体
* 类第一次加载的时候，会对静态代码块进行初始化
* 类设计技巧
  * 绝对保证数据私有
  * 显示的初始化所有的数据
  * 不要在类中过多的使用基本类型
  * 不是所有的域都需要独立的get、set方法
  * 对职责过多的类进行分解
  * 类名和方法名应该反映他们的职责
  * 优先使用不可变类

## 第五章 继承

* super与this不同，不能把super赋值给一个对象变量，super只是一个指示编译器调用超类方法的特殊关键字
* **如果将一个类声明为final，则其中的方法自动为final，而不包括域**
* 抽象类不能被实例化，但是可以引用非抽象的子类对象
* 关于Object类
  * hashCode，每个对象有一个默认的hashCode，其值为对象的存储地址
  * 如果重新定义equals方法，就必须重写hashCode方法，以便用户可以将对象插入到散列表中
  * hashCode方法应该返回一个整数值，并合理组合实例域的散列码，以便让不同对象的散列码分布均匀
  * equals与hashCode的定义必须一致，如果x.equals(y)返回true，那么x.hashCode()与y.hashCode()返回值相同。例如：如果定义Person.equals比较域ID，那么hashCode就需要散列ID，而不是其他域
  * 如果存在数组类型的域，可以用静态的Arrays.hashCode计算散列码，这个散列码由数组元素的散列码组成
  * getClass().getName()获得当前类名
  * 只要对象与一个字符串通过“+”连接，java编译器就会自动调用toString方法
  * Object类中的toString方法，用来打印出对象所属的类名和散列码
  * 数组继承了Object类的toString方法，所以打印数组最好用Arrays.toString(s)，打印多维数组用Arrays.deepToString(s)
  * **建议为自定义的每个类增加toString方法**
  * 由于每个值分别包装在对象中，因此ArrayList<Integer>的效率远远低于int[]
* 枚举类
  * 比较枚举类型的值，直接使用“==”就可以了
  * 所有枚举类型都是Enum类的子类
  * 枚举类中toString方法返回枚举常量名，如Size.SMALL.toString()返回字符串“SMALL”
  * 每个枚举类都有一个静态的values方法，它返回包含全部枚举值得数组
* 反射，能够分析类能力的程序称为反射
  * class类
    * getName方法返回类的名字，如e.getName()
    * Class.forName(className)返回类名对应的Class对象
    * T为任意的java类型（这个类型未必是一种类，如int.class是一个Class类型的对象），则T.class表示匹配的类对象
    * Class类实际上是一个泛型类，如Person.class的类型是Class<Person>
    * newInstance()可以动态的创建一个类的实例，如e.getClass().newInstance()，创建了一个与e具有相同类类型的实例
    * 将forName与newInstance配合使用，可以根据字符串中的类名创建一个对象：如```String s="java.util.Random"; Object m=Class.forName(s).newInstance();```

* 继承的设计技巧
  * 将公共操作和域放在超类
  * 不要使用受保护的域，两点：一，子类集合无限，任何一个都能从某各类派生子类，并访问protected域，破坏了封装性；二，java中同一个包中所有类都能访问protected域，而不管它是否是这个类的子类
  * 除非所有继承的方法都有意义，否则不要使用继承
  * 使用多态，而非类型信息
  * 不要过多的使用反射，反射很脆弱，编译器很难发现其中的问题

## 第六章 接口和lambda表达式以及内部类

* 接口
  * 接口中所有的方法自动属于public
  * 接口绝不能包含实例域
  * 1.8以后可以在接口中提供简单方法实现了，但是这些方法不能引用实例域——接口没有实例
  * 不能 构造接口对象，但是可以声明接口变量，接口变量必须引用实现了接口的类对象
  * 接口中的域自动设为public static final
  * java8可以在接口中增加静态方法
  * 如果在一个接口中定义了一个默认方法，又在另一个超类或者接口中定义了一个同样的方法，java解决规则：①超类优先，同名的默认方法会被忽略；②接口冲突，必须覆盖这个方法来解决冲突
  * Cloneable接口中clone方法默认为浅拷贝（只会拷贝对象，而不拷贝对象中的实例域），最好自己实现clone，建立深拷贝
* lambda表达式
  * 语法：```参数 -> 表达式```
  * 如果没有参数仍然要提供空括号：```() -> {for(...) ...}```
  * 如果可以推导一个lambda的参数类型，可以忽略其类型，如```(first, second) -> first.length()-second.length()```
  * 如果参数只有一个，而且参数类型可以推导，甚至可以省略小括号：```event -> println(...)```
  * 如果一个lambda表达式只在某些分支返回一个值，而另一些分支不返回值，这是不合法的，如```(int x) -> {if(x>0) return 1;}```
  * 函数式接口：只有一个抽象方法的接口
  * lambda表达式可以可以传递到函数式接口中的方法上
  * lambda表达式能做的也只是转换为函数式接口
  * lambda表达式可以捕获外围作用域中变量的值，但只能引用不会改变的变量
  * lambda表达式的重点是**延迟执行**
* 内部类
  * 只有内部类可以是私有的
  * 内部类中声明的所有静态域必须是final的，原因：对于每个外部对象，会分别有一个单独的内部类实例，如果这个域不是final，它可能就不是唯一的
  * 内部类不能有static方法（但也可以有静态方法，但只能访问外围类的静态域和方法）
  * 在方法中定义的类称为**局部类**，局部类不能用public或private访问修饰符声明，他的作用域被限定在声明局部类的块中
  * 局部类的优势：①对外部世界完全隐藏起来；②不仅可以访问包含他们的外部类，还可以访问局部变量，但是局部变量必须是final
  * 在内部类不需要访问外围类对象的时候，应该使用静态内部类
  * 与常规内部类不同，静态内部类可以有静态域和方法
  * 声明在接口中的内部类自动为static和public类
* 代理类
  * 代理类在运行过程中创建，创建之后与虚拟机中其他类没有区别了
  * 所有的代理类扩展Proxy类
  * 代理类一定是public和final

## 第七章 异常、断言和日志

* 异常
  * 异常对象都派生于Throwable类
  * RuntimeException包括：错误的类型转换、数组访问越界、访问null指针
* 使用断言
  * 断言机制允许在测试期间向代码中插入一些检查语句，当代码发布时，插入的检测语句就会被自动的移除
  * 语法：``assert 条件;``和``assert 条件：表达式;``，这两种都会对条件进行检测，如果结果为false，则抛出一个AssertionError异常；在第二种形式中，表达式将会被传入AssertionError的构造器，并转换成一个消息字符串
* 记录日志

## 第八章 泛型

* 泛型类可以看出是普通类的工厂
* 定义泛型类：``public static <T> T getMiddle(T... a)``
* 调用泛型方法：``String middle = Test.<String>getMiddle("tim", "Tome");``
* 不支持泛型类型的数组
* ``? extends Employee`` 限定为Employee所有子类
* ``? super Manager`` 限定为Manager所有超类

## 第九章 集合

![images](https://github.com/PrinceFeng/learning-doc/blob/master/images/20181229154049.png)

![20181229154028](https://github.com/PrinceFeng/learning-doc/blob/master/images/20181229154028.png)

* 









