

# JAVA学习笔记：

# ==今日长缨在手，何时缚住苍龙？==

# ==追风赶月莫停留,平芜尽处是春山。==

## 	24/8/1

IDEA:

![image-20240806191158099](image-20240806191158099.png)

###  				



java内存图：

![image-20240806192257233](image-20240806192257233.png)



###  				第一章：Java的基本程序设计结构	

#### java基础知识

jvm(JAVA虚拟机)：java程序运行的假想计算机，用来运行java程序

JDK和JRE:

​		jdk:java开发工具包：包含（javac(编译工具)、java(运行工具)、jre

​		jre:java运行环境

#### 注释:

 1.单行注释//

2.文档注释/**

*/

3.多行注释 /*

​    */

注意：==多行注释中不能嵌套多行注释==



#### 一个简单的java程序：用于输出hello world

```
public calss Main{
	public static void main(String [] args){
		System.out.println("Hello World")
	}
}
```



程序分析：

1.==java区分大小写，错误将无法运行程序==

2.public为访问修饰符，用于控制程序的其他部分对这块代码的访问级别

3.关键字class后紧跟类名==（类名规则：必须以字母开头，长度没有限制，不可以使用保留字。）==

4.==源文件代码名必须与公共类名相同。注意大小写。==

5.java虚拟机总是从main方法开始执行，==（java中的方法为c++中的函数），main方法必须设置为public==

6.==原代码中的{}为代码块，java中任何方法的代码都必须在{}中==

7.==main必须设置静态static==

8.==每个语句必须用;结尾==

9.==点号代表调用方法（函数),如object.method(parameters)==



#### java数据类型：==（java中，必须为每一个变量声明一个类型）==

##### 整形：四种整形变量

1.int型

2.long型

3.short型

4.byte型

注：

3和4用于特定的应用场合，如底层文件处理或者大数组

==整型的范围与运行java代码的机器无关==

##### 浮点型：两种

1.float

2.double

注：

double类型的数值精度是float的两倍，被称为双精度数

==大部分情况不使用float==

##### 字符型：

char

单引号引起来

##### 布尔型：

boolean

用于逻辑判断:false和true

==在java中，布尔型和数值型不可相互转换==



#### java中的变量与常量



##### 变量：

声明变量：type+name (和c++一样)

​		如下

​		int a; 

​		double b;

​		char c;

变量名：==开头不能是数字，不得有空格==

可以一行声明多个变量： int i,j;

==声明一个变量后必须进行初始化，否则报错==

int a; a=3;  或 int a=3;

==对于局部变量，不声明类型也可以自动获取类型。如a=3,a被自动识别为Int==



##### 常量：

关键字final指示常量

==常量只能被赋值一次，一旦赋值，不能更改。习惯上，常量名全部大写==

==java中经常使用一个常量在一个类的多个方法中使用，可以使用static final设置一个类常量，类常量定义位于main之外==



##### 枚举类型：

有时候，一个变量只包含一个有限的值，可以自定义枚举类型

enum指示枚举类型

​		如：

​		enum Size(small,medium,large,extra_large);

​		就可以用Size定义一个限制值的变量了

​		Size s=Size.medium;



# 8/2

#### 运算符：



##### 8/6新加内容 位运算：

​							左移动几位，就相当于乘2的几次方

​											==2<<2 结果为 2乘2的2次方 为8==

​								右移动，除以2的几次方，不能整除向下取整

​												==9>>2   结果为 9除2的2次方 为2==

##### 1.算术运算符：

加+减-乘*除/

==两个操作数都是整数为整除==

取模%

==整数除0提示错误，浮点数除0得到无穷大或者NaN结果==



##### 2.数字函数与常量 math**类中包含了你可能用的各种数学函数**

​         平方根 sqrt   如double x=4; double y ===Math.sqrt(x)==

​		  幂函数pow  如:double y===Math.pow(x,a)== ,x的a次幂

​     	math.sin cos tan atan exp log log PI E



##### ==不必在数学方法名和常量名前加前缀Math，只要在源文件最上面加：import static  java.lang.Math.*;==

#### 

##### 3.数值类型之间的转换



![image-20240802212333428](image-20240802212333428.png)

​      																		（==虚线表示可能有精度损失==）

当两个值进行计算时，会先将两个操作数转换为同一类型，然后进行计算



##### 4.强制类型转换

在要转换的值前加（）

如：

​     double x=9.997

​     int n===(int)x==

直接强制截断小数位

若想四舍五入可使用round方法如：

​      int n=(int)Math.round(x)

### ==不要将boolean类型和任何数值类型之间进行强制类型转换==



##### 5.布尔运算符

== 等于  ！=不等于 &&并且 ||或者

第二种：condition ?expression 1:expression2

​          成立执行expression1 否则执行expression 2



##### 6.==switch表达式==

​	需要在两个以上的值中做出选择时，可以使用switch表达式，如下

​						

```
		String seasonName=switch(seasonCode){
				case 0 -> "spring";
				case 1 -> "summer"
				case 2 -> "fall"
				case 3 -> "winter"
				default -> "sb"
		}
```

​				

可以给case提供多个标签 如：

```
int nunLetters=switch(seasonName)
{
		case "Spring","Summer","Winter" -> 6;
		case "Fall" -> 4
		default ->-1;
}
```



#### 7.==字符串==：java字符串就是unicode字符序列（字符串为String类）

​           如：

​						String e="";

​						String g="Hello World";

##### 7.1子串

​		String的substring方法可以从一个较大的字符串中提出一个子串如：

​						String a="Hello";

​						String s=a.substring(0,3);

​						s的值为"Hel"

#####    7.2拼接

​			java允许使用+号连接两个字符串

​       	==当一个字符串与一个非字符串拼接时，后者会自动换为字符串，如何对象都能换为字符串==

​     

​	 	 ==多个字符串放在一起，某个定界符分开，可以使用join方法==，如：

​                               String s=String.join("/","S","S","C");

​					结果为S/S/C

​             

​			==repeat可以重复生产字符串，如:==

​										String s="java".repeat(3)

​								结果为javajavajava



#####   ==7.3字符串不可变==

​            ==String类中没有任何一个方法可以修改字符串的内容==

   如果想修改，可以先截取，再拼接



##### 7.4检测是否相等

​    可以使用equals方法

​			如s.equals(t)，可以检测s和t是否相同

###       ==切记不要使用====比较字符串是否相等，否则可能出现意外的结果



##### 7.5空串与Null串



空串时长度为0的字符串，可以使用下面的方法查看一个字符串是否为空：

​      if(str.length()==0)   或者 if(str.equals(""))



null代表一个字符串没有和任何对象关联

​     if(str!==null)



##### ==7.6构造字符串==

​      多个短小按键输入字符串或者文件单词多次拼接影响效率和空间，可以使用StringBuilder类

  如果需要多个小字符串构造字符串，可以采用以下方法：

```java
首先构造一个空的字符串构造器：
StringBuilder builder=new StringBuilder();
当每次需要添加其他部分时，可以调用append方法：
builder.append(ch);
builder.apped(str);
构造完成后，最后使用toString方法，得到一个String对象，其中包含了所有添加的字符串
String a=builder.toString();
```



7.7字符串块

以"""开头 以“”“结尾

如： string a=""" helloasdfkjl

sadfasdf

asdf

sadf

