#### JAVA

>```java
>Scanner input = **new** Scanner(System.**in**);
>​	int one = input.nextInt();
>```
>
>

> 表达式:  必须赋值
>
> ​     int sum = age1 +3;
>
> ​     int sum1 = age1 + age2;
>
>   System.out.println(sum)
>
> 顺序
>
>   ( ) 可以干预顺序
>
>    int count = 24 * 60 * 60  方便修改   
>
> i++ 
>
> 字符串连接符  + 

##### for

> for(int i=0;i<3;I++){
>
> ​	System.out.println("i="+i)
>
> }
>
> ```java
> for(int i = 0;i<3;i++) {
> 			System.out.println("请输入第"+(i+1)+"个数");
> 		}
> 
> ```
>
> `对比 (i+1) 和不加的区别:`
>
> ```java
> 
> int sum = 0;
> 		int sum2 = 0;
> 		for (int i = 0; i < 6; i++) {
> 			sum = sum + (i+1);
> 			System.out.println("sum="+sum+",i="+i);
> 		}
> 	for (int i = 0; i < 6; i++) {
> 			sum2 = sum2 + i;
> 			System.out.println("sum2="+sum2+",i="+i);
> 		}
> i 的次数是不变的; 所以加1 的结果是多加了一次.
>   
> ```
>
> `随机数`
>
> ```java
> 1.先*10,在取整; 结果是 1~10 的随机数
> for (int i = 0; i <5; i++) {
> 			double num =Math.random();
> 			double num1 =(int)Math.random()*10;
> 			System.out.println("num="+num);
> 		}
> 		1.1
> 		for (int i = 0; i <5; i++) {
> 			int num1 =(int)(Math.random()*10);
> 			System.out.println("num1="+num1);
> 			
> 		}
> 2.0
> 		//n+1表示 0~n 的随机数   ,0~7
> 		for (int i = 0; i <5; i++) {
> 			int num2 =(int)(Math.random()*8);
> 			System.out.println("num2="+num2);
> 			
> 		}
> 		
> 2.1 //框定范围  +1 或更大的数 ,1~8的数
> 		for (int i = 0; i <5; i++) {
> 			int num3 =(int)(Math.random()*8)+1;
> 			System.out.println((i+1)+":num3="+num3);
> 					
> 		}
> 				
> ```
>
> 案例循环求和\平均数的案例
>
> ```java
> // 案例 
> 		Scanner input = new Scanner(System.in);
> 		int sum1 = 0;
> 		for(int i = 0; i<3;i++) {
> 			System.out.println("请输入第"+(i+1)+"个数");
> 			int a = input.nextInt();
> 			sum1 = a +sum1;1
> 		}
> 		System.out.println(sum1);
> 		int avg = sum1/3;
> 		System.out.println("平均值"+avg);
> 	}
> 
> ```
>
> 

#### 数组

> 元素类型 保持一致
>
> ```java
> int [ ] arr    //声明
> int [ ] arr = new int[5]  ;
> arr[0] = 1;  //赋值
> arr[1] = 2;arr[2] = 3;arr[3] = 4;arr[4] = 5;
> //注意数组下标越界
> for(int i = 0;i<arr.length;i++){   // 给数组赋值 赋值 0 是良好习惯
> 	arr[i] = 0;
> }
> for(int i = 0;i<arr.length;i++){
> 	System.out.println(arr[i]);//读取
> }
> ```
>
> 

####类

> ###1.什么是类:
>
> ​	是一种数据结构,是属性(变量)和方法(过程,函数)的集合
>
> 方法 = 程序逻辑(语句)的集合
>
> #####2.类的来龙去脉;
>
> ​     从面相过程—>面向对象 
>
> ​     面向对象可以理解成 多个面向过程的集合 ,类和类的关系(多态继承)
>
> 
>
> 类的声明   
>
> ​      可见范围修饰词  public     class 类    Student 名字 (首字母大写)  {方法 变量}
>
> > 其他的修饰词:
> >
> >  public   
> >
> > protected
> >
> > friendly
> >
> > private
>
> ####3.类这么写?
>
> ​	逻辑代码是放在 main 里面, 
>
>  	类里是声明语句,不能偶 for 和 if
>
> `Student stu2 = new Student();`   (Student()  构造器 同类名一直   ) 像数组
>
> 驼峰命名 
>
> ​     

##### 方法的传参和调用

