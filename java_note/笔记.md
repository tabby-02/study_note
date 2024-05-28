# 1.数据类型

## 1.简单数据类型

简单类型的变量被声明时，**存储空间也同时被分配**。

<img src="\笔记图片\Snipaste_2023-12-29_19-14-47.png" style="zoom:100%;" />

在整型类型和boolean类型之间不能相互转换

## 2.引用类型

引用类型(数组、class或interface)声明变量时，是**不会为变量(即对象)分配存储空间**。它们声明的变量不是数据本身，而是数据的引用(reference)，需用**new运算符**来为引用类型的变量**分配贮存空间**；

### 数组

1.初始化    int[] a = new int[3];     int[] a = {1,2,3};

2.java没有提供多维数组。它是通过创建数组的数组(和数组的数组的数组)。（**嵌套**）

3.必须首先将**低位维初始化**，再能对它后面的各位依次初始化。
利用对每维元素的分步初始化，可以创建**非矩形数组**的数组

# 

# 2.方法调用时参数传递

形式参数是简单类型
不会影响到实际参数引用中变量的值
形式参数是引用类型
会影响到实际参数引用中变量的值

# 3.过载，重载（覆盖）

**过载**：在<u>同一个类</u>中**同名不同参**方法。
参数不同：
	数量不同；
	数量相同，但是对应的类型不同；
	顺序不同

**重载(覆盖)**：<u>子类和父类</u>**同名同参**同返回类型方法(被覆盖的方法可以通过<u>***(1)super***</u>调用)

# 4.构造器

构造方法的**也可以方法过载**。一个类可以有多个构造方法；
构造方法之间通过**this()**形式**相互调用**。（this()必须在第一个//super()后）

# 5.继承

1.子类继承超类的所有成员；（private也包括，只是不能使用，可以通过**<u>*(2)super*</u>**访问被隐藏的）
2.子类**不能继承**超类的**构造器**，只能在构造器中**通过<u>*(3)super()*</u>调用**超类的构造器；（super()必须在第一个//this()前）

# 6.抽象类和接口

1.abstract方法是没有语句实现部分，直接由;结束。

2.有下面三种方法不能作为抽象方法定义：构造方法，类方法，**私有方法**

| 抽象类                                                       | 接口                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **abstract方法必须是在abstract类中**，abstract类中也**可以有非abstract方法** | 接口中的所有方法**都是abstract方法**                         |
| 抽象类中可以有一般的成员变量                                 | 在接口中定义的**成员变量都是常量**，具有**pubilc，final和static**属性，在创建这些变量时可以省略这些修饰符。 |
| 可以有构造函数                                               | **没有构造函数**                                             |
| 所有抽象方法必须被继承类重写                                 | 所有抽象方法必须被继承类重写                                 |
| 任何继承该抽象类的类的**实例**都**可以存储在**该**抽象类**的变量中 | 任何实现该接口的类的**实例**都**可以存储在**该**接口**类型的变量中 |
| abstract class A{  }                                         | interface A{  }                                              |
| class a extends A{  }                                        | class a implements A{  }                                     |



# 8.访问控制

<img src="\笔记图片\Snipaste_2023-12-29_19-41-34.png" style="zoom:100%;" />

# 9.异常

<img src="\笔记图片\Snipaste_2023-12-29_19-57-11.png" style="zoom:100%;" />

## 1.try-catch

try {
  try {
  }
  catch(异常类1 异常变量) {     ///只有这个catch有效(只匹配第一个，只匹配内层)
  }
  catch(异常类2 异常变量) {
  }
}
catch(异常类3 异常变量) {
}
catch(异常类4 异常变量) {
}
finally {
}

## 2.throw,throws

1.<u>**throw**</u> 异常对象

2.<返回类型> <方法名>(参数列表) <u>**throws**</u> 异常类1,...



## 3.自定义异常类

class XX <u>**extends Throwable**</u>{
XX() {<u>**throw**</u> ...}
}

# 10.线程

## 1.使用方法

### 法一：生成Thread子类

步骤：

class MyThread <u>***extends Thread***</u>{      public void <u>***run()***</u>{·········}     }
MyThread thread = <u>***new***</u> MyThread();            thread<u>***.start()***</u>;

### 法二：生成一个类，实现Runnable接口

class NewThreadRun <u>***implements Runnable***</u>{      public void <u>***run()***</u>{········}     }
NewThreadRun n=**<u>*new*</u>** NewThreadRun();        thread**<u>*.start()*</u>**;

