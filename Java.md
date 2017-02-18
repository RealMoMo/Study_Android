个人基础知识点梳理

//面试坑人考点
		
		int i=128;
		byte b=(byte)i; //i强制转换为byte类型，数据会溢出 最终等于-128
		System.out.println(b);
		//同理i=129 --> b=-127  
		
		//坑人考点2
		
		char c='a';
		System.out.println(c+1); //c+1自动转换为int类型 最终等于98
		char d=97;		
		System.out.println(d);//输出d为a
		
		//面试常见考点1
		//String类型是不是基本数据类型。 答案：不是，它是引用数据类型
		String str1="abc"; 
		String str2=new String("abc");
		System.out.println(str1+"  "+str2);//输出的内容是一致的
		boolean f=(str1==str2);
		System.out.println(f);//flase,地址是不一致的
		
		//2.常见考点   ---》      + 字符串拼接符 ， 算数运算符
		String str = "bui";
		System.out.println(1 + 3 + str + str + 2 + 2);
		
		//经典面试题
		int a = 8;
		int b = (a++)+(++a)+(a*10);
		//       8      10    100
		System.out.println(b);
		
		//		经典面试题一：
		int a,b; 
		a = b = 100;
		System.out.println(a); //100
		System.out.println(b); //100
		
//		经典面试题二：
		//下面的两种写法结果分别是？
		short s1=1; 
		//s1 =  s1+1; 会报错s1+1是int类型所以正确如下：
		s1 = (short) (s1+1);//要强转
		System.out.println(s1);
		
		short s2=1; 
		s2+=1;  //对于+=Java会自动强转。对于s2+＝1，Java会转成s2 = (short)(s2+1)  
		System.out.println(s2);		
		// s+=1 <=> s =  (s的类型)(s+1)
		
		
		
		/**
		 * 
		 * ==
		 * 基本数据类型（int）：判断值
		 * 引用数据类型（String）：判断内存空间（地址）
		 * int a=100;
		 * int b=100;
		 * boolean c=(a==b);//true
		 * 
		 * String str1="abc";
		 * String str2="abc";
		 * boolean d=(str1==str2);//true
		 * 
		 * String str3=new String("abc");
		 * String str4=new String("abc");
		 * boolean e=(str3==str4);//flase
		 */
		 
		 
		 	
//		经典面试题一：
		int x = 10;
		int y = 10;

		boolean flag = (x == y);
		System.out.println(flag);
		
//		经典面试题二：
		boolean b1 = true;
		boolean b2 = false;

		boolean b3 = (b1 == b2);
		System.out.println(b3);//false

		boolean b4 = (b1 = b2);
		System.out.println(b4);//false
		
		
		//	拓展1	
	//	JAVA 只有无符号右移，没有 无符号左移<<< 
	//	因为左移是在后面补0
	//	而右移是在前面边补1或0
	//	有无符号是取决于数的前面的第一位是0还是1
	//	所以右移是会产生到底补1还是0的问题。
	//	而左移始终是在右边补，不会产生符号问题。
	//	所以没有必要无符号左移<<<。
	//	无符号左移<<<和左移<<是一样的概念 
	//------------------------------------
	
	//	拓展2
	//	2进制 前面加0b或0B   0b11-->3
	//	8进制 前面加0   	011-->9
	//	16进制 前面加0x或0X   011-->17
	
	//	知识点1
	//	获取控制台输入Scanner scan = new Scanner(System.in);   实例化对象
	//			DataType className = scan.nextDateType();	
	//			scan这个对象去调用了nextDateType()方法，nextDateType：允许用户在控制台输入,返回值DateType
	//
	//	
	
	//	知识点2
	//	scan.close();
	//	申明了名为scan的数据输入扫描仪（Scanner），从而获得了配置内存，
	//	若结束时却没有关闭或释放该内存，而出现警告，只要用close()方法即可！
	
	//	知识点3
	//	switch允许的判断值：byte 、 short 、 int 、 char 、String 、 enum(枚举)
	
	
		//label
		//不建议使用：会让逻辑看起来比较复杂，比较乱，没有条理性
		//break label;可以跳出label循环
		//continue label;可以退出现在的循环并继续执行label循环
		// label可应用多重循环的跳出与跳过
		
		http: for( int i = 0; i < 3; i++){
					for(int j = 0; j < 3; j++){
						System.out.println("--i--"+i);
						if( i == 1){
							break http; //跳出http标签的循环体  即可以跳出多重循环
						}
					}
			}
			
