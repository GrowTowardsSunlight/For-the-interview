macos查看所有的javahome路径以及Java版本

```/usr/libexec/java_home -V```


## 目录

* [java的三个版本](#java的三个版本)
* [运行机制](#Java应用程序的运行机制)
* [JVM、JRE和JDK](#JVMJRE和JDK)
* [java下载安装和环境配置](#java下载安装和环境配置)
  * 环境配置
  * 测试jdk是否安装成功
  * JDK目录介绍
  

首要目标是快速建立知识体系，遇到难点不要纠结，以后再回看难点。当体系达到更高层次时，就很简单了。

C语言是贝尔实验室于1972年发明，C++是贝尔实验室于80年代推出的。
java是SUN公司于1995年发明。

java的核心优势是跨平台。Java虚拟机是实现跨平台的核心机制。比如：Java的int永远都是32位。不像C++可能是16，32，可能是根据编译器厂商规定的变化。java将C++的一些内容去掉,比如：头文件，指针运算，结构，联合，操作符重载，虚基类等等。

### java的三个版本:

  JavaSE(Java Standard Edition)：标准版，定位在个人计算机上的应用。这个版本是Java平台的核心，它提供了非常丰富的API来开发一般个人计算机上的应用程序，包括用户界面接口AWT及Swing，网络功能与国际化、图像处理能力以及输入输出支持等。在上世纪90年代末互联网上大放异彩的Applet也属于这个版本。Applet后来为
Flash取代，Flash即将被HTML5取代。

  JavaEE(Java Enterprise Edition)：企业版，定位在服务器端的应用。JavaEE是JavaSE的扩展，增加了用于服务器开发的类库。

  JavaME(Java Micro Edition)：微型版，定位在消费性电子产品的应用上。JavaME包含JavaSE的一部分核心类，也有自己的扩展类。该版本针对资源有
限的电子消费产品的需求精简核心类库，并提供了模块化的架构让不同类型产品能够随时增加支持的能力。

![Image text](https://github.com/GrowTowardsSunlight/java/blob/master/java三百集/img/javaedition.jpg)


### Java应用程序的运行机制

  Java首先利用文本编辑器编写 Java源程序，源文件的后缀名为.java；再利用编译器（javac）将源程序编译成字节码文件，字节码文件的后缀名为.class； 最后利用虚拟机（解释器，java）解释执行。

  java程序没有直接与操作系统挂钩，jvm和底层操作系统进行交互。

![Image text](https://github.com/GrowTowardsSunlight/java/blob/master/java三百集/img/java运行机制.png)

### JVMJRE和JDK

   JVM(Java Virtual Machine)就是一个虚拟的用于执行bytecode字节码的”虚拟计算机”。他也定义了指令集、寄存器集、结构栈、垃圾收集堆、内存区域。JVM负责将Java字节码解释运行，边解释边运行，这样，速度就会受到一定的影响。不同的操作系统有不同的虚拟机。Java 虚拟机机制屏蔽了底层运行平台的差别，实现了“一次编译，随处运行”。

   JRE(Java Runtime Environment)(java运行环境)包含：Java虚拟机、库函数、运行Java应用程序所必须的文件。

   JDK(Java  Development Kit)(Java语言的软件开发工具包)包含：JRE，编译器和调试器等用于程序开发的文件。

   tips:如果只是要运行Java程序，只需要JRE就可以。JRE通常非常小，其中包含了JVM。如果要开发Java程序，就需要安装JDK。


![Image text](https://github.com/GrowTowardsSunlight/java/blob/master/java三百集/img/jvmjrejdk.png)

### java下载安装和环境配置
[下载](https://www.oracle.com/technetwork/java/javase/downloads/index.html)

**环境配置**

1.进入Control Panel\System and Security\System

2.进入高级系统设置——>高级——>环境变量

3.在系统变量中新建变量JAVA_HOME，变量值为jdk所在路径。([注](https://www.sxt.cn/Java_jQuery_in_action/environment_variable_configuration.html "C:\Program Files\Java\jdk1.8.0_191"))

4.在系统变量的Path变量中新建一个值%JAVA_HOME%\bin。

tips

运行java或者javac都需要找到bin目录。不设置JAVA_HOME而直接在Path变量中新建bin所在路径，java和javac也能够运行。但是一些服务器和软件会主动找JAVA_HOME变量，所以我们必须要设置它。

如果使用JDK1.5以上就不需要配置classpath环境变量(类路径)。JRE会自动搜索当前路径下的类文件及相关jar文件。

**测试jdk是否安装成功**

进入cmd，输入java 或 java -version。

**JDK目录介绍**

bin: 存放一些二进制文件，包括exe文件等。java.exe,javac.exe都在bin目录中。

include：存放头文件

lib: 存放jar包

src：jdk的源代码