## 2.优先级

1.优先级划分为10级，用1至10的整数表示

2.三个优先级常量：(1)MIN_PRIORITY,(10)MAX_PRIORITY和(5)NORM_PRIORITY

3.没有为线程分配优先级，则Java系统为其赋值为NORM_PRIORITY

4.Thread类的**setPriority(int a)**方法来修改系统自动设置的线程优先级。

5.出现一个高优先级线程，那么低优先级线程就只能停止执行，放弃CPU，推回到**等待队列**中。具有相同的优先级，则按“先来先服务”的原则调度

<img src="\笔记图片\Snipaste_2023-12-29_15-41-38.png" style="zoom:80%;" />

start()：用于调用run()方法使线程开始执行。
stop()：立即停止线程执行，其内部状态清零，放弃占用资源。
wait()：使线程处于等待状态。线程等待某个条件调用wait()方法。
notify()：使线程脱离阻塞状态。在条件变量所在的对象中调用
notify()方法即可使线程脱离阻塞状态。
sleep()：调整线程执行时间，参数指定睡眠时间。
**yield()**：暂停调度线程并将其放在等待队列末尾，等待下一轮执行，使同优先级的其它线程有机会执行。

## 3.线程同步

### 1.synchronized

1.使用修饰符**synchronized**来为被保护资源加锁。

2.synchronized只能用来说明**方法和代码段**，<u>不能</u>用它来说明<u>类和成员变量</u>。

3.用synchronized修饰的方法和代码段称为方法同步和代码段同步，它意味着**同一时刻**该方法或代码段**只能被一个线程执行**，其它想执行该方法或代码段的线程必须等待



### 2.wait方法和notify方法

通常可以用notify()或notifyAll()方法**唤醒**其它一个或所有线程。

使用wait()方法来使该线程处于**阻塞**状态，等待其它的线程用notify()唤醒

# 11.输入输出流

## 1.流

字节流：处理二进制数据的流，每次处理**一个字节**的数据，以Stream结尾

字符流：处理某种格式的特定数据，每次处理**一个字符**的数据，以Reader Writer结尾

节点流：直接**从指定的位置**（如磁盘文件或内存区域）读或写。其它的流则称为过滤器。

过滤器：输入流往往是以**其它输入流作为它的输入源**，经过过滤或处理后再以新的输入流的形式提供给用户，过滤器输出流的原理也类似。

## 2.字节流

<img src="\笔记图片\Snipaste_2023-12-29_17-18-12.png" style="zoom:150%;" />

### 1.字节流顶层抽象类InputStream,OutputStream

InputStream类提供了有关读入数据的三个读入方法：
int read()
 方法返回一个0至255之间的整数或-1, -1代表遇到了流的结束，其它对应读入的字节。
int read(byte[])
 方法则将字节读入参数给定的字节数组，返回值是实际读入的字节数或- 1(遇到了流结束)。
int read(byte[],int,int)
 方法的后两个参数分别给出读入的起始位置和读入的最大字节数

### 2.下层子类

**所有InputStream的子类都是针对不同的输入数据源，**输出源要和输入源对应

### 3.下层节点流 FileInputStream,FileOutputStream

FileInputStream类的构造器有：（in/out针对的是java，**in->读文件,out->写文件**）
	 FileInputStream(String)    参数String对象表示文件名。
 	FileInputStream(File)      参数File对象表示文件名
FileOutputStream类的构造器有：
 	FileOutputStream(String)
	 FileOutputStream(String,boolean)   boolean参数为false，原文件数据被丢弃，然后再输出数据，boolean参数为true，															在原文件末尾追加输出数据，原文件数据仍然存在（**boolean->是否保留原数据**）
 	FileOutputStream(File)

### 4.下层过滤器流 BufferedInputStream,BufferedOutputStream

增加输入输出**缓冲机制**，从而显著地**提高**输入输出的**速度**

### 5.下层过滤器类 DataInputStream,DataOutputStream

允许程序按与**机器无关**的风格读写Java数据

## 3.字符流

<img src="\笔记图片\Snipaste_2023-12-29_17-42-21.png" style="zoom:150%;" />

String buffer;

FileReader fr = new **FileReader**(new File(args[0]));
bRead = new **BufferedReader**(fr);
buffer = bRead.readLine();

FileWriter fw = new FileWriter(new File(args[2]));
bWrite = new BufferedWriter(fw);
bWrite.write(buffer);