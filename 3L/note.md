# 学习笔记：Object-Oriented Programming


## 关键词

- Method

    > A Method provides information about, and access to, a single method on a class or interface. The reflected method may be a class method or an instance method (including an abstract method).
    >
    > 一个方法提供了一个类或接口中一个方法（函数）的信息和访问方式。被反射的方法可以是类方法或实例方法。

- Variable

    > A Java variable is a piece of memory that can contain a data value.
    >
    > Java变量（区别于数学变量）是一段可储存数据的内存。
    
- Class

    > A class is nothing but a blueprint or a template for creating different objects which defines its properties and behaviors. Java class objects exhibit the properties and behaviors defined by its class. A class can contain fields and methods to describe the behavior of an object.
    >
    >

- Data Type
    > A data type or simply type is a classification of data which tells the compiler or interpreter how the programmer intends to use the data.
    >
    >

- Conditional
    
    > In computer science, conditional statements, conditional expressions and conditional constructs are features of a programming language, which perform different computations or actions depending on whether a programmer-specified boolean condition evaluates to true or false.
    >
    >

&nbsp;

## Method

> 方法是本章的重头戏，也是Java和XML最大的区别。Java的内容都封装在类里，而类的功能都由一个或多个方法实现。一个方法就像一个数学函数，它接受一些参数（输入），返回一个结果（输出）。方法的定义分为签名和实现。

上一章的笔记讲解了方法的基本概念。在这一章中讲师重点展开了方法的细节，我就上章的笔记做一些补充。

#### Definition

> 签名规定了方法名，方法接收的形参列表，以及方法返回值类型。除此以外还有可选的访问控制关键词，如public/private/protected，static，final等等。下面看一个例子：

```Java
public static void test(String []args)
```

> 上述是test方法的签名，它接受一个String数组；返回类型为空，即不返回结果；static表示它是类唯一方法，被所有实例共享；public表示它访问>权限为公开，其他类和包都能访问它。