--------------

		//Arrays.binarySearch  看看原码，返回是int类型
		//若在数组找到num ，返回的是元素下标
		//若没有找到，返回num插入数组位置的元素下标取负再减一			
			
		public static void main(String[] args) {
		int[] is = {2,435,23,6,4,16,18,20,22,24,26,28};
		
		Arrays.sort(is);//用sort方法，进行排升序
		for(int i : is){
			System.out.println(i);
		}
		
		int num = Arrays.binarySearch(is, 7);//3--》-2=-1 + -1    5--》 -3 = -2 -1
		System.out.println(num);
	}
	
}

-------------

/**
	 * 类
	 * 
	 * 对象： 属性 +方法
	 * 属性：对象的特征描述
	 * 方法:对象具体的操作
	 * 
	 * 属性 --- 全局变量（也叫成员变量）：系统会给一个默认值
	 * 方法 --- 局部变量
	 * 
	 * 
	 * 默认值：
	 * 	引用数据--null
	 * 	整数类型--0
	 * 	浮点型--0.0
	 * 	char--u/0000空格
	 * 	boolean--false
	 * 
	 * String name;
	 * public String name;忽略掉了 [= "xxx"]
	 * 
	 * 全局变量作用域：所有的方法都能去使用
	 * 局部变量作用域：方法本身
	 * 
	 * this :  1.   this.变量  --》调用的是全局变量
	 * 		   2.   this.方法 --》调用本类的方法
	 * 		   3.   this() --> 调用相应的构造方法（this（）且只能放在构造方法的第一句）
	 * 
	 * 
	 * 访问修饰符：
	 * 			private --》 修饰全局变量，变量私有化                  可通过get/set方法去访问该变量
	 * 					--》 修饰的方法，不能通过对象去调用	
	 * set方法
	 * public void set+成员变量名(数据类型  参数){
	 * 	this.成员变量名= 参数;
	 * }
	 * get方法
	 * public 返回值类型 get+成员变量名(数据类型  参数){
	 * 	return this.参数;
	 * }
	 * 
	 * 
	 * 构造方法：与类名相同的方法
	 * 作用：变量初始化
	 * 
	 * {  ====代码块===  应用在初始化}
	 * 
	 *  方法的重载：
	 * 		1.方法名相同
	 * 		2.参数列表不同（内容、顺序）
	 * 		3.与返回值/访问修饰符无关
	 */

-----------------

	/**
	 * 学习方法的重写
	 * 
	 * 重载：
	 * 		1.同一类里
	 * 		2.方法名相同
	 * 		3.参数列表（个数或者类型）不同
	 * 		4.与返回值、访问修饰符无关
	 * 
	 * 重写、复写:
	 * 		当父类的方法无法满足子类的需求时，就需要重写。
	 * 
	 * 重写的规则：
	 * 		1.在子父类关系中的子类
	 * 		2.方法名相同
	 * 		3.跟返回值有关
	 * 		4.访问权限不能比父类的更严格
	 * 		5.参数列表相同
	 * 
	 *   父类  -------子类
	 *   private     public   可以
	 *   public      private  不可以
	 *   
	 *   重载  --vs-- 重写
	 * 
	 */	

-------------------

		/**
		 *  == : 比较的内存地址
		 *  
		 *  Object类的 -- equals： 比较两个对象是否相等
		 *  String类的 -- equals： 比较两个字符串内容是否相等
		 *  
		 *  getClass():返回当前类的详细信息：属于哪个包的哪个类 class com.momo.test01.MyString
		 *  
		 *  hashCode
		 *  
		 *  com.momo.test01.MyString@1581593: getClass + hashCode
		 */

