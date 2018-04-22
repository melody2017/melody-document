[TOC]
## 1、面向对象的特征有哪些方面? 【基础】 

面向对象的特征主要有以下几个方面： 

1. 抽象：抽象就是忽略一个主题中与当前目标无关的那些方面，以便更充分地注意与当前目标有关的方面。抽象并不打算了解全部问题，而只是选择其中的一部分，暂时不用部分细节。抽象包括两个方面，一是过程抽象,二是数据抽象。 

2. 继承：继承是一种联结类的层次模型，并且允许和鼓励类的重用，它提供了一种明确表述共性的方法。对象的一个新类可以从现有的类中派生，这个过程称为类继承。新类继承了原始类的特性，新类称为原始类的派生类（子类），而原始类称为新类的基类（父类）。派生类可以从它的基类那里继承方法和实例变量，并且类可以修改或增加新的方法使之更适合特殊的需要。 

3. 封装：封装是把过程和数据包围起来，对数据的访问只能通过已定义的界面。面向对象计算始于这个基本概念，即现实世界可以被描绘成一系列完全自治、封装的对象,这些对象通过一个受保护的接口访问其他对象。 

4. 多态性：多态性是指允许不同类的对象对同一消息作出响应。多态性包括参数化多态性和包含多态性。多态性语言具有灵活、抽象、行为共享、代码共享的优势，很好的解决了应用程序函数同名问题。 

## 2、作用域public,private,protected,以及不写时的区别？【基础】 

答：区别如下： 

|作用域|当前类|同包|子孙类|其他|
|:---:|:---:|:---:|:---:|:---:|
|public|√|√|√|√| 
|protected|√|√|√|×| 
|default|√|√|×|×| 
|private|√|×|×|×| 

不写时默认为default。 

## 3、String 是最基本的数据类型吗? 【基础】 

不是。 

## 4、float 型float f=3.4是否正确? 【基础】 

答:不正确；精度不准确,应该用强制类型转换，如下所示：float f=(float)3.4 。 

## 5、语句float f=1.3；编译能否通过？【基础】 

答:不能；应该用强制类型转换，如下所示：float f=(float)1.3； 。 

## 6、short s1 = 1; s1 = s1 + 1;有什么错? 
答：short s1 = 1; s1 = s1 + 1;s1+1运算结果是int 型，需要强制转换类型；short s1 = 1; s1 += 1;可以正确编译,自动类型提升。 

## 7、Java 有没有goto? 【基础】 

答：goto 是java 中的保留字，现在没有在java 中使用。 

## 8、int 和Integer 有什么区别? 【基础】 

答：Java 提供两种不同的类型：引用类型和原始类型（或内置类型）； 
int 是java 的原始数据类型，Integer 是java 为int 提供的封装类。 
Java 为每个原始类型提供了封装类： 
原始类型: boolean,char,byte,short,int,long,float,double 
封装类型：Boolean，Character，Byte，Short，Integer，Long，Float，Double引用类型和原始类型的行为完全不同，并且它们具有不同的语义。引用类型和原始类型具有不同的特征和用法，它们包括：大小和速度问题，这种类型以哪种类型的数据结构存储，当引用类型和原始类型用作某个类的实例数据时所指定的缺省值。对象引用实例变量的缺省值为，而原始类型实例变量的缺省值与它们的类型有关。 

## 9、&和&&的区别？【基础】 

答：&是位运算符，表示按位与运算，&&是逻辑运算符，表示逻辑与（and）。 

## 10、简述逻辑操作(&,|,^)与条件操作(&&,||)的区别？【基础】 

答：区别主要有两点：a.条件操作只能操作布尔型的,而逻辑操作不仅可以操作布尔型,而且可以操作数值型b.逻辑操作不会产生短路。 

## 11、heap 和stack 有什么区别？【基础】 

答：栈是一种线形集合，其添加和删除元素的操作应在同一段完成，栈按照后进先出的方式进行处理；堆是栈的一个组成元素。 

## 12、Math.round(11.5) 等于多少? Math.round(-11.5)等于多少? 【基础】 

答：Math.round(11.5)==12 Math.round(-11.5)==-11 round 方法返回与参数最接近的长整数，参数加1/2 后求其floor。 

## 13、swtich 是否能作用在byte 上，是否能作用在long 上，是否能作用在String上? 【基础】 

答：switch（expr1）中，expr1 是一个整数表达式。因此传递给switch 和case语句的参数应该是int、short、char 或者byte。long,string 都不能作用于swtich。 