这章的视频不再把函数签名和实现分开讲解，而是同意成为定义。同时它提供了一个更清晰的图解，我们依次对每部分展开
![image](https://github.com/mark818/google_study_jams/raw/master/3L/3L-1.png)

- Access modifier
    - 方法的访问权限分为public，private和default。
    - public表示该方法对任何文件里的任何方法都可见。
    - private表示该方法只对类内方法可见，类外均不可见。此处注意，main可见其所在类内的private方法和变量。

- Return data type
    - 方法对应数学中的函数，调用它是为了完成某种计算。通常我们想要它返回一个结果，而Java需要我们规定返回结果的数据类型。
    - 返回的类型可以是任何变量类型，包括基本变量和类对象，加上特殊的无返回关键词void，表示函数没有返回值，如main。
    - Java中有一种特殊的方法-构造函数；它不返回数据且不需要声明返回类型。

- Method name
    - 方法名和变量名一样，首字母必须是大小写字母或$或_，其他部分可以是任何unicode字符，如汉字。
    - 与变量名一样，方法名不能与[Java保留关键词](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/_keywords.html)
    冲突。
    - 同类中两个方法如果有相同名字，则形参列表必须不同，形成重载（本章没有涉及）。

- Parameter list
    - 形参列表以小括号开始，小括号结束，其中每个形参以逗号分隔
    - 每个形参声明语法为```参数类型 参数名```
    - 形参数量没有限制，但是过多参数会影响程序运行效率。
    - e.g. 
        ```(int arg1, float arg2, String arg3)```

然后再看一个例子
![image](https://github.com/mark818/google_study_jams/raw/master/3L/3L-2.png)

#### Input parameters / Arguments

这两种术语是一个意思，但是我更喜欢使用arugments，来和定义中的paramters区分开。

- 在中文中arguments被称为实参，与形参形成呼应。
- 方法里的形参定义了一个规则，既我接受的参数应该是怎么样，但是没有提供真正的数据 (毕竟方法是能处理变量的，如果定死了数据就失去了它的意义)。
- 实参则是调用方法时传入的真实数据，是实实在在的。
- 传入实参时只需输入变量名或字面值常量，由编译器检查类型是否与形参匹配。
- 实参数量和类型应与形参一一对应（除可变参数列表），而变量名可以不同（通常都不同，想想为什么）。
- 如果在开发过程中修改了方法的形参列表，则代码中所有对该方法的调用都要对应地修改实参列表。

#### Execution

一个正确的方法开始执行后总是会终止，也许几纳秒（加法函数），也许几年（服务器操作系统的主循环，直至硬件原因终止）。Java方法的终止条件有三：

- 所有语句执行完毕。
- 逐行运行时遇到了return语句
    - return语句应带有包含对应方法返回类型的变量，除非返回类型为void。
    - return语句直接导致方法终止，后面所有的代码都不会被执行。
    - 事实上一个非void的方法必须拥有return语句。
- 遇到运行时错误（RuntimeException）。

#### Use return value

方法返回的值可以被调用该方法的方法保留和使用。语法和声明一个普通变量类似，方法调用在等号右边作为这个变量初始化/赋值的对象。

![image](https://github.com/mark818/google_study_jams/raw/master/3L/3L-3.png)

我们看一个例子：

```Java
public int add(int left, int right) {
    return left + right;
}

public void useAdd() {
    int sum = useAdd(1, 2);
}
```

上述代码中，useAdd方法调用了add方法，传入实参1和2，并将得到的结果用来初始化一个局部变量sum。

#### Invocation

> 方法写出来的最终目的就是被使用，因此方法的调用规则也尤其重要。我们仍旧使用方法的名字，按照匹配的形参类型传入对应的实参，同时接收它的返回值。

有了上面的解释，调用的规则已经呼之欲出了。上一节的例子就是一个完整的调用。要注意的是返回值并非必须被保留，很多时候我们选择不接收返回值。

## Resource IDs

资源ID作为XML中的字符串，是不能在Java中作为变量名直接访问的。为了解决这个问题，Android在每个项目中自动生成一个叫R的类，并用静态变量的方式提供了Acitivity中所有的id和其他更多的id，大大提升了开发效率。

## Class vs Object

课程进行到第三章终于讲到了Java和所有面向对象语言的核心概念：类和对象。
类和对象虽在口语中经常被混用，其实他们是不同却又紧密联系的两个概念。

#### Class
- 类是方法和变量的封装，将程序员从繁杂的细节中解放出来，以面向对象的高度抽象角度设计软件架构。
- 类通过继承实现了代码重用，提高开发效率。
- 类通过虚函数实现运行时多态，使开发更灵活。

#### Object
- 对象是类的实例。
- 一个类可以产生任意多的对象。
- 每个对象拥有自己的一份类中声明的成员变量和函数。

举个例子，类是细胞核中的RNA，对象就是细胞根据RNA造出的蛋白质，拥有RNA描述的一切性状。

#### Create Object

上面说到对象是类的实例，现在我们从语法上来分析一下实例化对象的过程。
![image](https://github.com/mark818/google_study_jams/raw/master/3L/3L-4.png)
联想一下定义基本变量的语法，我们类似的有

- 变量类型，这就是类名
- 变量名

而不同的是等号右边

- new关键字，表示新建了一个对象，也是区分对象和基本类型的关键。
- 类名+参数列表，在视频中虽然分开列，但是其实它们一起通过参数匹配调用了类的对应构造方法。

图上的例子对应语法模版实例化了不同类的对象。需要注意的是，与C++不同，即使调用无参数的默认构造方法，Java中的代码也不可以省略()。

#### Call Methods on Object

在类外调用类中的方法时并不像之前那样方便，需要用到点运算符。
![image](https://github.com/mark818/google_study_jams/raw/master/3L/3L-4.png)
我们使用```对象名.方法（参数列表）```的方式调用，且受到访问权限(Access modifier)限制。

#### Inheritance

继承又是一个面向对象的关键技术。

- 当一个类继承于另一个类时，我们将被继承的类称为基类（父类），继承类称为派生类（子类）。
- 派生类自动沿用基类的所有非private变量和构造方法以外所有非private方法。
- 派生类使用完全相同签名的方法可以覆盖基类的方法，从而实现多态。

![image](https://github.com/mark818/google_study_jams/raw/master/3L/3L-5.png)
而由于话题较大，且视频中没有展开，就简单带过了

## findViewById

这个方法太重要了，所以视频中单独提出来讲解。与javascript中findElementById一样，这是代码与XML交互的主要渠道。它接收一个id，返回一个Object，要求程序员自己进行类型转换得到想要的View。这个方法背后是著名的工厂模式思想，这里就不展开了。