------------------		


		/**
		 * 了解接口
		 * 一个人只能有一个亲爹，但是可以有多个干爹
		 * 
		 * 继承：子类只能继承一个父类
		 * 
		 * 接口的语法：
		 * 
		 *  	1.接口是一个特殊的“抽象类”
				2.接口中的方法必须是抽象方法
				3.接口中的所有方法默认添加public abstract
				4.接口中可以定义属性，默认添加public static final
					工作中通常会定义一个存放常量的接口
				5.接口中不可以包含构造方法、代码块
				6.接口可以定义内部类，内部类不会默认添加任何修饰符(忽略)
				7.接口不能实例化，存在的意义就在于“实现”（除非该类为抽象类）
					接口不是类，没有构造方法，所以不能被实例化
				8.一个类可以实现多个接口!!!（重中之重）
				9.实现接口的类也可以继承别的类
				10.接口之间可以继承
				
				抽象类  -- vs -- 接口（模子）
				
				需求： 1.编写一个父类，要去强制子类实现方法，但是父类里又要有一些功能的方法---抽象类
					  2.编写一个父类，要去强制子类实现方法 --- 接口
				
		 */ 
		 
		 
---------------------


		/**
		 * final:
		 * 
		 * 修饰属性：常量 , 常量名都用大写 ps：PERSON_NAME , 内存位置：常量池、常量区
		 * 
		 * 修饰方法： 不能被重写，不希望子类去修改此方法的功能时
		 * 
		 * 修饰类：不能被继承，成为了最终版的类
		 * 
		 * final --vs-- static
		 * 			
		 */
		 
		 
----------------------

	/**
	 * 	学习内部类
	 * 
	 * 内部类:一个类里面的类
	 * 	学习路线：
	 * 		变量：
	 * 			成员变量（属性、全局变量）
	 * 				实例化变量
	 * 				静态化变量
	 * 			局部变量
	 * 
	 * 		内部类：
	 * 			成员内部类
	 * 				实例化内部类(内部类可以去调用外部类的所有属性和方法)
	 * 				静态化内部类
	 * 			局部内部类
	 * 				匿名内部类
	 */
	 
	 /**
	 * 	匿名内部类：
	 * 		没有名字的内部类，如果说该类只需要创建一次对象且该对象只使用一次，
	 * 		则不需要去创建该类，建议采用匿名内部类的方式，减少类的个数。
	 * 
	 */

-----------------------

java内存分析自己百度去。


------------------------

//		StringBuilder与StringBuffer的用法完全一致，
//		唯一的区别是StringBuffer是线程安全的，而StringBuilder不是线程安全的。
//		所以StringBuilder的性能要比StringBuffer要好。
//		单线程推荐使用StringBuilder，
//		多线程使用StringBuffer。

-------------------------

	/**
	 * 
	 * 基本数据类型包装类：
	 * 
	 * 装箱：基本数据类型 --> 对应的包装类
	 * 拆箱：对应的包装类 --> 基本数据类型
	 * 
	 * 自动装箱：可以直接把一个基本数据类型赋值给包装类
	 * 自动拆箱：可以直接把一个包装类对象，赋值给基本类型
	 * 自动装箱/拆箱：必须在JDK1.5版本之后
	 * 
	 */
	 
	 
	 package com.momo.pack;

public class TestPackKnowledgePoint {

