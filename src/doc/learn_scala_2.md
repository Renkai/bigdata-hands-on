# Scala入门(二)

## 函数

在编程中,为了能够做出更好的抽象,我们往往会把代码块整理成函数,这里介绍下在Scala中怎样定义一个函数

```scala
def add(a:Int,b:Int) = a + b
```

这是一个简化的定义,我们没有给出返回值的类型,编译器自动为我们做了这件事😄,现在我们试试在Ammonite中试一试这个函数

```scala
➜  ~ amm
Loading...
Welcome to the Ammonite Repl 1.6.8
(Scala 2.13.0 Java 1.8.0_181)
If you like Ammonite, please support our development at www.patreon.com/lihaoyi
renkai-renkai@ def add(a:Int,b:Int) = a + b
defined function add

renkai-renkai@ add(1,1)
res1: Int = 2
```

为了了解函数定义更多一点,我们再来看下`add`的完整写法

```scala
  def add(a: Int, b: Int): Int = {
    a + b
  }
```

和简化的写法相比,上面代码中的`: Int `定义了返回值的类型,花括号中包含了函数的所有类型,其中最后一行(这个例子里正好只有一行)表达式的值表示函数的返回值.在编写复杂函数的时候,建议先把返回值类型写明,这样实现逻辑的时候编译器就能帮你排错啦.

### 关键词`return`通常是是不需要的

很多语言都使用`return`关键词表示函数的返回值,出于照顾群众习惯的考虑,Scala也保留了这个关键词.但是,这通常是不必要的比如像下面这样定义一个函数,功能和上面两个版本一样,但是编译器会给出一个`Warning: Return keyword is redundant`.

```scala
  def add(a: Int, b: Int): Int = {
    return a + b // Return keyword is redundant
  }
```

定义函数的时候,如果感觉确实离不开`return`,也不要气馁,用就用吧.但是同时记得考虑下是不是能通过充分利用表达式的特性把`return`去掉.下面是比较使用和不使用`return`关键词来实现函数分支操作的一个例子.

```scala tab=使用return
  def concat(a: String, b: String): String = {
    if (a == null || b == null)
      return null
    return a + b
  }
```

```scala tab=不使用return
  def concat(a: String, b: String): String = {
    if (a == null || b == null) null
    else a + b
  }
```



## 数据结构

## Billion Dollar Mistake