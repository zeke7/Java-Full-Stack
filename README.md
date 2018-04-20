# Java 学习笔记
***
因为在网上看到有些很多笔记很不错，而且边学习边做笔记也能帮助自己更好的理解，同时又能帮助到其他人，所以我会经常更新我的笔记并分享给大家。。。  
本笔记将从最基础的JAVA SE开始到JAVA EE 以及后面的一系列框架    
喜欢的同学可以star一下我哦。。。如果有哪里出错的或者有问题的请发邮件联系我！（hfang@coastal.edu）  
***
## 目录
* [JAVA SE](#java-se-部分)
* [第1节 Hello World](#第1节-hello-world)
* [第2节 代码的注释](#第2节-代码的注释)
* [第3节 标识符与关键字](#第3节-标识符与关键字)
* [第4节 数据类型](#第4节-数据类型)
* [第5节 运算符](#第5节-运算符)
* [第6节 程序逻辑控制](#第6节-程序逻辑控制)
* [第7节 方法的使用](#第7节-方法的使用)
* [第8节 面向对象](#第8节-面向对象)
* [第9节 数组](#第9节-数组)
* [第10节 String](#第10节-string)
* [第11节 static关键字](#第11节-static关键字)
* [第12节 代码块和内部类](#第12节-代码块和内部类)
* [第13节 继承 覆写 抽象类](#第13节-继承-覆写)
* [第14节 抽象类 接口](#第14节-抽象类-接口)
* [第15节 Object类](#第15节-object类)
* [第16节 异常](#第16节-异常)
***
#### 安装配置JAVA环境（略）详情参考  
https://www.java.com/zh_CN/download/help/download_options.xml    
#### 第1节 Hello World
建立 Hello.java 文件，先来一个最简单的应用程序：  
```Java
  public class Hello{
    public static void main(String[]args){
          System.out.println("Hello world");
      }
    }
```
* JAVA 程序分为两个操作：
  * 编译程序：（在cmd中）javac Hello.java形成 Hello.class文件
  * 解释程序：（在cmd中）java Hello  
* JAVA 程序组成：类（核心）
  * public class 类名称{}：文件名（Hello.java）与类名称保持一致
  * class 类名称{}：文件名（Hello.java）与 类名称 可以不一致，可以同时存在多个class，编译后形成各自的*.class文件
* 主方法：所以的程序都由主方法开始执行 public static void main(String[]args){}  
#### 第2节 代码的注释
  代码的注释意思是，你的代码并不会被程序执行，就相当于一段文本。
* // 单行注释；
* /*...*/ 多行注释；
* /**...*/ 文档注释；
```Java
  public class Hello{
    public static void main(String[]args){
          //System.out.println("Hello world"); 单行注释；
          
       /* System.out.println("Hello world"); 
          System.out.println("Hello world"); 
          System.out.println("Hello world"); */ 多行注释；
        }
        /** 文档注释
          ... IDE 会帮助编写 （Integrated Development Environment）
         */
     public static void sayHello(){}
    }
```  
#### 第3节 标识符与关键字
  标识符通俗的说就是，程序中各个类或者变量或者方法的名字，其由字母、数字、_、$组成，不能是JAVA保留的关键字，并且不能以数字开头。    
  标识符可以使用中文，但是不推荐使用。
  关键字参考百度百科：https://baike.baidu.com/item/java%E5%85%B3%E9%94%AE%E5%AD%97  
#### 第4节 数据类型
  本节代码:[DataTypeDemo.java](/Java_examples/DataTypeDemo.java)  
  Java数据类型分为 内置类型 和 引用数据类型 两大类  
  内置类型有： 
* boolean	布尔值，作二元判断	true, false （逻辑控制）
* byte	8位有符号整数	最小值-128，最大值127 （内容传递，编码解码）
* short	16位有符号整数	最小值-32768，最大值32767 
* int	32位有符号整数	最小值-2147483648（-2^31），最大值2147483647（2^31-1） （表示整数）
* long	64位有符号整数	-2^63~(2^63-1) （日期时间，文件内存）
* float	32位浮点数	1.4E-45~3.4028235E38
* double	64位浮点数	4.9E-324~1.7976931348623157E308 （表示小数）
* char	16位Unicode字符  （避免使用中文的乱码问题）
  引用数据类型是数组，根据这些基本的内置类型扩展的新类，还有接口（之后会学）  
#### int, long, byte（数据类型cont’d）  
  int, long, byte类型可称为整形（e.g. 10,20,30....这些都是常量）  
  在程序中，一般使用变量(变量名称在一个代码块中只能声明一次)来储存常量(格式：数据类型 变量名 = 常量)  
  当然，储存的常量也不能无限大，int可以储存最小值-2147483648（-2^31），最大值2147483647（2^31-1）  
  当储存的数值超过了最大值，就会变成最小值，像一个循环，在DataTypeDemo.java中有代码。  
  为了解决这个问题，可以扩大数据类型 int --> long (-2^63~(2^63-1))此时出现一个问题，数据类型之间如何进行转换？  
*  数据类型的转换有这些规律：
   * 范围小的数据跟范围大的数据进行计算时，自动向范围大的转型
   * 范围大 --> 范围小，采用强制转换（方法1： 常量标记，方法2：(数据类型)），在DataTypeDemo.java中有代码。
#### float, double（数据类型cont’d）  
   double是默认的小数类型，float的范围比double小，具体转换的例子在DataTypeDemo.java中有代码。  
   整形不保留小数位，要使用double数据类型来显示小数。
#### char （数据类型cont’d）  
   char使用 “ ' ” 声明内容。  
   字符（char）可以与int类型互相转换（编码形式 ASCII部分编码）需要注意 '0'(char) 与 0 (int) 是不一样的，具体的例子在DataTypeDemo.java中。
#### boolean （数据类型cont’d）  
   只有两种取值：true, false。多用于条件判断，具体的例子在DataTypeDemo.java中。
#### String （数据类型cont’d）  
  String使用 “ " ” 声明内容。  
  String表示的是一个字符串（多个字符的集合），可以使用“+”进行连接操作  
  转义字符：换行(\n), 制表符(\t), \(\\), 双引号(\"), 单引号(\')  
#### 第5节 运算符
本节代码:[OperatorDemo.java](/Java_examples/OperatorDemo.java)  
常用的运算符：四则运算，三目运算，逻辑运算
* 四则运算，即简单的加减乘除以及取模（mod）的运算，还有两种特殊的运算符（++，--）分别代表自增和自减，但是位置不同效果不同，具体在本节代码中有实现。可以根据代码展示的结果进行推敲更助于理解。
* 三目运算是根据条件进行判断并返回一个内容，具体格式为：数据类型 变量 = Boolean表达式？满足条件时的内容：不满足条件时的内容；。
* 逻辑运算主要有3种，与（&，&&），非（！），或（|，||）  
  &与&&的区别在于，& 会执行所有的判断条件，而 && 当一系列条件从前往后，某一个条件不符合时就不再判断后面的条件。  
  |与||的区别在于，| 会执行所有的判断条件只要有一个条件正确就返回true，而 || 当一系列条件从前往后，某一个条件符合时就返回true就不再判断后面的条件。
#### 第6节 程序逻辑控制
本节代码:[LogicDemo.java](/Java_examples/LogicDemo.java)  
通过分支结构控制程序的逻辑：  
```Java
  public class Hello{
    public static void main(String[]args){
    //第一种通过if...else的方式
         if(条件){
          //满足条件
          ...do something
         }else{
          //不满足条件
          ...do something
         }
    //第二种通过if...else if...else if..若干...else 的方式
        if(条件1){
          //满足条件1
          ...do something
         }else if(条件2){
          //满足条件2
          ...do something
         }else if(条件3){
          //满足条件3
          ...do something
         }else{
          //不满足以上条件
          ..do something
         }
    //第三者通过switch进行条件判断
        switch(整数|字符|枚举|字符串){
            case 内容1:{
               //满足内容1
               [break;]
            }
            case 内容1:{
               //满足内容2
               [break;]
            }
            case 内容1:{
               //满足内容3
               [break;]
            }
            ...
            [default: {
              //不满足以上任意一个内容，默认情况...
            }]
        }
        //如果不添加break的话，switch就会从第一个满足条件的case开始执行接下来的所有case
        
      }
```  
通过循环结构控制程序的逻辑： 
  主要分为两种，while循环和for循环
  * while循环的用法为：  
  ```Java
      while(条件){
        ....do something  
      }  //当条件满足，便会一直执行其中的程序
      
      do{
        ...do something
      }while(条件){
        ...do something
      } //先执行do中的程序，如果条件满足再进入while
  ```
  * for循环的用法为：  
   ```Java
    for(初始化条件; 循环判断; 条件变更){
          ...do something
    }
   ```  
 对于循环的控制，使用两种关键字: continue(推出此次循环继续下一次循环)， break(完全退出循环)
 #### 第7节 方法的使用
 本节代码:[MethodDemo.java](/Java_examples/MethodDemo.java) 
 * 方法基本上来说，就是把一段代码封装起来变成代码块。当你想要使用这个代码块的功能时，不需要重新进行编写，只需要调用这个方法名称就可以了。当然定义方法的格式比较复杂，只能给出一个大概的模板。
 ```Java
   public (static) 返回值类型 方法名称(参数类型 参数名字, ...){
          ...do something
          [return 返回值;] // 此返回值类型应与方法体中的类型一致
          }
   如果此方法没有返回值类型，就可以使用 void 在返回值类型位置进行声明
 ```
 * 方法中一个比较重要的概念是“重载”，即同一个方法名称要执行多项不同的操作，简单来说就是，方法的名称相同，参数的类型和个数不相同。
    * 需要注意的是，进行重载的方法返回值类型一定要统一
 * 方法中的另一个概念是“递归调用”，简单来说就是方法自己调用自己，为了避免无限循环下去，要设置一个结束条件，在本节代码中有实例。  
    注：定义方法的格式比较复杂，本节的例子只能是其中的一小部分。
 #### 第8节 面向对象
  本节代码:[ObjectOrientDemo.java](/Java_examples/ObjectOrientDemo.java)
* 面向对象：是代码变的模块化，组件化，然后重复利用这些模块，避免代码的重复编写。  
    这种程序有这几种的特征：封装性，继承性，多态性。
  * 封装性：在代码块里，有许多的私有属性和方法，和一定的结构。封装性能够很好地保护代码块里的内容
  * 继承性：在实现的一定功能的代码块上扩充新的功能。
  * 多态性：有一类的代码具有多个不同表现形式或形态。例如：车中有许多类的车（轿车，货车，公交车）。同一个接口，使用不同的实例而执行不同操作。
***
* 类与对象 （最基本的组成单元）  
  类：用于保存一类对象所拥有的共同属性，描述出对象的结构，包括了属性和功能。不能直接使用，只能通过实例对象来使用。
  对象：根据某一类产生的此类的一个特定的对象，同一类的对象具有相同的属性和功能。 
***
* 类与对象的基本定义方法  
  类：class 类名{}，类中的组成主要有：**Field(属性，成员)  Method(方法)**
  对象：实例化对象的格式： 
  * 类名称 对象名称 = new 类名称(参数...); (一步完成)  
  * 类名称 对象名称 = null;  
    对象名称 = new new 类名称(参数...); (分步完成)  
**实例化对象之后**，可以使用这个对象来操作它的属性和方法： **对象.属性**  **对象.方法**
***
* **new 关键字**  
new 关键字引出一个概念，引用数据类型（分为 类，接口，和数组）。 引用数据类型需要使用 **new** 关键字来进行内存空间的开辟。  
* 堆内存：使用new关键字进行开辟空间（有一个地址）并保存对象的属性
* 栈内存：保存堆内存的地址数值
* 引用：当使用了**new**关键字进行实例化对象，各自对象肯定占据一个自己的堆内存空间，不会互相影响。例如本节实例代码中的car4和car5。
* 对象引用传递:  本节实例代码中的car6和car7。结合结果进行理解一个堆内存可以同时被多个栈内存指向。
***
**深入理解封装性**
     如果没有封装性这个概念，一个对象可以从外部很容易的调用其属性和方法，对其本身的属性进行修改，这是很不安全的。解决的方法就是将类中的属性设置为对外不可见(private)从而使得外部对象无法直接调用并操作类中的属性。  
     总结一下，针对类的属性都要求使用private声明，如果想要被外部所操作就要使用setter，getter方法。  
     封装性就是保证类内部定义被外部不可见。
***
**构造方法和匿名对象**  
* 构造方法：方法名称与类名称相同，没有返回值声明。当创建了一个新的对象时，它的构造方法就会被调用，只调用一次。如果用户没有为这个类定义构造方法，JAVA 会自动调用内部的无参构造方法。当用户定义了一个构造器之后，JAVA程序不会自动调用内部的无参构造器。构造方法实在构造对象的最后一步被调用的。  
  * 构造方法的作用：在实例化对象的时候，传入参数直接为实例化对象属性进行赋值。从而避免多次使用setter方法进行对类属性的操作。
  * 构造方法的重载:注意参数的类型及个数，参考本节代码中的Book类。  
* 匿名对象：没有栈指向意味着没有其他对象对其进行引用，当使用过一次之后就将变为垃圾空间等待回收。  
* **代码模型：简单JAVA类** 实例为本节代码Student类
  * 类名称有意义
  * 属性必须使用private封装
  * 提供至少一个构造方法
  * 不可出现输出语句（输出类的信息）
  * 覆写toString()方法，用于取得完整对象信息
 #### 第9节 数组
  本节代码:[ArrayDemo.java](/Java_examples/ArrayDemo.java)
* 数组的基本定义就是一组相同类型的对象的集合，并且数组属于引用数据类型。  
声明并开辟数组的格式为：  
  **数据类型 数组名称[] = new 数据类型[长度];（也可以分步完成，参考对象实例化）**  
静态初始化的格式为：  
  **数据类型 数组名称[] = {数据，数据，...};**  
  **数据类型 数组名称[] = new 数据类型[]{数据，数据，...};** 
* 数组的index从0开始，通过 数组名称[index] 访问数组中的对象。如果index超过了(长度-1),会出现 index越界的错误。 
* JAVA的数组采用的是顺序结构，所以可以采用循环的方式有顺序地输出数组中的所有的值  
* 二维数组  
声明并开辟数组的格式为：  
  **数据类型 数组名称[][] = new 数据类型[行][列];（也可以分步完成，参考对象实例化）**  
  **数据类型 数组名称[][] = new 数据类型[][]{{数据，数据，...},{数据，数据，...}};** 
* 对象数组 （*引用数据类型的集合* ）  
声明并开辟数组的格式为：  
  **类名称 对象数组名称[] = new 类名称[长度];（也可以分步完成，参考对象实例化）**  
静态初始化的格式为：  
  **类名称 对象数组名称[] = new 数据类型[]{实例化对象，实例化对象，...};** 
 #### 第10节 String  
 本节代码:[StringDemo1.java](/Java_examples/StringDemo1.java) && [StringDemo2.java](/Java_examples/StringDemo2.java)
 * String类的实例化方式
    * 直接赋值
    * 使用new关键字进行赋值
    * 两种实例化方式的区别：如果使用直接赋值的方式，如果有多个对象都赋了相同的String值(e.g. "hello")，则他们指向的地址都相同。事实上匿名对象会被存入一个对象池，如果新的对象赋的值已经在对象池中存在的话，会自动进行对象的引用不会开辟新的空间。如果使用new关键字进行对象的实例化的话，即使每个对象都赋了相同的String值，每个对象的地址都不相同。（会产生大量垃圾空间）
 * String中的比较
    * "=="比较 ==>  比较的是字符串对象的地址, 本节代码中有实例
    * equals()方法 ==> 内容比较
 * String的匿名对象即为字符串(e.g. "Helloworld")
 * String的常量定义之后不能进行更改
 ***
 **String 的常用操作方法**
 **此内容多在于StringDemo2.java中实例**  *此处仅仅列出常用方法* 
 * charAt()方法返回指定index的字符
 * toCharArray() 将字符串转换为字符数组
 * getBytes() 字符串变为字节数组方便数据传输和转换 
 * equals()进行字符串比较，区分大小写
 * equalsIgnoreCase()进行字符串比较，区分大小写
 * compareTo()通过字符编码判断两个字符串大小
 * contains()判断子字符串是否存在
 * indexOf()从前向后查找字符串，返回第一个字符的位置
 * lastIndexOf()从后向前查找字符串，返回第一个字符的位置
 * startWith() 是否以指定字符串开头
 * endsWith() 是否以指定字符串结尾
 * contains() 判断子字符串是否存在
 * replaceAll() 字符串替换，全部替换
 * replaceFirst() 替换首个符合要求的字符
 * substring() 字符串截取
 * split() 字符串拆分  
 ......还有一些方法在实例Demo中有提供
 #### 第11节 static关键字  
 本节代码:[StaticDemo.java](/Java_examples/StaticDemo.java) 
 Static 可以用来声明属性和方法  
 * static 属性为全局属性, 一个对象对他进行修改后, 此属性在其他对象中也被修改  
   可以使用 类直接调用此属性进行修改 (在没有实例化对象的情况下也可以操作此属性)
 * static方法, 可以在没有实例化对象的情况下调用  
 * static方法不能直接访问 非static属性或者方法  
   非static属性或者方法 没有限制调用其他方法，但其本身必须被实例化对象调用
 #### 第12节 代码块和内部类
 代码块分为：普通代码块（没用...），构造块（没用...），静态块（优先执行），同步代码块  
 内部类：  
   ```Java
   class Car{  //外部类
   	private String msg = "Hello";
        class Brand{ //内部类
	      private String brand = "BMW";
	      public void print(){
		    System.out.println(msg); //内部类可以直接使用外部类的私有属性，不需要实例化对象
		    System.out.println("Car Brand");
		}
	     }
	     //外部类可以轻松地使用内部类的私有属性
	     public void printBrand(){
	     	 new Brand().print();  //内部类对象
		 System.out.println(new Brand().brand);
	    }
	}
	public class TestDemo{
		public static void main(String args[]){
			Car car1 = new Car() ;
			car1.printBrand() ;
			//直接实例化内部类对象
			Car.Brand brand1 = new Car().new Brand();
		}
	}
   ```
 #### 第13节 继承 覆写
  本节代码:  
[ExtendsDemo.java](/Java_examples/ExtendsDemo.java)  
[OverwriteDemo.java](/Java_examples/OverwriteDemo.java)  
[PolymorphismDemo.java](/Java_examples/PolymorphismDemo.java)  
 ***
**继承**  *解决代码重用*  
class 子类 extends 父类 {}
* 子类被称为派生类（derived class）, 父类称为超类（super class）  
  子类可以继承使用父类的方法，并可以扩充自己的方法和功能  
  父类私有的属性（private）被子类使用但是不能被子类直接访问  
  子类在调用自己的构造前，先调用父类的无参构造， super()(在父类没有无参构造的情况下，必须加上)
* 限制：不允许多重继承（解决方法，B类继承A类，C类继承B类实现C类继承A,B两类）
***
**覆写**  *与重载不同*  
子类中的属性或者方法可能与父类中的属性或者方法同名，此时就需要使用覆写  
* 方法的覆写：如果子类没有覆写父类中的方法，子类的实例化对象将使用父类中的方法。被子类覆写的方法，不能比父类拥有更严格的访问控制权限（public > default > private),父类中的方法如果使用private声明，子类无法进行覆写  
***
**对象多态性**  
方法的多态性：本质上来说就是方法的重载和覆写  
对象的多态性：对象的向上（自动）向下（强制）转型
* 向上转型：同一个方法针对不同子类有不同的实现
* 向下转型：父类调用子类的方法，为了防止出现转型错误，使用 instanceof
 #### 第14节 抽象类 接口
  本节代码:  
[AbstractDemo.java](/Java_examples/AbstractDemo.java)  
[InterfaceDemo.java](/Java_examples/InterfaceDemo.java)  
***
**抽象类**
* 抽象方法要使用abstract进行声明，
* 并且拥有抽象方法的类一定是抽象类同样要是由abstract进行声明
* 法对抽象类进行实例化对象，抽象类必须拥有子类，抽象类的子类必须覆写抽象类中的全部抽象方法
* 抽象类的对象实例化对象需要依靠子类完成，向上转型
* 抽象类中会有一些属性，抽象类中同样存在构造方法对这些属性进行初始化
* 抽象类不能使用final进行定义，因为抽象类必须拥有子类  
***
**接口**
* 接口的组成：特殊的类，只有抽象方法和全局常量。使用interface关键字进行定义
* 接口必须要有子类，一个子类可以implements多个接口，接口的子类覆写接口中的所有抽象方法，并且采用向上转型的方法进行实例化操作
* 接口里面只有一种访问权限：public
* 一个接口可以使用extends同时继承多个接口，接口不能继承抽象类
* 接口用来定义不同层之间的操作标准
 #### 第15节 Object类
  本节代码:  
[ObjectDemo.java](/Java_examples/ObjectDemo.java)  
Object类是所有类的父类，
Object类可以接收全部类的对象，可以向上自动转型
可以通过Object类来实现类中的equals功能，eclipse可以自动生成
 #### 第16节 异常




 

 

 