## 14、编程题: 用最有效率的方法算出2 乘以8 等於几? 【基础】 

答： 2 << 3。 

## 15、有没有length()这个方法? String 有没有length()这个方法？【基础】 

答：数组没有length()这个方法，有length 的属性。String 有length()这个方法。 

## 16、在JAVA 中，如何跳出当前的多重嵌套循环？【基础】 

答：在最外层循环前加label 标识,然后用break:label 方法即可跳出多重循环。 

## 17、构造器Constructor 是否可被override? 【基础】 

答：构造器Constructor 不能被继承，因此不能重写Overriding，但可以被重载Overloading。 

## 18、两个对象值相同(x.equals(y) == true)，但却可有不同的hash code，这句话对不对? 【基础】 

答：不对，有相同的hash code。 

## 19、是否可以继承String 类? 【基础】 

答：String 类是final 类，故不可以继承。 

## 20、以下二条语句返回值为true 的有： 

A：“beijing”==“beijing”； 

B：“beijing”.equalsIgnoreCase（new String（“beijing”））；【基础】 

答：A 和B 。 

## 21、当一个对象被当作参数传递到一个方法后，此方法可改变这个对象的属性，并可返回变化后的结果，那么这里到底是值传递还是引用传递? 【基础】 

答：是值传递。Java 编程语言只有值传递参数。当一个对象实例作为一个参数被传递到方法中时，参数的值就是对该对象的引用。对象的内容可以在被调用的方法中改变，但对象的引用是永远不会改变的。 

## 22、我们在web 应用开发过程中经常遇到输出某种编码的字符，如iso8859-1等，如何输出一个某种编码的字符串？【基础】 
```JAVA
public String translate(String str){  
String tempStr = "";  
try{  
tempStr = new String(str.getBytes("ISO-8859-1"), "GBK");  
tempStr = tempStr.trim();  
}catch (Exception e){  
System.err.println(e.getMessage());  
}  
return tempStr;  
}  
```
## 23、String 和StringBuffer 的区别? 【基础】 

答：JAVA 平台提供了两个类：String 和StringBuffer，它们可以储存和操作字符串，即包含多个字符的字符数据。这个String 类提供了数值不可改变的字符串。而这个StringBuffer 类提供的字符串进行修改。当你知道字符数据要改变的时候你就可以使用StringBuffer。典型地，你可以使用StringBuffers 来动态构造字符数据。 

## 24、String, StringBuffer StringBuilder 的区别。【基础】 

答：String 的长度是不可变的；StringBuffer 的长度是可变的，如果你对字符串中的内容经常进行操作，特别是内容要修改时，那么使用StringBuffer，如果最后需要String，那么使用StringBuffer 的toString()方法；线程安全；StringBuilder 是从JDK 5 开始，为StringBuffer 该类补充了一个单个线程使用的等价类；通常应该优先使用StringBuilder 类，因为它支持所有相同的操作，但由于它不执行同步，所以速度更快。 

##25、Overload 和Override 的区别。Overloaded 的方法是否可以改变返回值的类型? 【基础】 

答：方法的重写Overriding 和重载Overloading 是Java 多态性的不同表现。重写Overriding 是父类与子类之间多态性的一种表现，重载Overloading 是一个类中多态性的一种表现。如果在子类中定义某方法与其父类有相同的名称和参数，我们说该方法被重写(Overriding)。子类的对象使用这个方法时，将调用子类中的定义，对它而言，父类中的定义如同被“屏蔽”了。如果在一个类中定义了多个同名的方法，它们或有不同的参数个数或有不同的参数类型，则称为方法的重载(Overloading)。Overloaded 的方法是可以改变返回值的类型。 

## 26、定义类A 和类B 如下：【基础】 
```JAVA 
class A {  
int a=1;  
double d=2.0;  
void show(){  
System.out.println("Class A: a="+a +"   d="+d);  
}  
}  
class B extends A{  
float a=3.0f;  
String d="Java program.";  
void show(){  
super.show( );  
System.out.println("Class B: a="+a +"   d="+d);  
}  
}  
```
(1) 若在应用程序的main 方法中有以下语句： 

A a=new A(); 

a.show(); 

则输出的结果如何？ 

(2) 若在应用程序的main 方法中定义类B 的对象b： 

A b=new B(); 

b.show(); 

则输出的结果如何？ 

答：输出结果为： 

1）Class A: a=1 d=2.0 ； 