	public static void main(String[] args) {

		Integer i1 = 100;//实际是Integer i1 = Integer.valueOf(100);
		Integer i2 = 100;
		Integer i3 = 200;
		Integer i4 = 200;

		//Integer.valueOf源码如下：
		//	    public static Integer valueOf(int i) {
		//	        assert IntegerCache.high >= 127;
		//	        if (i >= IntegerCache.low && i <= IntegerCache.high)
		//	            return IntegerCache.cache[i + (-IntegerCache.low)];
		//	        return new Integer(i);
		//	    }
		//		在通过valueOf方法创建Integer对象的时候，如果数值在[-128,127]之间。
		//		便返回指向IntegerCache.cache中已经存在的对象的引用；否则创建一个新的Integer对象。

		System.out.println(i1==i2);		//true
		System.out.println(i3==i4);		//false

		Double d1 = 100.0;
		Double d2 = 100.0;
		Double d3 = 200.0;
		Double d4 = 200.0;

		//	    public static Double valueOf(String s) throws NumberFormatException {
		//	        return new Double(FloatingDecimal.readJavaFormatString(s).doubleValue());
		//	    }

		System.out.println(d1 == d2);	//false
		System.out.println(d3 == d4);	//false


		//		Integer Double为什么结果不一样。通俗说：在某个范围内的整型数值的个数是有限的，而浮点数却不是。

		//	注意，Integer、Short、Byte、Character、Long这几个类的valueOf方法的实现是类似的。
		//		　　　　　Double、Float的valueOf方法的实现是类似的。



		Boolean b1 = false;
		Boolean b2 = false;
		Boolean b3 = true;
		Boolean b4 = true;

		System.out.println(b1==b2);		//true
		System.out.println(b3==b4);		//true
		
		//	    public static Boolean valueOf(String s) {
		//	        return toBoolean(s) ? TRUE : FALSE;
		//	    }

		//	    /**
		//	     * The {@code Boolean} object corresponding to the primitive
		//	     * value {@code true}.
		//	     */
		//	    public static final Boolean TRUE = new Boolean(true);
		//
		//	    /**
		//	     * The {@code Boolean} object corresponding to the primitive
		//	     * value {@code false}.
		//	     */
		//	    public static final Boolean FALSE = new Boolean(false);
		
		
		System.out.println("==========next==============");
		
//		谈谈Integer i = new Integer(xxx)和Integer i =xxx;这两种方式的区别。
//
//		　　当然，这个题目属于比较宽泛类型的。但是要点一定要答上，总结一下主要有以下这两点区别：
//		　　1）第一种方式不会触发自动装箱的过程；而第二种方式会触发；
//		　　2）在执行效率和资源占用上的区别。第二种方式的执行效率和资源占用在一般性情况下要优于第一种情况（注意这并不是绝对的）。
		
			Integer a = 1;
	        Integer b = 2;
	        Integer c = 3;
	        Integer d = 3;
	        Integer e = 321;
	        Integer f = 321;
	        Long g = 3L;
	        Long h = 2L;
	         
	        System.out.println(c==d);
	        System.out.println(e==f);
	        System.out.println(c==(a+b));
	        System.out.println(c.equals(a+b));
	        System.out.println(g==(a+b));
	        System.out.println(g.equals(a+b));
	        System.out.println(g.equals(a+h));
		
		/**
		 * 当 "=="运算符的两个操作数都是 包装器类型的引用，则是比较指向的是否是同一个对象.
		 * 而如果其中有一个操作数是表达式（即包含算术运算）则比较的是数值（即会触发自动拆箱的过程）。
		 * 另外，对于包装器类型，equals方法并不会进行类型转换。
		 * 
		 * 第一个和第二个输出结果没有什么疑问。第三句由于  a+b包含了算术运算，
		 * 因此会触发自动拆箱过程（会调用intValue方法），因此它们比较的是数值是否相等。
		 * 而对于c.equals(a+b)会先触发自动拆箱过程，再触发自动装箱过程，也就是说a+b，
		 * 会先各自调用intValue方法，得到了加法运算后的数值之后，便调用Integer.valueOf方法，再进行equals比较。
		 * 同理对于后面的也是这样，不过要注意倒数第二个和最后一个输出的结果（如果数值是int类型的，
		 * 装箱过程调用的是Integer.valueOf；如果是long类型的，装箱调用的Long.valueOf方法）。
		 */
		
		
		
		
	}
}


--------------------------

//Java获取随机数的3种方法
//方法1
//(数据类型)(最小值+Math.random()*(最大值-最小值+1))
//例:
//(int)(1+Math.random()*(10-1+1))
//从1到10的int型随数
//方法2
//获得随机数
//for (int i=0;i<30;i++)
//{System.out.println((int)(1+Math.random()*10));}
//(int)(1+Math.random()*10)
//通过java.Math包的random方法得到1-10的int随机数
//公式是:最小值---最大值（整数）的随机数
//（类型）最小值+Math.random()*最大值
//方法3
//Random ra =new Random();
//for (int i=0;i<30;i++)
//{System.out.println(ra.nextInt(10)+1);}
//通过java.util包中的Random类的nextInt方法来得到1-10的int随机数
// 
//生成0到1之间的任意随机小数：
//生成[0,d)区间的随机小数，d为任意正的小数，则只需要将nextDouble方法的返回值乘以d即可。
//[n1，n2]
//也就是 ra.nextDouble() * (n2-n1)+n1


