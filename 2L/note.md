# 学习笔记：Making an App Interactive


## 关键词

- Activity
    >  An activity is a single, focused thing that the user can do. 
    > 
    >  Activity是一件用户可以做的单一，专门的事物。

- File Extention

    >  a group of letters occurring after a period in a file name, indicating the format of the file.
    > 
    >  一组文件名后出现的字母，表示文件的格式。
     
- Comment

    > Comments can be used to summarize code or to explain the programmer's intent.
    >  
    > 注释可以用来总结代码或解释程序员的意图。
    
- Method

    > A Method provides information about, and access to, a single method on a class or interface. The reflected method may be a class method or an instance method (including an abstract method).
    >
    > 一个方法提供了一个类或接口中一个方法（函数）的信息和访问方式。被反射的方法可以是类方法或实例方法。

- Variable

    > A Java variable is a piece of memory that can contain a data value.
    >
    > Java变量（区别于数学变量）是一段可储存数据的内存。
    
&nbsp;
## Comment

![image](https://github.com/mark818/google_study_jams/raw/master/2L/2L-1.png)

Comment既注释。注释和源代码一起出现在源文件中，并会被根据它的语法被编译器识别并跳过，因为注释的真正意义是帮助读者理解代码。Java中的注释有两种语法，单行注释与多行注释。

#### Single Line Comment

单行注释使用双反斜线```//```符号。使用该符号后，该行```//```后面的内容全部作为注释，被编译器忽略。如

```Java
public class Test { // 声明类名
    private int test; // 私有整型成员变量
    
    public Test() { // 构造函数
        test = 0; // 初始化成员变量
    }
}
```

上述代码中所有的中文都出现在```//```之后作为注释，方便读者理解代码。

#### Multiline Comment

多行注释使用开始符号```/*```和结束符```*/```。无论这两个符号出现在句首，句尾还是句中，只要它们之间的相对前后关系不变，两个符号中间的内容都会被注释。

```Java
public class Test {
    private int /* 这是一句插在中间的注释*/ test;
    
    public Test() { /* 这是一句
        多行的
        注释 */  test = 0;
    }
}
```

上述用法会影响代码美观，通常不将注释插入到代码中。这么写是为了方便解释规则。

## onClick

onClick是本章中新介绍的XML属性，能够调用java源码中的同名函数。其背后实现涉及C++反射，原理较为复杂。我在线下的活动中向组员粗略解释了一下，作为彩蛋，这里就不说了。

顾名思义，onClick控制的是被按下时的行为。而这个行为表现为调用一个Java方法。

## Method

方法是本章的重头戏，也是Java和XML最大的区别。Java的内容都封装在类里，而类的功能都由一个或多个方法实现。一个方法就像一个数学函数，它接受一些参数（输入），返回一个结果（输出）。方法的定义分为签名和实现。

#### Signature

签名规定了方法名，方法接收的形参列表，以及方法返回值类型。除此以外还有可选的访问控制关键词，如public/private/protected，static，final等等。下面看一个例子：

```Java
public static void test(String []args)
```

上述是test方法的签名，它接受一个String数组；返回类型为空，即不返回结果；static表示它是类唯一方法，被所有实例共享；public表示它访问权限为公开，其他类和包都能访问它。

#### Implementation

实现则是函数真正做事的地方。在签名后面写一对大括号，大括号内的代码将被执行，同时可以使用形参列表，并必须返回指定类型的结果。

```Java
public static void test(String []args) { // 大括号可换行可不换行，按传统不换行
    System.out.println("Hello World");
}
```

上述代码实现了test方法，内容为在标准输出中输出```Hello World```并换行。

#### Invokation

方法写出来的最终目的就是被使用，因此方法的调用规则也尤其重要。我们仍旧使用方法的名字，按照匹配的形参类型传入对应的实参，同时接收它的返回值。

```Java
public static void main(String []args) { // 大括号可换行可不换行，按传统不换行
    test(args);
}
```

上述main方法在它的实现中调用了test方法，并传入了对应的实参。因为该函数返回类型为空，所以不接受返回值。

## Arithmatic Operators

![image](https://github.com/mark818/google_study_jams/raw/master/2L/2L-2.png)

数学计算是编程中必不可少的一环。Java提供了常用的数学运算符号：```+ - * /```用来计算，并用```()```来改变运算优先顺序，一切都和小学数学教的一样。要注意的是Java里的数学运算不使用中括号和大括号，用嵌套的小括号表达多级顺序即可。

## "+" in String class

但是这里有个例外，在常用的字符串操作中经常有合并两个字符串的操作。为了方便书写，Java为字符串定义了特殊的+号。当+号两边有一个参数是字符串时，另一个参数（如果不是字符串）将被尝试强制转换成字符串，若成功即将右边字符串的内容拼接在左边字符串内容之后作为结果，生成一个新的字符串。通常被转换的参数是一个数字，整型或浮点。当连加出现时，表达式将按从左到右的顺序，把第一个加号产生的结果替换整个加法表达式，然后计算下一个加。如

```Java
"a" + 2 + 3 + "bc" + 5 = 
"a2" + 3 + "bc" + 5 = 
"a23" + "bc" + 5 = 
"a23bc" + 5 = 
"a23bc5"
```

当然这个过程对人是不可见的。这种推导行为被称作String concatenation。

![image](https://github.com/mark818/google_study_jams/raw/master/2L/2L-3.png)

## Variable

![image](https://github.com/mark818/google_study_jams/raw/master/2L/2L-4.png)

方法是Java的重要组成部分，变量则是另一部分。它和在代码中直接写数字最大的区别就是它可变。变量指定了计算机中一块内存来储存一种指定类型的数据，并可以被方法查看和修改。声明变量的语法类似方法签名，没有了形参列表，多了可选的初始值。如

```Java
public class Test { // 声明类名
    private int test; // 私有整型成员变量
    
    public Test() { // 构造函数
        test = 0; // 初始化成员变量
    }
}
```

这是解释注释时使用的例子，我们看到test是一个变量，拥有private访问权限，类型为int，名字为test。变量还可以被初始化一个值，如

```Java
public class Test { // 声明类名
    private int test; // 私有整型成员变量
    
    public Test() { // 构造函数
        int dumb = 1;
        test = dumb; // 初始化成员变量
    }

}
```

这里dumb变量是一个定义在方法中的局部变量，并被初始化成1。它的值随后通过```=```号赋给了test成员变量。

## Alice Yang的访谈

2A和2B的最后，讲师采访了Gmail的负责人Alice Yang，请她回顾自己入职Google以来的心路历程，如何克服各种困难。其中重点则是如何调试有错的程序，并利用Android Studio的可视化调试器快速定位错误。在后半段中她提到了Gmail使用了哪些Java变量，比如储存姓名和邮箱的String变量，记录邮件数量的int变量等等。