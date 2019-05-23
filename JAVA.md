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