----------------------------


集合自己百度

-----------------------------
异常：

	/**
	 * 错误(Error)：
	 * JVM系统内部错误或资源耗尽等严重情况－属于JVM需要负担的责任这一类异常事件无法恢复或不可能捕获，
	 * 将导致应用程序中断。
	 * 
	 * 解决方法：优化代码，使得Error错误几率减少
	 * 
	 * OutOfMemoryError：内存溢出
	 * StackOverflowError:栈溢出
	 */
	 
	 
	 /**
	 * Exception：异常
	 * 其它因编程错误或偶然的外在因素导致的一般性问题。
	 * 我们自身能处理的异常
	 * 
	 * 一般性异常：
	 * RunTimeException：非受检异常--不要求强制处理异常
	 * 
	 */
	 
	 
	/**
	 * 
	 * 异常机制：
	 * 
	 * 1.error（错误）:我们要尽可能的优化代码
	 * 
	 * 2.Excepton（异常）：编码不严禁
	 * 		1.运行时异常RunTimeException -- 非受检性异常：java不要求强制处理异常
	 * 		2.一般性异常-- 受检性异常：强制要求处理异常
	 * 
	 * 3.处理异常的方法：
	 * 		1. try（发生异常的代码）-catch（捕获异常的类型和对象）{处理异常的代码}-多重catch -finally{总会被执行} 
	 * 		2. throws ： 修饰方法（放在方法名后面） --- 抛出（多个）异常
	 * 		3. throw  ：抛出单个异常
	 * 
	 * 4.自定义异常类
	 * 
	 * 用法：1.语法
	 * 		 2.不建议自定义异常类
	 * 
	 * 工作中：try -catch  和  throws
	 * 
	 * 
	 */
	 
----------------------


file api比较简单 自己看

----------------------

IO流


	/**
	 * 1.字节流：
	 * OutputStream 输出流：抽象类  --- write(写)
	 * InputStream 输入流：抽象类  ---read(读)
	 * 使用其子类 --- FileOutputStream FileInputStream
	 * 
		2.字符流
			Reader --- Writer   抽象类
			InputStreamReader --- OutputStreamWriter  转换流
			FileReader --- FileWriter 文件字符流
			BufferedReader --- BufferedWriter  字符缓冲流
			
			
		3.对象流
		
		重要概念：序列化与反序列化
		
	
		 * Serializable:序列换接口 --- 标记接口
		 * 
		 * 类结构
		 * 
		 * 欺骗JVM
		 * 
		 * transient:透明-->不把被修饰的属性写入的文件里
		 * static修饰属性不能存入流中
		 
		 4.随机访问流
		 RandomAccessFile
		 
		 了解其断点续传的功能
		 
		 5.标准流
		 System.in  System.out
		 
		 6.打印流
		 PrintStream  PrintWriter
		 
		 7.内存流
		 ByteArrayOutputStream 
		 经典考点：内存流关闭无效
	 
	 */

------------------------