"""



# 8/3



#### 输入与输出



##### 输入：

第一步：构造一个与“标准输入流”System.in关联的Scanner对象

​				Scanner a = New Scanner(System.in)

​				构建了一个a对象

 第二步：现在就可以读取输入了：

​				==使用nextLine读取一行==

​						String name = a.nextLine()

​				==使用next读取一个单词==(空格分开)

​						String name=a.next();

​				==使用nextInt读取整数==

​						int name=a.nextInt()

​				==使用nextDouble读取下一个浮点数==

​	                  double name=a.nextDouble()

最后，在程序的最前面加上：import java.util.*;



##### 格式化输出：

​			可以用System.out.print(x)将数值x输出到控制台

​			==格式化输出利用printf方法实现，沿用了c语言函数库中的古老约定。 如System.out.printf("%d",a)==

​				C 语言和 Java 的格式说明符大部分是相同的，但 Java 有一些额外的特性。例如，Java 支持 `%b` 来格式化布尔值，支持 `%t` 来格式化日期和时间。



如果想要读取一个文件的内容，可以使用Scanner a =new Scanner(Path of("路径")，StandardCharsets,UTF_8);



#### 三种基本结构：

##### 控制流程：

##### 1.块作用域

##### 	块内包含若干程序语句，由一对大括号括起来，一个块可以嵌套在另一个块中，==但是不能再嵌套的两个块中声明同名的变量。==



##### 2.条件语句：

在java中，条件语句为：if（condition)statement

```java
if(a>b){
a=a+1;
}
else
{
a=a-1;
}
```



##### 3.循环：



##### 3.1while循环

while(condition)statement



while(/////){





}



##### 3.2do while循环

do{

}while(condition);



##### 3.3for循环

for(int i=1;i<=10;i++)

{

}

==切记，谨慎将浮点数作为计时器，可能导致无限循环==



##### 4.多重选择（switch语句）

```
switch(a){
case 1 -> 
   .....
case 2 ->
  .....
default ->
 ......
}

==不需要在每个case中写break;==
```



也可以使用c语言相同的格式，需要写break;



##### 5.中断流程的语句

标签：

break;

continue;

break:标签；



## 8/4



##### 大数

如果基本的整数和浮点数精度不足以满足需求，那么可以使用java.math包的两个类BigInteger 和BigDecimal他们可以处理任意长度序列的数值，BigInteger整数运算，BigDecimal浮点数计算



不能使用人们熟悉的算术运算符来组合大数，需要使用add和multiply方法

例如：

​		sum_result = num1.add(num2)

​		 product_result = num1.multiply(num2)



#### Random随机数：

第一步：导入包：import java.util.Random

第二步：创建对象：Random x = new Random()

第三步：x.nextInt() 随机生成一个int范围内的数

   如：

```
import java.util.Random
Random x=new Random()
int b=x.nextInt()
```

##### ==若想范围内生产随机数，在nextInt中（）填写系数，表示0到这个数，如想生成1-10 nextInt(10)+1==



### ==数组：==

##### 1.声明数组

在声明数组时，需要指出数组类型，元素后紧跟[]和变量名，如

## 									int [] a;或者int a[];  （优先前者）

但是这句话只是声明了a，并没有初始化为一个正在的数组，==应该使用new 初建数组==

###  								==int []a=new int[100]==

#### ==一旦创建数组，就不能修改它的长度==

#### ==数组长度可以是变量如： new int[n]    //n为变量==



简便方法：int []a={1,2,3,4,5} 无需使用new甚至不需要指定长度



可以构建长度为0的数组：new a[]o 或者new a[]{}





##### 2.访问数组元素

与c语言相同

==获取数组元素个数使用a.length()==



##### 3.for each循环

for each循环是一个强有力的循环结构，可以用来处理数组或其他任何元素集合中的每个元素，而不必考虑索引值。

​						for(variable:collection){

.........................................................

}

variable为定变量，循环中为每个元素的值，collection为数组名  如：

```
for(int e:a){
System.out.println(e);
}  //输出每个元素
```



##### 4.数组拷贝

java中允许一个数组变量复制到另一个数组中，这是两个变量将引用同一个数组：

​												int[] a=b;  //b为已知数组

### ==改变一个变量所指向的数组内容，另一个变量也会反映出这些改变。==



如果希望复制值而不是地址，可以使用arrays类的copyOf方法：

​								int[] a=Arrays.copyOf(b,lengths)

第二个参数为数组a的长度



##### 5.数组排序

如果想对数值型数组进行排序，可以使用Arrays类中的sort方法：

​					Array.sort(a);

这个方法使用了优化的快速排序



##### 6.多维数组

使用多个索引访问数组元素。 后面学习 跳过





### 方法：（函数）

==方法之间不嵌套==

定义：

修饰符 返回值类型 方法名（参数）{

​			代码块	

​		return 结果

}



#### ==方法的重载：方法名相同，参数不同（个数、类型、类型顺序），可以进入不同的方法==

##### 				重载和返回值无关，和方法名无关





# 8/6

## 对象和类

## ==面向对象编程三个核心思想：封装，继承，多态==



### 类（class)：类指定了如何构造对象。可以将类比作制作蛋糕的磨具，对象比作蛋糕。



类的分类：

### ==1.测试类：带main方法的类，运行代码==

### ==2.实体类：是一类事物的表示形式（世界万物）==



类的组成：

1.属性(变量)

定义位置：类中方法外 

作用范围：作用于当前类

定义类型：数据类型 初始化 

默认值（无需初始化）：

​					整数：0

​					小数：0.0

​					字符:'\u0000'

​					布尔：false

​					引用：null

2行为（成员方法）：这一类事物能干什么

和普通方法一样（==去掉static==)



 由一个类构造对象的过程称为创建这个类的一个实例。

 用JAVA编写的所有代码都在某个类中。

如果类名包含static，调用不需要new，直接使用



#### 对象：一类事物的具体体现（即把抽象的类化为具体）



### 对象的使用：

##### 1.导入：import 包名.类名 （如果两个类在一个包内，则不需要导包） 

##### 2.创建：想使用哪个类中的成员，就new哪个类的对象

格式：类名 自定义名 = new 类名()

##### 3.调用使用 （成员变量、成员方法）

  对象名加.



##### 匿名对象：

```
int i=10
int是数据类型
i 是变量名
10是真正的数据

Person p=New Person()
Person是数据类型
p是变量名
New Person()真的数据
```

匿名对象是指没有左边的内容 直接New 对象.成员

##### ==如果只想简便使用方法可以使用匿名对象，如果赋值切记不要用==



### ==成员变量与局部变量==：

1.定义位置不同：

成员变量：类中方法外

局部变量：方法中或参数位置

2.初始化值不同：

成员变量：有默认值，不需手动赋值，可以直接使用

局部变量：无默认值，必须赋值

3.作用范围不同：

成员变量：整个类中

局部变量：自己所在的方法，其他方法无法使用

4.内存位置不同（了解）：

成员变量：在堆中，跟着变量走

局部变量：在栈中

5.生命周期不同（了解）：

成员变量：随着对象的创建的产生而产生，对象的消逝而消逝

局部变量：随着方法的调用而产生，随着方法调用完毕而消逝



==如果成员变量和局部变量重名，采用就近原则，先访问就近变量==



## ==封装（信息隐藏）：是处理对象的一个重要概念。==

封装就是将数据和行为组合在一个包中，对对象的使用者隐藏具体的实现细节。

代码放到方法中，或一个成员被private修饰都是封装的表现

关键字private:被private的只能在本类中使用，别的类无法使用



#### 如何使用：

修饰成员变量：private 数据类型 变量名

修饰方法：将public换为private



属性被private私有化了，外界无法直接调用，所以需要使用公共接口get/set方法（在类中新建两个方法叫get/set)

set：为属性赋值

get：获取属性值



this的使用：

1.如果成员变量和局部变量重名，采用就近原则，先访问就近变量

this关键字表示当前变量

##### 作用：区分重名的成员变量和局部变量

##### ==this.的一定是成员变量==

哪个对象调用的this所在的方法，this就代表哪个对象





#### 构造方法：方法名和类名一致，切能初始化对象的方法

#### 分类：

有参构造和无参构造

#### 特点：

1.方法和类名一致

2.没有返回值

#### 格式：

##### 1.无参构造：

public 类名（）{

}

用于new对象

特点：每个类都默认有一个

##### 2.有参构造

public 类名（形参）{

}

用于New对象或为属性赋值

##### 继承：通过扩展一个类得到一个新类



### JAVAbean：java编写类的一种规范

要求：==1.类必须是具体的公共的，public class 类名==

​            2.==必须有无参构造和有参构造==

​			3.==成员变量私有化，提供操作成员变量的get和set方法==



扩展 javabeen和数据库的关系：1.表名->类名 2.属性名->类名3->对象->表中每行数据4->表中单元格数据



## static关键字：静态

用于修饰成员变量



##### 格式：

修饰变量： static 数据类型 变量名

修饰方法：修饰符 static 返回值类型 方法名（形参）{

}



#####  调用静态成员：

（特别简单）无需new对象，直接类名使用



##### static特点：

1.静态对象属类对象，不属于对象成员

2.静态对象会随着类的加载而加载

3.静态成员优先于非静态成员存在在内存中

4.==凡是根据静态成员所在的类构建的对象，都可以共享这个静态成员==



##### static修饰成员的访问特点：(思路核心：静态对象会随着类的加载而加载)

1.在静态方法中能直接访问非静态成员吗？

 不能！

2.在非静态方法中能直接访问静态成员吗？

能！

3.在静态方法中能直接访问静态成员吗？

能！

4..在非静态方法中能直接访问非静态成员吗？

能！

==**结论：不管在不在同一个类中，非静态成员都可以使用New对象调用，静态成员都可以类名直接调用**==



## 对象数组：类似普通数组

例子：

```java
Person p[=new Person[2]; 
person p1=new Person("liming",12)
person p2=new Person("wangna",19)
p[0]=p1;
p[1]=p2
此时p[0]就是p1
p[1]就是p2
```



## 方法参数：

#### 基本数据类型和引用数据类型的区别：

基本数据类型有：四个整形，两个浮点型，字符型，布尔型

其他的都是引用数据类型

### *==基本数据类型传递的是值，不是变量本身。==*

### *==引用数据类型传递的是地址，双方同时改变==*







## 可变参数：只明确了参数的数据类型，不明确参数的个数

#### ==格式：数据类型...变量名（必须是三个点）==



注意：

1.可变参数的本质是一个数组

2.不能连续使用多个可变参数

3.可变参数和普通参数在一起时，需放在最后



##### 类之间的关系：

![image-20240806184343077](image-20240806184343077.png)

依赖（uses-a)：如果一个类的方法要使用或操作另一个类的对象，我们说前一个类依赖于后一个类



聚合（has-a)：即整体对象包含部分对象，如Order对象中包含Item对象



继承（is-a)：个类可以继承另一个类的属性和方法,形成父类和子类的关系。





# ==继承：==父类和子类（实质上是一种设计代码的思想理念）

##### 1.父类：我们定义了多个类，发现这些类中有很多重复性的代码，我们定义 一个父类，将相同的代码抽取出来，其他类直接继承这个类，就可以直接继承这个父类，直接使用父类中的内容。



##### 2.怎么继承：

关键字extends

子类extends 父类



##### 注意：

###### 1.子类==可以继承父类中的私有和非私有成员==，但是==不能使用父类中私有成员==！（有继承权，不能使用私有）

2.构造方法不能继承



#### ==继承怎么学：==

==继承不要从是否"拥有"方面来学习，要从是否能“使用”方法来学习==



#### 如何使用：

1.定义一个父类，在其中定义重复的代码

2.定义一个子类继承父类 ->extends(关键字)

 					子类 extends 父类

3.创建子类对象，直接使用父类中非私有成员

```
假设父类已经定义为fulei
public class Manager extends fulei{

}
```



### ==继承中的对象访问特点==

#### 1.子类父类对象不重名的情况

![image-20240813204743529](image-20240813204743529.png)

总结：==看等号，左边是谁，先调用谁中的成员==

##### 				如果等号左边是父类类型，==只能==调用父类中的成员变量。如果等号左边是子类类型，既能调用子类对象，也能调用父类继承过来的对象



#### 2.子类父类对象重名的情况

## 总结：重名时==看等号，左边是谁，先调用谁中的成员==



#### ==继承方法的调用情况：==

看new 的是谁，就是谁的方法，子类没有找父类



# ==上面继承所有的访问特点全部用于多态==





### 方法的重写：

概述：如果子类中有一个和父类方法名以及参数列表相同的方法，它就是重写的方法



==前提：继承==



访问特点：看new的是谁 先调用谁中的



#### 判断是否为重写方法：==在方法上写一个@Override(注解)==



注意事项：1.子类重写父类方法之后，权限==必须要保证大于等于父类权限==（权限指的是访问权限）

​									public>protected>默认>private

​					2.子类方法重写父类方法，方法名和参数类型要一样

​					3.==私有方法不能被重写，构造方法不能被重写，静态方法不能被重写==

​                    4.子类重写父类方法之后，返回值类型应该是父类方法返回值类型的子类类型

​				



方法重写的使用场景：某个功能的升级改造，子类需要对父类以及实现好的功能进行重新改造



继承中构造方法的特点：

在new子类对象时，会先初始化父类（先走父类无参构造方法）



==原因：每个构造方法里面的第一行，默认都会有一个super()，不写jvm自动提供一个==

​						super()代表父类无参构造方法

​										

### super和this



### super的具体使用：super()代表父类引用

1.作用：可以在子类中调用父类中的成员

​          1.调用父类构造方法->

​							==必须在子类的构造方法中写==super()或super(参数)

​		  2.调用父类成员变量

​									super.成员变量名

​		  3.调用父类成员方法

​									super.成员方法名（）





### this的具体使用:代表当前对象（哪个对象调用的this所在的方法，this就代表哪个对象）

1.作用：

​      a.区分重名的成员变量和局部变量

​      b.调用当前对象中的成员



2.如何使用

​     a.调用当前对象的构造：在构造中写this()或this(参数)

​     b.调用当前对象的成员变量

​								this.成员变量

​	 c:调用当前对象的成员方法:
 								this.成员方法



## 继承的特点：

1.只能单继承，不能多继承（一个儿子不能多个爹）

2.支持多层继承

3.一个父类可以有多个子类

4.构造方法不能继承，也不能重写

​    私有方法可以继承，但是不能重写

​    静态方法可以继承，不能被重写



#### 为父类私有属性赋值:使用get或set方法



# 抽象：

1.抽象类：抽取共性方法，放在父类中，没办法确定具体实现，因为每个子类对此方法的实现细节不同，此时可以定义为抽象方法

抽象方法所在的类一定是抽象类



2.如何定义抽象方法：关键字abstract

修饰符 abstract 返回值类型 方法名（参数）：



3.定义抽象类：public abstract classs 类名{}



注意：1.抽象方法所在的类一定是抽象类

​            2.抽象类中不一定有抽象方法

​			3.子类继承抽象父类时，需要重写父类中所有的抽象方法，不然编译报错

​             4.抽象类不能new对象，只能通过new子类对象，调用重写的方法

​		

总结：可以把抽象类看成一类事物的标准，要求只要是属于这一类的，都必须要拥有抽象类中的方法， 必须要实现。怎么证明拥有了？实现了？->重写



注意事项：

1.不能直接new对象，只能创建非抽象子类的对象

2.抽象类中，不一定有抽象方法，但是抽象方法所在的类一定是抽象类

3.抽象类的子类，必须重写父类中的所有抽象方法，否则编译报错，除非该子类也是抽象类

4.抽象类中可以有成员变量，构造，成员方法

5.抽象类中虽然有构造方法，但是不用于New对象，用于子类创建对象时，初始化父类属性使用的



# 接口和多态

### 接口：是一个引用数据类型，是一种标准，规则。



##### 1.如何定义：关键字:==interface==

​		public interface 接口名{}

##### 2.如何实现：关键字：==implements==(实现类)

​              实现类 implements 接口名{}

##### 3.接口中可以定义的成员：

​		a. ==jdk7之前==:

​				1.抽象方法：public abstract->即使不写public abstract默认也带，写上更好

​				2.成员变量：public static final 数据类型 变量名=值 ->即使不写public static final,默认也有

​								==final是最终的，被final修饰的变量不能二次赋值，所以final复制的是常量==

​		b：==jdk8==:

​				1.默认方法:public default 返回值类型 方法名(形参){}

​				2 静态方法:public static 返回值类型  方法名(形参){}

 

​		c:==jdk9及以后==:

​				1.私有方法：private的方法(用的不多)



## ==具体使用方法：==

1.定义接口：

public interface 接口名{}

2：实现：

public class 实现类类名 implements 接口名{}

3.使用:

a.实现类实现接口

b.重写接口中的抽象方法

c.创建实现类对象(接口不能直接new对象)

d.调用重写的方法



## 接口中的成员：

##### 1.1抽象方法：

  定义格式public abstract 返回值类型 方法名（）；

1.2注意：

 不写public abstract默认也有

1.3使用：

​		a.定义实现类，实现接口

​		b.重写抽象方法

​      	  c.创建实现类对象，调用重写的方法



##### 2.1默认方法：

 定义格式public default 返回值类型 方法名(){
方法体

reutrn;

}

2.2使用：

​     	a .定义实现类，实现接口 

​	     b.默认方法可重写，可不重写

​    	 c.创建实现类对象，调用默认方法



##### 3.1静态方法：

 定义格式：public static 返回值类型 方法名(){

方法体

return ;

}

3.2使用：接口名直接调用



### ==默认方法和静态方法的实际作用：可以作为临时加的一个小功能来使用==



4.1成员变量：

格式：public static final 数据类型 变量名=值

相关知识点：final代表最终的，被他修饰的变量不能二次赋值，可以视为常量

特点：==不写public static final 默认也有==

使用：接口名直接调用

### ==必须赋值初始化==

注意：

1.被static final修饰的变量需要手动赋值

2.习惯上将static final修饰的变量名大写





### 接口的特点：

1.接口可以多继承->一个接口可以继承多个接口

​      public interface InterfaceA extends InterfaceB,InterfaceC{}

2.接口可以多实现->一个实现类可以实现一个或者多个接口

  public class InterfaceImpl Implements InterfanceA,InterfaceB{}

3.一个子类可以继承一个父类的同时实现一个或者多个接口

  public class Zi extends Fu implements InterfaceA,InterfaceB{}

4.继承和实现接口只要是父类中的抽象方法，子类或者实现类都要重写



当一个类实现多个接口时，如果接口中抽象方法重写且参数一致的，而且只需要重写一次

当一个类实现多个接口时，如果默认方法有重名的且参数一样的，必须重写一次



## 接口和抽象类的区别： 

##### 相同点：

a.都位于继承体系的顶端，用于被其他类实现或者继承

b.都不能new

c.都包含抽象方法，其子类或者实现类都必须重写这些方法



##### 不同点：

a.抽象类：一般作为父类使用，可以有成员变量，构造，成员方法，抽象方法等

b接口：成员单一，一般抽取接口，抽取的都是方法，视为功能的大集合

c抽象类不能多继承，但是接口可以





# 多态：

怎么学：

​	   a.不要从字面含义上理解多态，要从形式上

​           b.要知道多态的好处

​	    c.多态的前提



前提：

 	 1.必须有子父类继承或者接口实现关系

​	  2.必须有有方法的重写（没有重写，多态没有意义），多态主要就是重写方法

  	3.new对象:父类引用指向子类对象

​				==Fu fu=new Zi() 等号左右不一样==

·				大类型接受了一个小类型的数据->如double b=10



注意：

​	多态不能直接调用子类特有功能

 	



### 多态条件下的成员访问特点

和继承相同：看等号，左边是谁，先调用谁中的成员。看new 的是谁，就是谁的方法，子类没有找父类



## 多态的好处（为什么用多态）

1.问题描述

如果使用原始方法new对象（等号左右两边一样），既能调用重写的，还能调用继承的，还能调用自己特有的成员

但是多态方式new对象，只能调用重写的，不能直接调用子类特有的成员，为什么还要用多态？



2.多态方式和原始方式new对象的优缺点

  	原始方式：

​			a.优点：既能调用重写的，还能调用父类非私有的，还能调用自己特有的

​			b缺点：拓展性差

​	多态方式：扩展性强





# 多态的转型：

### 1.向上转型：

​	父类引用指向子类对象

​		表现方式：double b=1

### 2.向下转型：

​	将大类型强制转换为小类型

​		表现方式：子类类型 对象名2=（子类类型）对象名1 int i=（int)b

#### 	==想要调用子类特有功能，就需要向下转型==

![image-20240820223747024](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20240820223747024.png)



### 转型中可能出现的问题：

1.如果等号左右两边类型不一样，会出现类型转换异常（ClassCastException)

​	如：cat cat1=(cat)Animal

​		但是Animal是传过来的dog

​		此时报错

​	解决方法：向下转型前，先判断类型 使用instanceof

​				对象名 instanceof 类型 会得到一个boolean类型结果

​				

# java面向对象编程的一些杂类：

#### 1.1权限修饰符：

##### 		public:公共的，最高的权限，被它修饰的成员，在哪里都能访问

​		protected:受保护的

​		default:默认的，注意：==不写权限修饰符就是default,不能直接把它写出来==

##### 		private:私有的，只能在自己的类中访问	

##### 	

#### ==1.2不同权限的访问能力==

|                | public | prtocted        | default | private |
| -------------- | ------ | --------------- | ------- | ------- |
| 同类           | yes    | yes             | yes     | yes     |
| 同包不同类     | yes    | yes但是不能修改 | yes     | no      |
| 不同包子父类   | yes    | yes             | no      | no      |
| 不同包非子父类 | yes    | no              | no      | no      |

建议：属性用private-封装思想

​	   成员方法public->便于调用

​	    构造public->便于new



## 2.1final关键字

使用：可以修饰一个类，方法，局部变量，成员变量，对象

#### 2.2final修饰类：

格式：public final class类名{}

​	被他修饰的类不能被继承（==太监类==）

#### 2.3final修饰方法：

格式：修饰符 final 返回值类型 方法名(){
}

 	被它修饰的方法不能被重写

#### 2.4final修饰局部变量：

格式：final 数据类型 变量名=值

​	被它修饰的变量不能二次复制（视为常量）

#### 2.5final修饰成员变量

格式：final 数据类型 变量名=值

​	被它修饰的变量不能二次复制（视为常量）

#### 2.6final修饰对象

格式：final 类型 对象名=new 对象()'

 	被它修饰的对象地址值不能改变，对象中的属性值可以改变



## 3.1代码块

在一个类中直接写{},他就是代码块，如果New这个对象，它会优先于构造方法执行

#### 3.1.2：静态代码块

格式:static {}

特点：new的时候他最优先执行，==不管New几次只执行一次==

###### ==用法：如果想优先初始化一些变量并且只初始化一次，就可以使用静态代码块==



## 4.1内部类：

类中再定义一个类，就是内部类



什么时候使用：当一个类内部，还有一个部分需要完整的结构去描述，而这个内部的完整结构又只为外部事物提供服务，那么整个内部的完成结构最好用内部类

java中允许一个类的定义位于另外一个类内部，前者称为内部类，后者称为外部类



分类：

​	成员内部类（静态，非静态）、

​	局部内部类（）

​	匿名内部类（重点）



##### 4.2.1静态成员内部类

格式：public class A{

​	static class B{

}

}

​	B就是内部静态类

##### 注意：a.可以定义属性，方法，构造等

​	    b.静态内部类可以被final或者abstract修饰，被final修饰不能继承，被abstract修饰不能new

​	    c.静态内部类不能调用外部的非静态成员

​	    d.内部类还可以被四种权限修饰符修饰		



#### 4.2.2调用静态内部类

==外部类.内部类 对象名 =new 外部类（）.内部类（)==



##### 4.3非静态内部类

除了调用方法和静态内部类一样，不加static

4.3.1调用方法：

​	==外部类.内部类 对象名=new 外部类().new内部类()==



### 4.4局部内部类

定义在方法中，代码块中，构造中的内部类

##### 4.4.1接口类型作为方法参数传递和返回：

​	接受和返回的都是实现类，而不是接口

##### 4.4.2抽象类作为方法参数传递和返回

接受和返回的都是其子类对象，而不是抽象类

##### 4.4.3普通类作为方法参数传递和返回

接受和返回的都是其对象，而不是类

##### ==4.4.4局部内部类的实际操作==

![](C:\Users\Administrator\Desktop\java笔记\image-20240823160618206.png)



## ==4.5匿名内部类（重点）==

 所谓的匿名内部类就是没有显式声明出类名的内部类

格式：

```
new 接口/抽象类(){

抽写方法

}.重写的方法()
```





# API文档：

api: application programming interface,应用编程接口，

​		说白了就是定义出来的类以及接口，以及其中的方法等

为了方便查询开发好的接口和类，会对应提供一个文档，这个文档叫做API文档



查询我们要使用的对象，以及方法，就是程序员的字典



# 异常：

代码出现了不正常的现象，在java中，异常都是一个一个的类

![](C:\Users\Administrator\Desktop\java笔记\7507cb0a09c50cb9efd5523a8eb5a1d.png)



#### 创建异常对象：关键字 throw

​			格式：throw new 异常

![](C:\Users\Administrator\Desktop\java笔记\yichgang.png)



## 异常处理的两个方式：

### 1.throws

格式：throws 异常

位置：在方法参数和方法体之间，小括号后面，大括号前面

作用：向上抛异常

==一般不用，不负责任，如果使用和try ...catch连用==



##### 	throws处理多个异常，throws 异常1，异常2



### 2.try...catch

格式:

```java
try:{

可能出现异常的代码

}catch(异常 对象名){

处理异常的代码 ->一般将异常信息保存到日志文件中

}
```



##### 处理多个异常：

```java
try:{

可能出现异常的代码

}catch(异常 对象名){

处理异常的代码 ->一般将异常信息保存到日志文件中

}catch(异常 对象名){

处理异常的代码 ->一般将异常信息保存到日志文件中

}catch(异常 对象名){

处理异常的代码 ->一般将异常信息保存到日志文件中

}catch(异常 对象名){

处理异常的代码 ->一般将异常信息保存到日志文件中

}
```



注意：

如果catch的多个异常之间有子父类继承关系，我们可以直接catch父类异常

​	如果不清楚是否有子父类继承关系，我们可以直接catch Exception

  

### finally关键字：

代表不管是否触发了异常，都会执行的代码块

特殊情况：如果之前执行了system.exit(0)  终止当前正在执行的程序

```java
try:{

可能出现异常的代码

}catch(异常 对象名){

处理异常的代码 ->一般将异常信息保存到日志文件中

}finally{
不管是否有异常，都会执行
}
```



## 抛异常的注意事项：

1.如果父类的方法抛了异常，那么子类重写以后要不要抛？

可抛可不抛

2.如果父类中的方法没有抛异常，那么子类重写以后要不要抛？

不要抛



## 自定义异常：

新建一个类 继承exception(编译时期错误)，或者==继承(RuntimeException运行时期错误)==，一般用黄色这个

就可用新建得类名抛出错误

throw  new 新错误名



### 打印异常信息得三个方法：

Throwable类中的方法：

```java
String toString()//输出异常类型和设置的异常信息



String getMessage()//只输出异常信息



void printStackTrack()//打印异常信息最全


```



# Object类：

#### ==所有类的父类，所有类都会默认继承它==



## 三个方法：

#### 1.toString:返回该对象的字符串表示

注意：a.如果没有重写toString方法，printlin一个对象，会直接调用toString方法，输出一个地址值

​	   b.如果重写过toString方法，将返回对象内容

#### ==总结：如果直接输出对象名不想输出地址值，需要重写toString方法==



#### 2.equals：比较两个对象的==地址值==是否相等

#### ==equals如果针对基本数据类型，比较的是值，如果比较引用数据类型，比较的是地址==



#### 3.clone:克隆方法

可以克隆一个属性值一样的新对象



# String类

#### String代表字符串



#### 特点：a. java程序中所有字符串字面值（如“abc"）都用此类的对象实现，（==凡是但双引号的都是String的对象==）

​	    b. ==字符串是常量，创建后不得更改==

​				String s=”hello"

​				s=s+"world"///会创建一个新的对象		

​	     c. String对象是不可变的，所以可以共享 如图

​			![](C:\Users\Administrator\Desktop\java笔记\sTRINGGONGXIANG.png)

​			

#### String的实现原理

  一个被final修饰的char数组（jdk8之前）

一个被final修饰的byte数组（jdk9以后）





## String的创建：

1.String() 利用无参构造创建    例：String s1=new String()

2.String(String original)利用字符串创建   例：String s2=new String("abc")

3.String(char[] val)利用char数组创建

​			例:char[] a={'a','b','c'};

​			     String s3= new String(a)

4.String(byte[] bytes)通过平台指定的默认字符集解码指定的byte数组，构造一个新的String

##### ==5.String(char[],offset,count) 从数组的第几个索引，读取几个字符，创建字符串==



##### ==6简化模式：String 变量名=""==



## String面试题：

![](C:\Users\Administrator\Desktop\java笔记\strIngbs.png)



## 字符串判断：

![](C:\Users\Administrator\Desktop\java笔记\zifuchuanjiehe.png)



# StringBuilder类：

一个可变的字符串序列，此类提供了一个与StringBuffer兼容的一套API，但是不保证同步（线程同步），（线程不安全，效率高）



#### 作用： 拼接字符串



###### String拼接字符串有缺点，他每次拼接都会产生新的字符串，就会在堆内存中开辟空间，严重占用内存，影响效率。StringBuilder底层自带一个缓冲区（不被final修饰的字符串），接节省内存



#### 特点：

![](C:\Users\Administrator\Desktop\java笔记\buildstringtedian.png)



#### 构造： StringBuild()



常用方法：StringBuilder.append(任意数据类型)  字符串拼接  可以多次append 如 as.append("s").append("c")...

​		    StringBuilder.reverse()  字符串翻转

​		    StringBuilder.toString() 将StringBuilder转为String



# 数学相关类：



## math类

abs() 绝对值

ceil()向上取整

floor 向下取整

round()四舍五入

max(a,b)

min(a,b)

####  ==可以直接使用，不需要new==



## BigInteger类：

有时可能会使用比Long还大的数（称为对象），可以用BigInteger



##### 构造：BigIntrger(参数)



##### 方法

.add 加法

.subtract减法

.multiply乘法

.divide除法a

.intValue 转为int

.longValue 转为long



## BigDecimal类:

### ==java开发不能用float和double直接进行运算，可能精度损失==

## ==BigDecimal用于解决精度损失问题==



#### 构造方法：==BigDecimal() 参数传string类型的数值==



##### 常用方法：

![](C:\Users\Administrator\Desktop\java笔记\bigdouble fangfa.png)

#####   ==注意 如果除不尽会出现从错误，所以使用以下方法解决：==

##### 方法1：老方法

```java
.divide(divisor,scale,BigDecimal.roundingMode)
 		divisor:除号后面的数
 		scale：保留几位小数
 		roundingMode:取舍方式
 						ROUND_UP:向上加1
 						ROUND_DOWN:直接舍去
 						ROUND_MALF_UP:四舍五入
```

##### 方法2：新方法

```
.divide(divisor,scale,Roundmode.roundingMode)//Roundmode是一个枚举

```





# 日期相关类:



### Date类：用于表示特定的时间

### 构造:new date()

无参当前时间，有参指定时间



方法：setTime()

​	    getTime返回时间 毫秒值



### Calendar日历类（抽象类）



##### 方法：calendar getInstance() 获取当前详细信息

```java
Calendar calendar =Calendar.getInstance();
System.out.println(calendar)
```



##### .get(calendar.字段) 获取相应的日历字段

##### .set(calendar.字段，value) 修改字段值

##### .getTime() 转为date类型

##### .add(calendar.字段,加或减) 给字段加或者减



## SimpleDateFormat日期格式化类：

##### 构造:SimpleDateFormat(pattern)

##### ==pattern代表指定的日期格式，字母不能改变，连接符可以改变==

##### ==y年M月d日H时m分s秒==



##### 方法:

##### .format(date) 将Date对象按照指定的格式转为String

##### .parse(string) 再转为Date



## Jdk8出现的新日期类：

### 1.LocalDate类

##### 不可变的日期对象，年月日

##### 方法：

LocalDate now() 创建LocalDate对象

LocalDate of(year,month,day) 创建对象，设置年月日





## 2.LocatDateTime类

不可变的日期对象，和上面一样，但是包含==时分秒==



![](C:\Users\Administrator\Desktop\java笔记\jdk8 riqi lei tianjiaxiugai.png)

![](C:\Users\Administrator\Desktop\java笔记\jdk8日期偏移.png)



## ==Period和Duration类==

### ==Period用于计算日期之间的偏差==

##### 方法：

==先写这个==Period between(LocalDate1,LocalDate2):计算两个日期之间的差值==再选下面的==

.getYears() 相差的年

.getMonts() 相差的月

.getDays() 相差的日



## ==Duration用于计算时间之间的偏差==

##### Duration between(Temporal starInclusive,Temporal endExclusive) 

##### Temporal是一个接口

#####  实现类LocalDate LocalDateTime

##### ==需要传递LocalDateTime==

#### ==........没什么特别的，直接传递对象就行。。。。。==

##### 方法：

1.toDays()相差天数

2.toHours()相差小时

3.tominutes()相差分钟

4.toMillis()相差毫秒



## DateTimeFormatter日期格式化类

![](C:\Users\Administrator\Desktop\java笔记\jdk8新日期类.png)



# System类

系统相关类（工具类）

##### 特点：构造私有，不能利用构造方法new对象

#####  ==方法都是静态的，可以直接调用==



方法：

##### 1.System.currentTimeMillis()返回以毫秒为单位的当前时间，一般用于测效率

##### 2.System.exit()终止当前运行的虚拟机

##### 3.==System.arraycopy(src,srcpos,dest,destpos,lenth) 数组复制,src原数组,srcpos从哪个索引开始,dest目标数组,ldestpos从第几个索引开始粘贴,length复制多少个元素==



# ==Arrays数组工具类：==

##### 特点：

  类名直接调用



##### 方法：

toString() 按照格式打印数组元素

sort() 升序排序

binarySearch(a[],key)二分查找，需要先升序排序

 copyOf(original,newLength) 数组扩容



# 包装类

##### 基本数据类型对应类就是包装类

##### 类名除了int变成了Integer ，char变成了Charactor，其他全部是首字符大写

##### 作用：==让基本类型拥有类的特性，可以使用包装类中的方法来操作数据==



##### 构造方法:现在不推荐使用

包装类名(数据)



### ==装箱：将基本类型转为包装类== ~推荐使用

##### 方法：

静态方法 .ValueOf(数据)



## ==拆箱：将包装类转为基本类型==

##### 方法

.数据类型ValueOf

 如 		int i=a.intValueOf



## 自动拆箱装箱

##### 大部分时间拆箱装箱都是自动的

![](C:\Users\Administrator\Desktop\java笔记\自动拆箱装修.png)



## 疑难面试题包装类

![](C:\Users\Administrator\Desktop\java笔记\包装类疑难杂集.png)

-128-127



## 基本类型和字符串之间的转换

#### 基本转字符串

1.加号之间拼接（最常用）

2.String中的静态方法

​	String s=String.valueOf(int i)



 

#### 字符串转基本

每个包装类中都有一个类似的方法parse...



# ==实际开发中，一般数据都定义为包装类，方便与数据标连接==



# ==多线程：==

### 线程和进程：

##### 进程：在内存在执行的应用程序

##### ==线程：进程中最小的执行单元，负责当前进程中程序的运行，一个进程中至少有一个线程，一个进程中有多少线程就是多线程程序==



##### 使用场景：

1.耗时操作

2.聊天记录

3.后台服务器



##### ==一个线程可以做一个事，我们就可以同时做多件事了，提高了CPU的利用率==



### 并发和并行：

##### 并行：同一个时刻，有多个执行在多个cpu上同时执行（多个人做不同的事）

##### 并发：同一个时刻，多个指令，在一个cpu上交替执行（一个人做多个事）



##### 细节扩展：

##### 1.之前cpu是单核的，在执行多个程序的时候，好像是在同时执行，原因是cpu在多个线程之间做高速切换

##### 2.现在一般是多核多线程cpu,比如2核4线程，那么cpu可以同时运行4个进程，如果多于4个进程，cpu就会切换运行，所以现在依然是并行与并发同时存在。



## CPU调度

##### 1.分时调度

让所有线程轮流获取cpu使用权，平均分配每个cpu的分配时间片

##### 2.抢占式调度

多个线程抢占，哪个线程先抢到，哪个先运行，一般优先级高的先抢到

##### ==JAVA是抢占式调度==



## 主线程：

##### 专门为Main方法服务的通道，就是主线程



# ==如何创建多线程==

##### 第一种方法：继承Thread类

##### 关键字：Thread、



#### 具体：

1.定义一个类，继承Thread

2.重写run方法，在run方法中设置线程任务(具体要执行的代码)

3.创建自定义线程类的对象new

##### 4.==使用Thread中的start方法，不要使用run方法==。jvm会自动调用run方法。



注意：同一个线程对象不能多次调用start方法，如果想再次调用start，需要new一个新的线程对象



## Thread中的方法：

start()开启线程，自动调用方法

run()设置线程任务

getName() 获取线程名字  

setName()给线程设置名字

currentThread()返回当前运行的线程对象，返回的可以在作为参数

sleep(millis)线程睡眠，到时候后自动醒来，继续执行



### 上面都是重要的方法，下面是扩展的方法：

setPriority(int ) 设置线程优先值,默认优先级为5，最小优先级1，最大优先级10

getPriority(int) 获取线程优先级

setDaemon(boolean) 设置守护线程，当非守护线程执行完毕，守护线程就要结束

yield()礼让线程，如果两个线程一起执行，尽量让他们平衡交替执行（效果不明显~）

join()插入线程，插队线程，先执行



## 创建多线程的第二个方法

##### 实现Runnable接口



1.创建一个类，实现Runnable接口

2.重写run方法，设置线程任务，

3.利用Thread类的构造方法，参数是Runnable的实现类

4.调用start方法，jvm自动调用run方法。



## 两种实现多线程的方式区别：

1.Thread继承只能单继承，有局限性

2.实现Runnable接口可以多实现，没有局限性



## 匿名内部类创建多线程 （严格上不属于创建多线程方式之一）

基于实现Runnable接口实现

```java
new Thread({
    @Override
    public void run(){
        System.out.println(Thread.currentThread().getName)
    }
}),start();
```

==线程属于一次性消耗品，在执行完 run() 方法之后线程便会正常结束了，线程结束后便会销毁，不能再次 start，只能重新建立新的线程对象。==

# 线程安全：

### 当多个线程访问同一个资源时，导致了资源出现问题

### 线程安全的三大特性

1、原子性
原子性是指操作是不可分的。其表现在于对于共享变量的某些操作，应该是不可分的，必须连续完成。

比如 a++ 操作，实际上 JVM 会分 3 步来完成。
①读取变量 a 的值
② a 的值+1
③将值赋予变量 a

这三个操作中任何一个操作过程中，a 的值被人篡改，那么都会出现我们不希望出现的结果。所以我们必须保证这是原子性的。

所以想要实现 ++ 这样的原子操作就需要用到 synchronized 或者是 lock 进行加锁处理。

如果是基础类的自增操作可以使用 AtomicInteger 这样的原子类来实现（其本质是利用了 CPU 级别的 的 CAS 指令来完成的）。

JDK 1.8中的原子类


2、可见性
可见性是指一个线程对共享变量的修改，另外一个线程能够立刻看到；

我们在编写Java程序的时候，JVM为了提高程序的执行效率，会对我们的程序进行优化，把经常需要被访问的变量存储在我们的缓存当中，也就是CPU中的寄存器（Cache）里，而避免直接去内存里读。

CPU从内存里读数据，需要通过总线发送指令给内存。

这个速度远远比不上让CPU直接从Cache里面读取数据。

但是在多线程的情况下，某一变量可能已经被别的线程改变了，但是该缓存却无法察觉到内存中的变化，从而造成我们的线程读取的数据跟内存里面的数据是不一致的（脏读）

通过上述描述我们可以知道：由于多核硬件架构的问题，CPU 高速缓存之间本身是不可见的，必须要实现缓存一致性协议。Java方面提供了两个关键字来保证多线程情况下共享变量的可见性方案（volatile、synchronized）。

3、有序性
有序性是指程序在执行的时候，程序的代码执行顺序和语句的顺序是一致的。
那为什么会出现不一致的情况呢？
这是由于重排序的缘故。

在执行程序时，为了提高性能，编译器和处理器常常会对指令做重排序；
重排序不会影响单线程的执行结果，但是在并发情况下，可能会出现诡异的BUG。

举例：

Java 中可以使用 volatile 来保证顺序性，synchronized 和 Lock 也可以来保证有序性，和保证原子性的方式一样，通过同一段时间只能一个线程访问来实现的。

除了通过 volatile 关键字显式的保证顺序之外， JVM 还通过 happen-before 原则来隐式的保证顺序性。其中有一条就是适用于 volatile 关键字的，针对于 volatile 关键字的写操作肯定是在读操作之前，也就是说读取的值肯定是最新的。

## ==解决线程安全问题的第一个方法：使用同步代码块==

#### 1.格式

==synchronized==(任意对象。例如：NEW OBJECT //随便对象都行){

可能出现不安全的代码

}

##### 任意对象就是锁对象

一个线程拿到锁后，会进入同步代码块中执行，其他线程拿不到锁，进不去同步代码块，在外面等待排队，实现了线程安全



## ==解决线程安全问题的第二个方法：同步方法==

### 一：普通同步方法（非静态）

#### 格式：

修饰符 synchronized 返回值类型 方法名（参数）{

方法体

return ...

}

==位置： 在实现类中，与重写的run方法并列，在run中调用他==

锁：this对象



### 二：静态同步方法

#### 格式：

修饰符 static synchronized 返回值类型 方法名（参数）{

 方法体

return 结果

}

锁：class对象



# 死锁和线程状态

### 死锁

两个或者两个以上的线程，在执行的过程中，由于竞争同步锁而产生一种阻塞的情况，如果没有外力的作用，他们将无法继续执行下去，这种情况就是死锁

#### ==死锁一般出现在同步代码块的嵌套中==



## 线程状态（生命周期）

![](C:\Users\Administrator\Desktop\java笔记\线程状态.png)

![](C:\Users\Administrator\Desktop\java笔记\线程状态2.png)

![](C:\Users\Administrator\Desktop\java笔记\线程状态方法.png)

# Lock锁

一个接口

##### 实现类:ReentrantLock

#### 方法：

lock()获得锁

unlock()释放锁

```java
Lock lock = new ReentrantLock();
lock.lock();
....................
lock.unlock();
.................
```



#### synchronized()和lock()的区别：

synchronized不管是同步代码块还是同步方法，都需要在结束一对{}后才能释放对象

lock通过两个方法控制，使用更加灵活





# 实现多线程的第三种方法

## 实现Callable接口，类似与Runnable

### 方法：

call() 设置线程任务



#### call()与run()的区别：

call方法有返回值,有异常可以throws

run方法没有返回值，不能throws



## <V>泛型：

用于指定我们操作什么类型的数据，<>中只能写数据引用类型，不行默认为Object类型数据

//实现Callable时,指定泛型是什么类型的，返回值就是什么类型的



##### 获取call方法返回值：FutureTask<v>类

##### FutureTask<v>实现了一个接口 Future<v>

##### FutureTask<v>有一个方法：get()   获取call方法的返回值



# 实现多线程的第四种方法

#### 线程池：

之前来一个线程任务，就需要创建一个线程对象去执行，用完还要销毁线程对象，如果线程对象多了，就需要频繁创建线程对象和销毁消除线程对象，会严重销毁内存资源，所以我们让线程对象循环利用，用的时候拿，用完了拿回去

![](C:\Users\Administrator\Desktop\java笔记\线程池概念.png)



### 实现：

1.如何创建线程池：用具类->Executors

2.获取线程池对象：Exectors中的newFixedThreadPool(int nThreads) //参数为最多的线程对象条数

3.返回值ExecutorService是线程池,用来管理线程对象

4.执行线程任务：ExecutorService中的方法submit(),提交Runnable任务或Callable任务用于执行

5.方法返回值：Future接口，用于接受call方法或者run方法的返回值,run没有返回值可以不用

​			get()方法

6.关闭线程池：ExecutorService中的方法 shutdown() 启动有序关闭，先前提交的任务将被执行，但不会接受任何新任务



# 定时器Timer(了解）:

概述：定时器

#### 构造：Timer()

#### 方法：

schedule(task,firsttime,period)

task:抽象类，runnable的实现类

firstime：从什么时间开始

period:隔多久来一次 （单位：毫秒）



# 集合：

怎么学集合？ 学特点 学怎么用

之前学了保存数据的有：变量，数组（==缺点定长==），所以如果添加一个数据或者删除一个数据，信仰创建新数组不好用。所以可以使用长度可变的容器：集合



### 特点：

a.只能存储引用数据类型的数据

b.长度可变,操作方便

c.有大量方法



### 分类：

a.单列集合：一个元素就一个组成部分

b.双列集合：一个元素有两个组成部分 



## 1.单列集合框架

![](C:\Users\Administrator\Desktop\java笔记\集合框架.png)

#### 所有单列集合的接口：Collection  

还有两个子接口 List接口和Set接口 它两继承Collection

List接口的实现类：ArrayList、LinkedList、Vector

​	ArrayList:元素有序，元素可重复，有索引，线程不安全，底层为数组

​	LinkedList:元素有序，元素可重复，有索引，线程不安全，底层为双向链表（本质上无索引）

​	Vector（不常用）:元素有序，可重复，有索引，线程安全，底层为数组

Set的实现类： Hashset,LinkedHashSet,TreeSet

​	Hashset:元素无序，元素唯一，无索引，线程不安全，底层为哈希表

​	LinkedHashSet:元素有序，元素唯一，无索引，线程不安全，底层为哈希表加双向链表

​	TreeSet:可对元素进行排序，元素唯一，无索引，线程不安全，底层为红色树



## Collection接口的使用：

#### 概述：单列集合的顶级接口

#### 使用：

​		多态创建 Collection<E> 对象名 = new 实现类对象<E>()

​		<E>被称为泛型，决定了集合中能存储什么类型的数据，可以统一元素类型

​		泛型中只能写引用数据类型，如果不写，默认Object类型，此时什么类型的数据都可以存储

​	  		<int>不行    <Integer> 行

##### 		==细节：new集合对象时，等号前的泛型必须写，等号后的可以不写== 因为jvm会根据前面的推出后面的



#### 常用方法：

​	add(e):将给定的元素添加到当前集合中

​	addAll(Collection <? extends E> c):将另一个集合元素添加到当前集合中（集合合并）

​	clear():清楚集合中的所有元素

​	contains(o):判断当前集合中是否包含指定的元素

​	isEmpty():判断是否为空

​	remove(o):删除指定的元素

​	toArray():把集合中的元素存储到数组中

​	size():返回元素个数



# 迭代器：

用到：Iterator接口

##### 作用：遍历集合

获取：Collection中的方法：

​		Iterator<E> iterator()

方法：

​	boolean hasNext() 判断集合有没有下一个元素

​	E next() 获取下一个元素

​			

```java
//假设已经有了集合list,其中有元素
Iterator<String> iterator = list.iterator();
while(iterator.hasNext()){
    String element =iterator.next();
    System.out.println(element);
}
```

注意：next方法不要连续使用多次，容易出现错误



# ArrayList：

#### 概述：List接口的实现类

#### 特点：

元素有序，可重复，有索引，线程不安全

#### 数据结构：数组

![](C:\Users\Administrator\Desktop\java笔记\arraylist 常用方法.png)



# LinkedList:

概述：是List接口的实现类

#### 特点：

元素有序，可重复，有索引，线程不安全

#### 数据结构：双向链表

#### 方法：

![](C:\Users\Administrator\Desktop\java笔记\linkedlist.png)



# 增强For:

#### 基本使用：

​	遍历集合或者数组，

#### 格式：

for(元素类型 变量名：要遍历的集合名或者数组名){

....................//变量名代表每一个元素

}

#### 快捷键：

#### 集合名或者数组名.for



#### 遍历集合底层实现原理：迭代器

#### 遍历数组底层实现原理：普通数组

#### ==在使用增强for的时候，不要随意修改数组长度，否则会出现并发修改异常==



# Collections集合工具类：

一个集合工具类

#### 特点：

构造私有

方法都是静态的



#### 使用：类名直接调用

### 方法：

Collelctions.addAll(Collection<?supper T> c,T... elements) 批量添加对象

Collelctions.shuffle(List<?> list) 将集合中的元素顺序打乱

Collelctions.sort(List<T>list)按照默认规则(ASCLL表）排序

##### ==sort(List<T> list,Compatator<?super T> c) 按照自己指定的规则排序==

​				Compatator比较器：

​				方法:int compare(T o1,To2) //o1-o2升序  o2-l1降序

​	![](C:\Users\Administrator\Desktop\java笔记\比较compatator.png)

#### 扩展：

Array中的静态方法：	

​	asList(T...a) 直接指定元素，转存到list集合中

​				List<String> list =Arrays.asList("张三","李四","王五")；



# 泛型：

*使用 Java 泛型的概念，我们可以写一个泛型方法来对一个对象数组排序。然后，调用该泛型方法来对整型数组、浮点数数组、字符串数组等进行排序。*

#### 关键字：<>

#### 作用：统一数据类型，防止将来的数据转换异常

#### 注意：

1.泛型中的类型必须是引用类型

2.如果不写，默认为Object



## 泛型方法：

可以接收不同类型的数据

所有的泛型方法声明都有一个类型声明部分（<>)，它定义在方法返回类型之前。<>中包含一个或多个类型参数，用逗号隔开,每个泛型参数被称为类型变量

类型参数能被用来声明返回值类型

参数必须是引用数据类型



#### java中的泛型标记符:

E->Element(在集合中使用，元素)=

T->Type(Java类)

K->键

V->value值

N->number（数值类型）

?->不确定的数据类型

```java
public class Test{
public static <E> void printa(E[] inputarray){
for(E e:inputarray){
System.out.printf("%s",e);
}
}
public static void main(String args[]){
Integer [] inta={1,2,3,4,5};//
Double [] doublea={1.1,2.2,3.3,4.4,5.5};//
Character[] chara={'H','E','L'};//都是包装类数组，泛型必须用引用数据类型
printa(inta);
printa(doublea);
printa(chara);
}
}
```

==可以用extends来限制<>传递过来的参数，如==

​			public static<T extends Number> double sum(T num1,T num2){

.........................................................

}///只能接受Number和他的子类



## 泛型类：

泛型类和非泛型类的声明类型，只是在类名后添加了类型参数声明部分

和泛型方法一样，泛型类的类型参数声明部分也包含一个或多个类型参数，参数间用逗号隔开。一个泛型参数，也被称为一个类型变量，是用于指定一个泛型类型名称的标识符。因为他们接受一个或多个参数，这些类被称为参数化的类或参数化的类型。



#### 类型通配符：<?>

例如 **List<?>** 在逻辑上是 **List<String>,List<Integer>** 等所有 **List<具体类型实参>** 的父类。

类型通配符下限通过形如 **List<? super Number>** 来定义，表示类型只能接受 **Number** 及其上层父类类型，如 **Object** 类型的实例。



# Hash Set:

HashSet 类位于 java.util 包中，使用前需要引入它

HashSet 基于 HashMap 来实现的

#### 特点：

不允许重复，允许null，无序，线程不安全

它实现了Set接口（set实现了collections接口）

方法：

添加元素可以使用 add() 方法

contains() 方法来判断元素是否存在于集合当中

remove() 方法来删除集合中的元素

删除集合中所有元素可以使用 clear 方法

计算 HashSet 中的元素数量可以使用 size() 方法



# Hash Map:

HashMap 是一个散列表，它存储的内容是键值对(key-value)映射。

HashMap 类位于 java.util 包中，使用前需要引入它

#### 特点：

允许一条null,线程不安全，无序，

HashMap 的 key 与 value 类型可以相同也可以不同，可以是字符串（String）类型的 key 和 value，也可以是整型（Integer）的 key 和字符串（String）类型的 value。

#### 创建：HashMap<Integer, String> Sites = new HashMap<Integer, String>();

#### 方法：

添加键值对(key-value)可以使用 put() 方法，put(1,"google")

 get(key) 方法来获取 key 对应的 value:

 remove(key) 方法来删除 key 对应的键值对

删除所有键值对(key-value)可以使用 clear 方法

计算 HashMap 中的元素数量可以使用 size() 方法



# Java 流(Stream)、文件(File)和IO

java.io包几乎包含了所有操作输入，输出的类

Java 为 I/O 提供了强大的而灵活的支持，使其更广泛地应用到文件传输和网络编程中。

## 读取控制台输入

Java 的控制台输入由 System.in 完成

为了获得一个绑定到控制台的字符流，你可以把 System.in 包装在一个 BufferedReader 对象中来创建一个字符流。

下面是创建 BufferedReader 的基本语法：

```java
BufferedReader br = new BufferedReader(new

						InputStreamReader(System.in));
```

BufferedReader 对象创建后，我们便可以使用 read() 方法从控制台读取一个字符，或者用 readLine() 方法读取一个字符串。

#### 单个字符读取：

```java
//使用 BufferedReader 在控制台读取字符
 
import java.io.*;
 
public class BRRead {
    public static void main(String[] args) throws IOException {
        char c;
        // 使用 System.in 创建 BufferedReader
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        System.out.println("输入字符, 按下 'q' 键退出。");
        // 读取字符
        do {
            c = (char) br.read();
            System.out.println(c);
        } while (c != 'q');
    }
}
```

## 读取字符串：

从标准输入读取一个字符串需要使用 BufferedReader 的 readLine() 方法。

String readLine( ) throws IOException

```java
//使用 BufferedReader 在控制台读取字符
import java.io.*;
 
public class BRReadLines {
    public static void main(String[] args) throws IOException {
        // 使用 System.in 创建 BufferedReader
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String str;
        System.out.println("Enter lines of text.");
        System.out.println("Enter 'end' to quit.");
        do {
            str = br.readLine();
            System.out.println(str);
        } while (!str.equals("end"));
    }
}
```

==一般使用Scanner类，不使用上面的。。。==



## FileInputStream：

该流用于从文件读取数据，它的对象可以用关键字 new 来创建。

可以使用字符串类型的文件名来创建一个输入流对象来读取文件：

​						InputStream f = new FileInputStream("C:/java/hello");

也可以使用一个文件对象来创建一个输入流对象来读取文件。我们首先得使用 File() 方法来创建一个文件对象：

```
File f = new File("C:/java/hello");
InputStream in = new FileInputStream(f);
```



#### 方法：

**close()** 关闭此文件输入流并释放与此流有关的所有系统资源

 **finalize()**这个方法清除与该文件的连接。确保在不再引用文件输入流时调用其 close 方法。

==**read(int r)**这个方法从 InputStream 对象读取指定字节的数据。返回为整数值。返回下一字节数据，如果已经到结尾则返回-1。==

 **read(byte[] r)** 这个方法从输入流读取r.length长度的字节。返回读取的字节数。如果是文件结尾则返回-1。



## FileOutputStream：

该类用来创建一个文件并向文件中写数据。

如果该流在打开文件进行输出前，目标文件不存在，那么该流会创建该文件。

创建方法和上一个类似

#### 方法：

**close()关闭此文件输入流并释放与此流有关的所有系统资源。** 

 **write(int w)**这个方法把指定的字节写到输出流中。

 **finalize()**这个方法清除与该文件的连接。确保在不再引用文件输入流时调用其 close 方法。



## 文件和I/O：

### 创建目录：

File类中有两个方法可以用来创建文件夹：

- **mkdir( )**方法创建一个文件夹，成功则返回true，失败则返回false。失败表明File对象指定的路径已经存在，或者由于整个路径还不存在，该文件夹不能被创建。

- **mkdirs()**方法创建一个文件夹和它的所有父文件夹。

- ```java
  import java.io.File;
   
  public class CreateDir {
      public static void main(String[] args) {
          String dirname = "/tmp/user/java/bin";
          File d = new File(dirname);
          // 现在创建目录
          d.mkdirs();
      }
  }创建目录 "/tmp/user/java/bin"
  ```

## 读取目录

一个目录其实就是一个 File 对象，它包含其他文件和文件夹。

如果创建一个 File 对象并且它是一个目录，那么调用 isDirectory() 方法会返回 true。

可以通过调用该对象上的 list() 方法，来提取它包含的文件和文件夹的列表。

```java
import java.io.File;
 
public class DirList {
    public static void main(String args[]) {
        String dirname = "/tmp";
        File f1 = new File(dirname);
        if (f1.isDirectory()) {
            System.out.println("目录 " + dirname);
            String s[] = f1.list();
            for (int i = 0; i < s.length; i++) {
                File f = new File(dirname + "/" + s[i]);
                if (f.isDirectory()) {
                    System.out.println(s[i] + " 是一个目录");
                } else {
                    System.out.println(s[i] + " 是一个文件");
                }
            }
        } else {
            System.out.println(dirname + " 不是一个目录");
        }
    }
}
```

## 删除目录或文件:

删除文件可以使用 **java.io.File.delete()** 方法。

==以下代码会删除目录 **/tmp/java/**，需要注意的是当删除某一目录时，必须保证该目录下没有其他文件才能正确删除，否则将删除失败。==

```java
import java.io.File;
 
public class DeleteFileDemo {
    public static void main(String[] args) {
        // 这里修改为自己的测试目录
        File folder = new File("/tmp/java/");
        deleteFolder(folder);
    }
 
    // 删除文件及目录
    public static void deleteFolder(File folder) {
        File[] files = folder.listFiles();
        if (files != null) {
            for (File f : files) {
                if (f.isDirectory()) {
                    deleteFolder(f);
                } else {
                    f.delete();
                }
            }
        }
        folder.delete();
    }
}
```





# Java 正则表达式

正则表达式定义了字符串的模式。

正则表达式可以用来搜索、编辑或处理文本。

正则表达式并不仅限于某一种语言，但是在每种语言中有细微的差别。

Java 提供了 java.util.regex 包，它包含了 Pattern 和 Matcher 类，用于处理正则表达式的匹配操作。

一个字符串其实就是一个简单的正则表达式，例如 **Hello World** 正则表达式匹配 "Hello World" 字符串。

**.**（点号）也是一个正则表达式，它匹配任何一个字符如："a" 或 "1"。



# Java 网络编程：

**同步和异步：**同步和异步是针对应用程序和内核的交互而言的，同步指的是用户进程触发IO 操作并等待或者轮询的去查看IO 操作是否就绪，而异步是指用户进程触发IO 操作以后便开始做自己的事情，而当IO 操作已经完成的时候会得到IO 完成的通知。

以银行取款为例：

**同步** ： 自己亲自出马持银行卡到银行取钱（使用同步 IO 时，Java 自己处理IO 读写）；

**异步** ： 委托一小弟拿银行卡到银行取钱，然后给你（使用异步IO 时，Java 将 IO 读写委托给OS 处理，需要将数据缓冲区地址和大小传给OS(银行卡和密码)，OS 需要支持异步IO操作API）；

**阻塞和非阻塞：**阻塞和非阻塞是针对于进程在访问数据的时候，根据IO操作的就绪状态来采取的不同方式，说白了是一种读取或者写入操作方法的实现方式，阻塞方式下读取或者写入函数将一直等待，而非阻塞方式下，读取或者写入方法会立即返回一个状态值。

以银行取款为例：

**阻塞** ： ATM排队取款，你只能等待（使用阻塞IO时，Java调用会一直阻塞到读写完成才返回）；

**非阻塞** ： 柜台取款，取个号，然后坐在椅子上做其它事，等号广播会通知你办理，没到号你就不能去，你可以不断问大堂经理排到了没有，大堂经理如果说还没到你就不能去（使用非阻塞IO时，如果不能读写Java调用会马上返回，当IO事件分发器通知可读写时再继续进行读写，不断循环直到读写完成）

**1.BIO 编程**

Blocking IO： 同步阻塞的编程方式。

BIO编程方式通常是在JDK1.4版本之前常用的编程方式。编程实现过程为：首先在服务端启动一个ServerSocket来监听网络请求，客户端启动Socket发起网络请求，默认情况下ServerSocket回建立一个线程来处理此请求，如果服务端没有线程可用，客户端则会阻塞等待或遭到拒绝。

且建立好的连接，在通讯过程中，是同步的。在并发处理效率上比较低。大致结构如下：

同步并阻塞，服务器实现模式为一个连接一个线程，即客户端有连接请求时服务器端就需要启动一个线程进行处理，如果这个连接不做任何事情会造成不必要的线程开销，当然可以通过线程池机制改善。

BIO方式适用于连接数目比较小且固定的架构，这种方式对服务器资源要求比较高，并发局限于应用中，JDK1.4以前的唯一选择，但程序直观简单易理解。

使用线程池机制改善后的BIO模型图如下:

**2.NIO 编程：Unblocking IO（New IO）： 同步非阻塞的编程方式。**

NIO本身是基于事件驱动思想来完成的，其主要想解决的是BIO的大并发问题，NIO基于Reactor，当socket有流可读或可写入socket时，操作系统会相应的通知引用程序进行处理，应用再将流读取到缓冲区或写入操作系统。也就是说，这个时候，已经不是一个连接就要对应一个处理线程了，而是有效的请求，对应一个线程，当连接没有数据时，是没有工作线程来处理的。

NIO的最重要的地方是当一个连接创建后，不需要对应一个线程，这个连接会被注册到多路复用器上面，所以所有的连接只需要一个线程就可以搞定，当这个线程中的多路复用器进行轮询的时候，发现连接上有请求的话，才开启一个线程进行处理，也就是一个请求一个线程模式。

在NIO的处理方式中，当一个请求来的话，开启线程进行处理，可能会等待后端应用的资源(JDBC连接等)，其实这个线程就被阻塞了，当并发上来的话，还是会有BIO一样的问题

**3.AIO编程：Asynchronous IO： 异步非阻塞的编程方式。**

与NIO不同，当进行读写操作时，只须直接调用API的read或write方法即可。这两种方法均为异步的，对于读操作而言，当有流可读取时，操作系统会将可读的流传入read方法的缓冲区，并通知应用程序；对于写操作而言，当操作系统将write方法传递的流写入完毕时，操作系统主动通知应用程序。即可以理解为，read/write方法都是异步的，完成后会主动调用回调函数。在JDK1.7中，这部分内容被称作NIO.2，主要在java.nio.channels包下增加了下面四个异步通道：AsynchronousSocketChannel、AsynchronousServerSocketChannel、AsynchronousFileChannel、AsynchronousDatagramChannel



## Socket 编程

.............................................



# Java 反射（Reflection）：

后续笔记存于web中
