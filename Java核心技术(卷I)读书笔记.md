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
    * 