线程

	/**
	 * 经典面试题：
	 * 请问当我们编写一个单纯的main方法时，
	 * 此时该程序是否为单线程的？为什么？
	 * 	public static void main(String[] args) {
		
		System.out.println("HelloWorld!!!!");
		
		}	
	 * 
	 * 肯定是多线程的
	 * 垃圾回收器
	 * 
	 */
	 
	 掌握多线程安全
	 
	 线程安全---加锁 
	 *  （1）同步代码块
	 *  （2）同步方法
	 *  （3）对象的互斥锁----用Lock接口的实现类（常用ReentrantLock） ----Lock lock = new ReentrantLock();
	 *  通过创建任务(Runnable)的方式应用锁
	 *  通过集成Thread的方式应用同步锁
	 *  分析加锁的关键点： 1.锁的范围   2. 锁对象是同一个对象
	 *  Runnable方式和Thread实现同步锁的区别			那些需要static修饰
	 
	 
	 	//总结：
		//1.守护线程---为主线程默默服务的线程，当主线程执行接收，守护线程跟着结束
		//2.线程池----优化线程的创建与结束； 3中线程池的使用方式：
		   //2.1. 通过单线程方式创建线程池对象
		   //2.2. 通过固定的线程数创建线程池对象
		   //2.3. 通过创建缓冲线程池对象的方式去执行任务
		//3.网络编程：（网络编程+IO+多线程）
		   //3.1. 网络的层次模型结构（了解）7层---4层模型
		   //3.2. 网络编程的3要素：ip、port、协议
		//4.网络编程应用：了解INetAddress类、Tcp(socket)编程（非常重点）
		//4.1. 熟悉TCP编程中ip、port的设置
		//4.2. 熟悉服务器端监听、客户端建立连接的过程
		//4.3. IO流在网络编程中的应用
		
		
	/**
	 * 
	 * 1.服务器与客户端之间的数据传输
	 *   1）服务器----指定一个socket进行监听客户端的连接请求
	 *   2）客户端----连接成功后，给服务器发送信息--socket的write基础流发送、字符缓冲流发送
	 *   3）服务器----接收客户端的数据---socket的read基础流接收、字符缓冲流接收
	 *   4）通过多线程的方式，将服务器与客户端的收与发分开，实现流畅信息的发送与接收
	 * 
	 * 2. 聊天室程序的应用
	 *   1）服务器----循环分配socket进行监听多个客户端的连接请求，并用集合存储服务器单独给每个客户端的线程
	 *   2）客户端----将客户端的发送与接收线程分开，便于数据的传输
	 *   3）客户端给服务器发送数据、那么服务器读取并转发给发送者、
	 *    （群聊：转发给除自己以外的客户）、（私聊：转发给指定的客户）
	 *   4）客户端的读取线程，将转发信息进行读取
	 *   5）退出、关闭io流、socket通道；将退出信息转发给其他客户
	 * 
	 */
	 
	 
----------------------

XML解析
DOM SAX PULL

JSon解析

json解析的3中方式：json gson JSON(FastJson) 
		1.最基本的方式（jsonObject、jsonArray）
		2.Gson的解析方式：实例化Gson对象，对象调用Fromjson、toJson
		3.Fast的解析方法：通过JSON类调用parseObject、parseArray；toJsonString

XML与json：
 * XML：   可扩展的标记语言，主要用于存储数据
 * json：轻量级数据交互格式，主要用于传输数据 
 
 
----------------------

正则表达式

了解其规则即可

----------------------

SQL语句

----------------------

反射
		
		
----------------------

		 
		 
		 


JAVA基础面试题 

01 面向对象的基本特征有哪些？分别解释；
·面向对象的四大特征为：封装、继承、多态、抽象；
·封装是将业务相近的、可重用的属性和方法封装为类，进而通过类的对象实例去调用；
·继承的目的是对现有类进行扩展和修改，扩展就是增加新的属性与方法，修改是指通过覆写父类方法实现自身的差异化实现；
·多态是指同一父类或接口可以有多个不同的子类或实现类，外界在调用时可以不必关心子类的具体实现，而只需要统一调用父类方法来实现业务逻辑；
·抽象是指父类或接口定义一个方法，但是不去做具体实现，而是将其定义为抽象方法，留待子类去做具体实现；
·抽象是多态的基础；



02 何为同步？何为异步？何为异步回调？
·同步/异步指的是任务间的时间先后关系；
·假设有A、B两个彼此独立的任务：
	如果B任务要在A任务结束后才能触发，就称这两个任务是同步的；
	如果A、B彼此互不干扰，并发执行，就称它们之间是异步的（步调不一致，各走各的）——显然异步是要借助于线程的；