> 1 参数 和返回值
>
> 2 方法的调用
>
> 3 静态方法
>
>    - 就是调用类不用实例化
>      - 在类里 添加 static   public static int add(int a,int b)
>      - 静态方法是属于类方法
>
> 字符比较 
>
> ​     equals("+")   ,不能用 "+"  == "+"
>
> `java 重点是封装` :就行一个黑盒子
>
> ```java
> public static void main(String[] args) {
> 		// 实例化对象
> 		MyMath math = new MyMath();
> 		int a = 3,b=5;
> 		int res = math.add(3, 5);
> 		System.out.println("和等于"+res);
> 		int res1 = math.add(a, b);
> 		System.out.println("和等于"+res1);
> 		int res2 = math.minus(a, b);
> 		System.out.println("差等于"+res2);
> 	}
> ```
>
> ==静态方法使用==
>
> ```java
> 不用实例化对象
> 在类的方法里 添加 static 
> public int add(int a,int b)  
> public static int add(int a,int b) //类里面的修改
> //下面是主函数
>   int res = MyMath.add(a,b); // 可以把实例的变量直接变成类名, 静态方法属于类
> 	System.out.println("和等于"+res);
>    
> ```
>
> `方法里面调方法`
>
> ```java
> public class MyMath {
> 	public static int calc(int a,int b,String op) {
> 		int res = 0;
> 		if(op.equals("+")) {  //op=="+" 字符串不能这么比较
> 			res = add(a,b); //调用的方法必须加的 staitc, add 前面也可以加类名
> 			
> 		}else if(op.equals("-")) {
> 			res = minus(a,b); //也可是方法不加 static 
> 		}
> 			
> 		return res;
> 	}
>   ---
> 	public static int add(int a,int b) {
> 		int res = a + b;
> 		return res;
> 	}
> 	public static int minus(int a,int b) {
> 		int res = a - b;
> 		return res;
> 	}
> 	public int mul(int a,int b) {
> 		int res = a * b;
> 		return res;
> 	}
> 	public int div(int a,int b) {
> 		int res = a / b;
> 		return res;
> 	}
> ```
>
> ```java
> //main 里调用
> int res = MyMath.calc(a, b, "+");
> 		System.out.println("和等于"+res);
> ```
>
> 

#### 类的使用

> 类的演变
>
> 1. 刚开始是一行一行的写
>
> 2. 同样的代码,在不同的地方用,为了减少复制粘贴
>
> 3. 从面相过程->面向对象
>
>      过程 就是一个个的方法
>
> 4. 后来发现过程也不够用了,   
>
> 5. 面向对象出现
>
>     c 的结构就是累的雏形
>
> 6. 类 就是方法和属性的集合, 有产生了继承\多态的关系
>
> 7. 一个文件包含一个类
>
> ```java
> package spl.filedemo;   //包路径   文件在那个包里 
> public class Student{//public(可见范围修饰词) class(关键字,类声明) 类名
>   									//  类名尽量开头大学, class 不区分大小写
>   										// private  protected friendly 其他访问范围 
>                       //public 等等于没有限制访问
>   int age = 0; //年龄属性
>   String name = "";
>   String[] hobby = new String[3]; //爱好属性
>   //这是声明代码 不能有逻辑代码 不能有 if for 等
>   // 逻辑语句只能在方法中,类里只有变量声明
>   public int age = 0;  //可以加 public 表示谁都可以过来看
>   
>   
>   //方法
>   public void sayHello(){
>     //逻辑代码  
>     //可以使用上面定义的声明
>     System.out.println(){
>     	System.out.println(name+""+age) //+可以换行
>     }
>   }
> }
> ```
>
> main入口
>
> ```java
> //声明一个学生类   
> //stu 是对象,Student类
> {
> Student stu = new Student();  //Student 要一样 后面是构造器
> stu.age = 18;
> stu.hobby[0] = "跳舞";
> stu.hobby[1] = "rap";
> stu.hobby[2] = "篮球";
> stu.sayHello();
>   
>  // Student类 stu2 对象
> Student stu2 = new Student();
> stu2.age = 18;
> stu2.hobby[0] = "跳舞1";
> }
> 
> ```
>
> 
>
> 

#### Java图像编程框架