2）Class A: a=1 d=2.0 

Class B: a=3.0 d=Java program。 

## 27、描述一下JVM 加载class 文件的原理机制? 【基础】 

答：JVM 中类的装载是由ClassLoader 和它的子类来实现的,Java ClassLoader是一个重要的Java 运行时系统组件。它负责在运行时查找和装入类文件的类。 

## 28、char 型变量中能不能存贮一个中文汉字?为什么? 【基础】 

答：能够定义成为一个中文的，因为java 中以unicode 编码，一个char 占16个字节，所以放一个中文是没问题的。 

## 29、abstract class 和interface 有什么区别? 【基础】 

答：声明方法的存在而不去实现它的类被叫做抽象类（abstract class），。然而可以创建一个变量，其类型是一个抽象类，它用于要创建一个体现某些基本行为的类，并为该类声明方法，但不能在该类中实现该类的情况。不能创建abstract 类的实例并让它指向具体子类的一个实例。不能有抽象构造函数或抽象静态方法。Abstract 类的子类为它们父类中的所有抽象方法提供实现，否则它们也是抽象类为。取而代之，在子类中实现该方法。知道其行为的其它类可以在类中实现这些方法。接口（interface）是抽象类的变体。新型多继承性可通过实现这样的接口而获得。接口中的所有方法都是抽象的，所有成员变量都是publicstatic final 的。一个类可以实现多个接口，当类实现特殊接口时，它定义（即 

将程序体给予）所有这种接口的方法。然后，它可以在实现了该接口的类的任何对象上调用接口的方法。由于有抽象类，它允许使用接口名作为引用变量的类型。通常的动态联编将生效。引用可以转换到接口类型或从接口类型转换，instanceof 运算符可以用来决定某对象的类是否实现了接口。 

## 30、Static Nested Class 和Inner Class 的不同？【基础】 

答：Static Nested Class 是被声明为静态（static）的内部类，它可以不依赖于外部类实例被实例化。而通常的内部类需要在外部类实例化后才能实例化。 

## 31、java 中会存在内存泄漏吗，请简单描述。【基础】 

答：会；存在无用但可达的对象，这些对象不能被GC 回收，导致耗费内存资源。 

## 32、abstract 的method 是否可同时是static,是否可同时是native，是否可同时是synchronized? 【基础】 

答：都不能。 

## 33、静态变量和实例变量的区别？【基础】 

答：静态变量也称为类变量，归全类共有，它不依赖于某个对象，可通过类名直接访问；而实例变量必须依存于某一实例，只能通过对象才能访问到它。 

## 34、是否可以从一个static 方法内部发出对非static 方法的调用？【基础】 

答：不可以,如果其中包含对象的method()，不能保证对象初始化。 

## 35、写clone()方法时，通常都有一行代码，是什么？【基础】 

答：Clone 有缺省行为：super.clone()，他负责产生正确大小的空间，并逐位复制。 

## 36、GC 是什么? 为什么要有GC? 【基础】 

答：GC 是垃圾收集的意思（Gabage Collection）,内存处理是编程人员容易出现问题的地方，忘记或者错误的内存回收会导致程序或系统的不稳定甚至崩溃，Java 提供的GC 功能可以自动监测对象是否超过作用域从而达到自动回收内存的目的，Java 语言没有提供释放已分配内存的显示操作方法。Java 程序员不用担心内存管理，因为垃圾收集器会自动进行管理。要请求垃圾收集，可以调用下面的方法之一：System.gc() 或Runtime.getRuntime().gc() 。 

## 37、垃圾回收的优点和原理。并考虑2 种回收机制。【基础】 

答：Java 语言中一个显著的特点就是引入了垃圾回收机制，使c++程序员最头疼的内存管理的问题迎刃而解，它使得Java 程序员在编写程序的时候不再需要考虑内存管理。由于有个垃圾回收机制，Java 中的对象不再有“作用域”的概念，只有对象的引用才有“作用域”。垃圾回收可以有效的防止内存泄露，有效的使用可以使用的内存。垃圾回收器通常是作为一个单独的低级别的线程运行，不可预知的情况下对内存堆中已经死亡的或者长时间没有使用的对象进行清楚和回收，程序员不能实时的调用垃圾回收器对某个对象或所有对象进行垃圾回收。回收机制有分代复制垃圾回收和标记垃圾回收，增量垃圾回收。 

## 38、垃圾回收器的基本原理是什么？垃圾回收器可以马上回收内存吗？有什么办法主动通知虚拟机进行垃圾回收？【基础】 