·异步回调是指：工作线程事先持有一个接口实例（通过传参、setter、构造方法均可），并在任务完成后去回调这个实例中的方法，即为异步+回调；
·异步回调的场景举例：
	主线程开启一条工作线程下载文件，并给这条线程设置一个回调接口（其实现为弹窗提示下载完成），之后主线程继续执行；
	下载线程在下载完毕后回调当初设置好的接口方法；
	主线程弹窗提示下载完成；



03 数组与List、Map、Set这几种集合类型有何异同？
·数组可以存取基本或对象类型的数据；数组是集合的底层实现，因此效率优于集合；但其长度是固定的，且数据类型必须是单一的，因此易用性不足；
·集合只能存取对象型数据；
·List，列表，有序（可按位置进行存取），对象内容可以重复；
·Set，集合，无序，对象内容不重复；
·Map，映射，以键值对的方式存取数据；



04 比较HashMap和HashTable的异同；
·HashMap的存取是异步的，HashTable的存取是同步的，——因此HashMap效率较高，但HashTable是线程安全的；
·HashMap允许有空键值，而HashTable不允许；
·HashMap查询是否存在键值的API为：containsValue()和containsKey()，HashTable为contains()；



05 何为线程安全？
·【线程安全】就是指一个对象不能被多个线程并发修改；
·一个对象如果能够被多个线程并发修改，它就不是线程安全的；



06 你熟悉SQL语句么？如何实现从【全年级学生成绩表】中查出各班的男同学的平均分、忽略平均分不及格的班级、按降序排列、并取其中的前三名？
·当然至少是比较熟悉的；
select 
avg(score) s,class
from students
where male = 1
group by class
having s > 60
order by s desc
limit 3
·group by、limit、常用的数据库函数都是常用的比较重要的SQL语法；



07 说说Socket通信的原理和一般步骤；
·又称套接字；
·基于TCP/IP协议；//（所以访问地址是IP+端口）
·基于长连接；//（Http基于短连接，返回数据后立即断开连接）
·客户端通过指定IP与端口，建立与服务端的连接；
·ServerSocket阻塞监听连接请求，并为每一个成功连接的客户端Socket建立一条独立的线程；
·连接建立后，服客两端通过输入输出流相互发送数据；
·通信结束后，断开Socket连接(disconnect)；



08 你熟悉哪些常用的设计模式？
·单例（控制对象的数量）：
·工厂（统一管理对象的创建，防止无度的new对象实例）：BitmapFactory
·适配器（将数据映射为对象）：BaseAdapter
·观察者（数据变化时通知机制）：OnClickListener
·构造器（一条龙的setter，代码简洁）：AlertDialogBuilder
·组合（同种类的实例相互嵌套持有）：ViewGroup

为什么要用设计模式
提高程序执行的效率
设计模式可以帮助我们改善系统的设计，增强系统的健壮性、可扩展性，为以后铺平道路。

反对过度使用设计模式



09 反射的原理是什么？
·运行时动态装配类的实例，并调用其属性和方法；
·首要步骤是获得class对象，可以通过类名或实例的getClass()方法两种手段获取；
·一旦得到class对象，就可以访问其中的所有属性和方法，包括私有属性和方法；
·反射机制在各种框架中被广泛使用；
·JNI中C调用JAVA也是通过反射机制实现的；



10 你了解注解的原理么？
·注解可以作用于类、属性或方法上；
·注解类中可以声明一系列相关方法，使用注解时以参数形式定义这些方法的返回值；
·运行时“解读类”能够通过调用注解类中声明的方法，获取其作用对象中注入的值，进而进行相应的业务处理；
·注解对象的“解读”工作，也是通过反射机制实现的；
·【注解 + 反射】在各种框架中被广泛使用；



11 为什么要使用泛型？
·泛型的作用是保证类型安全；
·任何想要声明类型（方法参数类型，方法返回值类型，属性类型）的地方，如果不确定类型，可以标记为泛型；
·创建泛型类对象（或继承泛型类）时，为保证类型安全，可以对泛型做具体类型声明；
·在使用实例或子类时，原泛型的位置必须使用具体声明的类型，否则就称之为类型不安全，将通不过编译；
·例如ArrayList<T>，当data = new ArrayList<String>()时，data中能且只能放String类型对象，否则会编译报错；