> 继承 extends 
>
> JFrame 窗口     `-- 口  X`
>
> game.setVisible  是在调用 JFrame 的方面对么,因为继承父类?
>
> 构造器具体的意义是啥?和普通定义的方法有何不同?
>
> **public** **void** setup() 和 **public** **void** draw() 是系统自带的方法么? 一定要写在 Game 类里么?
>
> Graphics 是 java 自带的包, 用来做什么?
>
> 为啥线程对象也能和类 一样实例化?  
>
> t = **new** Thread(**this**); 这句话的 this 实在理解不了?线程是啥?
>
> 不休眠也可以?就是把 20 改成 0.
>
> paint(Graphics g)无法理解. 为啥自己传自己
>
> 为啥返回 Game类,创建方法  public void setup(){} ,不可以 直接在GamePanel 里创建?
>
> **this**.game.setup();和t = **new** Thread(**this**); 这俩句的关系?
>
> **public** **void** paint(Graphics g) 里面的传参 g 是啥?
>
> ```java
> //出窗口
> public Game() {
> 		this.setTitle("java绘图");//设定标题
> 		this.setSize(400,300);//设定宽高,包含标题
> 		this.setLocation(200, 200);//位置
> 		this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);//关闭了x就关闭了程序
> 	
> 	}
> public static void main(String[] args) {//静态方法是属于类,看成外面的
> 		// TODO Auto-generated method stub
> 		Game game = new Game();
> 		game.setVisible(true); //让窗体显示出来
> 	}
> 
> ```
>
> `内侧的画板`
>
> ```java
> //面板也是独立的类,  GamePanel
> //先继承 extends JPanel implements Runnable
> //会产生未实现的方法
> @Override
> 	public void run() { }
> //写构造器:
> public GamePanel( ) {}  // 应用窗体类 ,复杂开始了
> //定义一个窗体类 Game game; 传进构造器
> //添加 this 
> //返回 Game类,创建方法  public void setup(){}
>   //Graphics 是颜料
> // GamePanel引用 Game 的setup()方法
> //开启一个线程  Thread t  声明线程对象
> //实例化 t 对象 
> //当 t.start 启动 会自动调用 run()方法
> // 在线程 run 里写死循环
> //线程要每秒不停的刷新页面 ,配合死循环,就是更新
> //休眠 20 毫秒  ,
> 		try {
> 				Thread.sleep(sleep);//停顿 20 毫秒
> 			}catch(InterruptedException e) {
> 				e.printStackTrace();
> 			}  //休眠保护
> //1000 / 20  就是 50 帧  30~60 正常   低于 30 卡
> //repaint  重绘面板
> //paint 方法 实现  
> //在 paint 方法了调用 draw()方法
> //在 Game类 里引入 GamePanel panel;
> //panel = new GamePanel(this);
> //给窗体添加面板组件 this.add(panel); 
> ```
>
> ```java
> public class GamePanel extends JPanel implements Runnable{
>   Game game;
>   Thread t;
>   public GamePanel(Game game){
>     this.game = game;   //game=g  this.game 是指2行的属性 ,等号后面的传参
>   	this.game.setup();
>     t = new Thread(this);
>     t.start();//启动
>   }
>   @Override
> 	public void run() {
>     try {
> 				Thread.sleep(sleep);//停顿 20 毫秒
> 			}catch(InterruptedException e) {
> 				e.printStackTrace();
> 			}  //休眠保护
>   }
> }
> ```
>
> `总结`
>
> > 1. 创建窗口   Game 类
> > 2. 创建画板 GamePanel 类
> > 3.  GamePanel 类生成 GamePanel 类方法,里面引入Game 类和线程
> > 4.  run() 线程 和 paint() 描绘引入 draw()
> > 5. 在game 类绘制 draw()的图形    

#### 14 oop

> (Object Oriented Programming，OOP，[面向对象程序设计](https://baike.baidu.com/item/面向对象程序设计/24792)）是一种计算机编程架构就是一种方法
>
> oop 对开发者省事的,开发者不用 oop 也行,可能性能还高.
>
> 对应 cpu 还增加了步骤, 继承 多态啊...
>
> 对用户没感觉
>
> oop 也有优点,在复杂的项目中
>
> ![image-20190531115050038](/Users/nj/Library/Application Support/typora-user-images/image-20190531115050038.png)
>
> 

> 数组初始化:  动态 和静态
>
> int[] arr = new int[3]    //动态  指定长度  
>
> int[ ] arr = new int[]{1,2,3};   //静态 指定内容
>
>    int[arr] = {1,2,3}  // 简化 静态

>![image-20190602093634532](/Users/nj/Library/Application Support/typora-user-images/image-20190602093634532.png)
>
>![image-20190602101952034](/Users/nj/Library/Application Support/typora-user-images/image-20190602101952034.png)

> 对象 
>
>    类封装方法

>
>
>![image-20190602141615534](/Users/nj/Library/Application Support/typora-user-images/image-20190602141615534.png)
>
>![image-20190602143939201](/Users/nj/Library/Application Support/typora-user-images/image-20190602143939201.png)
>
>![image-20190602152221267](/Users/nj/Library/Application Support/typora-user-images/image-20190602152221267.png)
>
>![image-20190602153021640](/Users/nj/Library/Application Support/typora-user-images/image-20190602153021640.png)
>
>![image-20190602153541035](/Users/nj/Library/Application Support/typora-user-images/image-20190602153541035.png)
>
>

> ### 孙老师 16 继承
>
> ​    类与类的的重复使用---代码重用
>
> ​		多态(重点)
>
> ​      继承只能是公开的 
>
> ​      private int z ; 私有的不能被继承
>
> ​		不能同时继承多个父亲:`**class** C **extends** B,A{}  `  ,不支持多继承
>
> ​      继承可以理解为扩展 , 子比父强
>
> ​      类型的大小  和功能的大小 
>
> ​      人是属于动物,但不能动物属于人, 程序员 医生是人的子类,   java 程序员是    程序员的子类
>
> ​       `重写`
>
> ​         儿子继承了爸爸的方法,对其进行了改动 ,必须是`方法的签名相同:返回值 方法名  参数列表`
>
> ​		