答：对于GC 来说，当程序员创建对象时，GC 就开始监控这个对象的地址、大小以及使用情况。通常，GC 采用有向图的方式记录和管理堆(heap)中的所有对象。通过这种方式确定哪些对象是"可达的"，哪些对象是"不可达的"。当GC 确定一些对象为"不可达"时，GC 就有责任回收这些内存空间。可以。程序员可以手动执行System.gc()，通知GC 运行，但是Java 语言规范并不保证GC 一定会执行。 

## 39、String s=new String(“xyz”);创建了几个String Object? 【基础】 

答：两个对象，一个是"xyx",一个是指向"xyx"的引用对象s。 

## 40、接口是否可继承接口? 抽象类是否可实现(implements)接口? 抽象类是否可继承实体类(concrete class)? 【基础】 

答：接口可以继承接口。抽象类可以实现(implements)接口，抽象类可继承实体类，但前提是实体类必须有明确的构造函数。 

## 41、Java 的接口和C++的虚类的相同和不同处。【基础】 

答：由于Java 不支持多继承，而有可能某个类或对象要使用分别在几个类或对象里面的方法或属性，现有的单继承机制就不能满足要求。与继承相比，接口有更高的灵活性，因为接口中没有任何实现代码。当一个类实现了接口以后，该类要实现接口里面所有的方法和属性，并且接口里面的属性在默认状态下面都是public static,所有方法默认情况下是public.一个类可以实现多个接口。 

## 42、一个“.java”源文件中是否可以包含多个类（不是内部类）？有什么限制？【基础】 

答：可以；必须只有一个类名与文件名相同。 

## 43、说出一些常用的类，包，接口，请各举5 个。【基础】 

答：常用的类：BufferedReader BufferedWriter FileReader FileWirter String Integer； 

常用的包：java.lang java.awt java.io java.util java.sql； 

常用的接口：Remote List Map Document NodeList 

## 44、Anonymous Inner Class (匿名内部类) 是否可以extends(继承)其它类？是否可以implements(实现)interface(接口)? 【基础】 

答：可以继承其他类或实现其他接口，在swing 编程中常用此方式。 

## 45、内部类可以引用他包含类的成员吗？有没有什么限制？【基础】 

答：一个内部类对象可以访问创建它的外部类对象的内容。 

## 46、java 中实现多态的机制是什么？【基础】 

答：方法的覆盖Overriding 和重载Overloading 是java 多态性的不同表现；覆盖Overriding 是父类与子类之间多态性的一种表现，重载Overloading 是一个类中多态性的一种表现。 

## 47、在java 中一个类被声明为final 类型，表示了什么意思？【基础】 

答：表示该类不能被继承，是顶级类。 

## 48、下面哪些类可以被继承? 【基础】 

1）java.lang.Thread (T) 

2）java.lang.Number (T) 

3）java.lang.Double (F) 

4）java.lang.Math (F) 

5）java.lang.Void (F) 

6）java.lang.Class (F) 

7）java.lang.ClassLoader (T) 

答：1、2、7 可以被继承。 

## 49、指出下面程序的运行结果: 【基础】 

```JAVA
class A{  
static{  
System.out.print("1");  
}  
public A(){  
System.out.print("2");  
}  
}  
class B extends A{  
static{  
System.out.print("a");  
}  
public B(){  
System.out.print("b");  
}  
}  
public class Hello{  
public static void main(String[] ars){  
A ab = new B(); //执行到此处,结果: 1a2b  
ab = new B(); //执行到此处,结果: 1a2b2b  
}  
}  
```

答：输出结果为1a2b2b；类的static 代码段,可以看作是类首次加载(虚拟机加载)执行的代码,而对于类加载,首先要执行其基类的构造,再执行其本身的构造。 

## 50、继承时候类的执行顺序问题,一般都是选择题,问你将会打印出什么?【基础】 
```JAVA 
package test;  
public class FatherClass {  
public FatherClass() {  
System.out.println("FatherClass Create");  
}  
}  
```
```Java
package test;  
import test.FatherClass;  
public class ChildClass extends FatherClass {  
public ChildClass() {  
System.out.println("ChildClass Create");  
}  
public static void main(String[] args) {  
FatherClass fc = new FatherClass();  
ChildClass cc = new ChildClass();  
}  
  
}  
```

答：输出结果为： 

FatherClass Create 

FatherClass Create 

ChildClass Create
