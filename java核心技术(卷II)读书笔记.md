# java核心技术卷2（v10）

## 第一章 Java SE 8的流库

* 流并不存储元素。这些元素可能存储在底层的集合中，或者按需生成的

* 流的操作不会修改其数据

* 流的操作是尽可能惰性执行的，也就是直至需要结果时，操作才会执行

  ```java
  // 统计单词个数
  long count = words.stream().filter(w -> w.length() > 5).count();
  ```

  这里stream会产生一个用于words列表的流，filter会返回另一个流，其中只包含长度大于5的单词，count会将这个流化简为一个结果。

* 流API

  ```java
  java.util.stream.Stream<T> 8
      * Stream<T> filter(Predicate<? super T> p)
      	产生一个流，其中包含当前流中满足P的所有元素
      * long count()
      	产生当前流中元素的数量，这是一个终止操作
      * static <T> Stream<T> of(T... values)
      	产生一个元素为给定值的流
      * static <T> Stream<T> empty()
      	产生一个不包含任何元素的流
      * static <T> Stream<T> generate(Supplier<T> s)
      	产生一个无限流，它的值是通过反复调用函数s而构建的
      * static <T> Stream<T> iterate(T seed, UnaryOperator<T> f)
      	产生一个无限流，它的元素包含种子、在种子上调用f产生的值、在前一个元素上调用f			产生的值，等等。
  java.util.Collection<E> 1.2
      * default Stream<E> stream()
      * default Stream<E> parallelStream()
      	产生当前集合中所有元素的顺序流或并行流
  ```

* 

