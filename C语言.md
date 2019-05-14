###c

```c
int * p = (int*)malloc(4)    //8 个字节
```

p 是静态,只能系统释放,  后面的可以自己释放 用 free (p)



动态

```c
int a[5]
pArr = (int *)malloc(4 * len);  //动态的类似一维数组
for (i=0;i<len;++i)    //赋值
  scanf("%d",&pArr[i])
 for(i=0;i<len;++i)     //输出
   printf("%d\n",pArr[i])
   
 free(pArr) //释放
  
```

> pArr 指向的是前 4 个字节,  pArr+1 是指向的 后 4 个字节
>
> a[0]也是指向 前 4 个字节
>
> pArr[0]也是指向 前 4 个字节
>
> 动态的 pArr 和静态的 a  , 使用效果是一样的,
>
> 系统定义的函数结束释放, 用户自己定义的,可以随时 free
>
> `realloc (pArr ,100)  动态添加空间`  不是重点了解

##### 144 动态内存和静态内存的区别

   进栈 和出栈

> f(){
>
> ​	A
>
> ​       g(5)
>
> ​      b
>
> }
>
> ![image-20190512183431025](/Users/nj/Library/Application Support/typora-user-images/image-20190512183431025.png)
>
> mallco  是在 堆里面分配  , 栈是存储结构,   堆是分配内存的排序方式
>
>  用压栈的方式存储空间,
>
> `排序` 重要  
>
> 堆没压栈和出栈,可以跨函数使用

#####145 多级指针

> ```c
> int i = 10;
> int * p = &i;
> int **q = &p;
> int ***r = &q
> 
> ***r = i
> &p 是 int **类型
> 
> 
> ```
>
> 

#####148静态变量不能跨函数使用

> ```c
> # include <stdio.h>
> 
> void f(int ** q) //q是个指针变量，无论q是什么类型的指针变量，都只占4个字节
> {
> 	int i = 5;
> 	//*q等价于p  q和**q都不等价于p
> 	//*q = i; //error 因为*q = i; 等价于 p = i; 这样写是错误的
> 	*q = &i;  // p = &i;
> }
> 
> int main(void)
> {
> 	int *p;  //13行
> 	
> 	f(&p);
> 	printf("%d\n", *p);  //16行  本语句语法没有问题，但逻辑上有问题
> 
> 	return 0;
> }
> ```
>
> 

##### 149动态内存可以跨函数使用

> ```c
> # include <stdio.h>
> # include <malloc.h>
> 
> void f(int ** q)
> {
> 	*q = (int *)malloc(sizeof(int)); //sizeof(数据类型) 返回值是该数据类型所占的字节数
> 			//等价于 p = (int *)malloc(sizeof(int));
> 	//q = 5; //error
> 	//*q = 5; //p = 5;
> 	**q = 5; //*p = 5;
> }
> 
> int main(void)
> {
> 	int * p;
> 
> 	f(&p);
> 	printf("%d\n", *p);
> 	
> 	return 0;
> }
> ```
>
> 

##### 151 为什么需要结构体

> ```c
> # include <stdio.h>
> 
> struct Student
> {
> 	int age;
> 	float score;
> 	char sex;
> };
> 
> int main(void)
> {
> 	struct Student st = {80, 66.6, 'F'};	
> /*	int age;
> 	float score;
> 	char sex;
> 	int age2;
> 	float score2;
> 	char sex2;
> */
> 	return 0;
> }
> ```
>
> `struct` 是结构体定义
>
> > **为什么需要结构体**
> >
> > 为了表示一些复杂的事物，而普通的基本类型无法满足实际要求。
> >
> > 
> >
> > **什么叫结构体**
> >
> > 把一些基本类型数据组合在一起形成的一个新的复合数据类型。
> >
> > 
> >
> > **

##### 152 如何定义结构体

>```c
>如何定义结构体
>
>​	3种方式：
>
>// 第一种  只是定义了一个新的数据类型，并没有定义变量   推荐采用1
>
>**struct** **Student**
>
>{Int age;
>
>Float score;
>
>Char sex;
>
>**};**  
>
>**//****第二种**
>
>  **struct** **Student**
>
>{Int age;
>
>Float score;
>
>Char sex;
>
>} st;
>
>**//** 第三种
>
>**struct**
>
>{Int age;
>
>Float score;
>
>Char sex;
>
>} st;
>```
>
>
>
>

#### 154 怎样使用结构体变量-赋值和初始化

> **怎样使用结构体变量**
>
> - 赋值和初始化
>   - 定义的同时可以整体赋值。
>   - 如果定义完之后，则只能单个赋初值。
>
> - 如果取出结构体变量中的每一个成员{重点}
>
>   1 . 结构体变量名.成员名
>
>   2 . 指针变量名->成员名 （更常用）
>
>     它会在计算机内部转化成 (\* 指针变量名).成员名  的方式来执行。
>
>     所以两者是等价的。
>
>   ```c
>   例子:
>    Struct Student{
>      Int age;
>      Float score;
>      Char sex;
>    };
>   Int main(void){
>     Struct Student st = {80,66.6f,"F"};////初始化定义的时候赋值  66.6在C语言中默认是double类型，如果希望一个实数是float类型，则必须在末尾加f或F, 因此66.6是double, 66.6f或66.6F是float
>     Sturct Student st2;
>     st2.age = 10;
>     st2.socre = 88;
>     st2.sex = 'F';
>     
>     Struct Student *pst = &st; // &st 不能写成 st 
>   	Pst->age = 88; // 通过结构体指针变量
>     st2.age = 10;  // 另一种方式
>   	printf("%d %f\n", st.age, pst->score);
>   
>   }
>   
>   ```
>
>   > 理解：
>   >
>   > 1.  `pst->age 会在计算机内部转化成 (*pst).age `的方式来执行,没有为什么，这就是->的含义，这也是一种硬性规定。*
>   >
>   > 2. 所以` pst->age 等价于 (*pst).age` 也等价于` st.age`
>   >
>   > 3.   pst->的含义：
>   >
>   >    pst 所指向的那个结构体变量中的`age这个成员`。 结构体变量的大小略大于其内部成员类型所占字节数之和。试：sizeof(struct) 若想通过函数对主函数结构体变量进行修改，则主函数必须发送地址，外函数定义指针结构体变量，通过外函数内部语句完成对变量的修改。 而仅想输出、读取操作，则不用传地址，定义指针过程。

#### 159 通过函数对结构体完成输入输出

> ```c
> /*
> 	2009年11月24日9:17:43
> 	通过函数完成对结构体变量的输入和输出
> */
> 
> 
> # include <stdio.h>
> # include <string.h>
> 
> struct Student
> {
> 	int age;
> 	char sex;
> 	char name[100];
> }; //分号不能省
> 
> void InputStudent(struct Student *);
> void OutputStudent(struct Student ss);
> int main(void)
> {
> 	struct Student st;  //15行
> 
> 	InputStudent(&st); //对结构体变量输入  必须发送st的地址
> //	printf("%d %c %s\n", st.age, st.sex, st.name);
> 	OutputStudent(st); //对结构体变量输出  可以发送st的地址也可以直接发送st的内容
> 
> 	return 0;
> }
> 
> void OutputStudent(struct Student ss)
> {
> 	printf("%d %c %s\n", ss.age, ss.sex, ss.name);
> }
> 
> void InputStudent(struct Student * pstu) //pstu只占4个字节
> {
> 	(*pstu).age = 10;
> 	strcpy(pstu->name, "张三");
> 	pstu->sex = 'F';	
> }
> 
> /*
> //本函数无法修改主函数15行st的值 所以本函数是错误的
> void InputStudent(struct Student stu)
> {
> 	stu.age = 10;
> 	strcpy(stu.name, "张三");  //不能写成 stu.name = "张三";
> 	stu.sex = 'F';
> }
> */
> ```
>
> 

#### 160结构体应该发内容还地址

> ```c
> 结构体：应该发送地址还是内容
> 设计函数的目的：必须考虑 功能单一， 还要考虑安全因素
> C++中指针前可加const 则只能读而不能修改其指向的变量。
> 指针的优点：
>   耗用内在小（4字节）
>   快速传递数据
>   执行速度快。
> 因此：推荐使用结构体变量作为函数参数来传递
> 
> /*
> 	2009年11月24日9:17:43
> 	示例:
> 		发送地址还是发送内容
> 	目的:
> 		指针的优点之一:
> 			快速的传递数据，
> 			耗用内存小
> 			执行速度快
> */
> 
> 
> # include <stdio.h>
> # include <string.h>
> 
> struct Student
> {
> 	int age;
> 	char sex;
> 	char name[100];
> }; //分号不能省
> 
> void InputStudent(struct Student *);
> void OutputStudent(struct Student *);
> int main(void)
> {
> 	struct Student st ;  //15行
> 	//printf("%d\n", sizeof(st));
> 
> 	InputStudent(&st); //对结构体变量输入  必须发送st的地址
> 	OutputStudent(&st); //对结构体变量输出  可以发送st的地址也可以直接发送st的内容 但为了减少内存的耗费，也为了提高执行速度，推荐发送地址
> 
> 	return 0;
> }
> 
> void OutputStudent(struct Student *pst)
> {
> 	printf("%d %c %s\n", pst->age, pst->sex, pst->name);
> }
> 
> void InputStudent(struct Student * pstu) //pstu只占4个字节
> {
> 	(*pstu).age = 10;
> 	strcpy(pstu->name, "张三");
> 	pstu->sex = 'F';	
> }
> 
> ```
>
> 

#### 162 结构体变量的运算

> ```c
> 结构体变量的运算
>    不能加减乘除操作，只能相互赋值。
> 例如： struct Student
> 	{	
> 		Int age;
> 		Char sex;
> 		Char[100];
> };
> Struct Student str1, str2;
> Str1 = str2 /  str2 = str1 ;  都是正确的。
> 
> ```
>
> 

##### 163 冒泡排序

> ```c
> void sort(int *a len){
>   int i,j,t;
>   for (i=0;i<len-1;i++){
>     for(j=0;j<len-i-1;i++){
>       if(a[j]>a[j+1]){   //>表示升序   <表示降序
>         t = a[j];
>         a[j] = a[j+1];
>         a[j+1] = t;
>       }
>     }
>   }
> }
> int main(viod){
>   int a[6] ={10,2,5,3,-7,0};
>   sort(a,6);
>   for(i=0;i<6;++i){
>     printf("%d",a[i]);
>   }
>   printf("\n");
>   return 0;
> }
> ```
>
> 

#### 164  学生管理系统

> 共3 部分 
>
>   1 输入学生信息    2 排序    3   输出学生信息
>
> ```c
> # include <stdio.h>
> # include <malloc.h>
> struct Student{
> 	int age;
> 	float score;
> 	char name[100];
> };
> 
> int main(void){
>   int len;
>   struct Student * pArr;
>   int i,j;
>   struct Student t;
>   
>   //动态构建一维数组
>   printf("输入学生个数:\n");
>   printf("len = ");
>   scanf("%d",&len);
>   pArr = (struct Student *)mallco(len * sizeof(struct Student ));
>   
>   //输入
>   for(i = 0;i<len;<++i){
>     printf("请输入第%d个学生的信息:\n", i+1);
>     printf("age = ");
>     scanf("%d",&pArr[i].age);
>     
>     printf("name = ");
> 		scanf("%s", pArr[i].name);  //name是数组名，本身就已经是数组首元素的地址, 所以pArr[i].name 不能改成 &pArr[i].name
>     
>     printf("score = ");
> 		scanf("%f", &pArr[i].score);
>     
>     //按学生成绩升序排序 冒泡算法
>     for(i=0;i<len-1;i++){
>       for(j=0;j<len-i-1;++j){
>         if(pArr[j].score > pArr[j+1].score){
>           t = pArr[j];
> 					pArr[j] = pArr[j+1];
> 					pArr[j+1] = t;
>         }
>       }
>     }
>     
>     printf("\n\n学生的信息是:\n");
>     //输出
>     for (i=0; i<len; ++i){
>       printf("第%d个学生的信息是:\n", i+1);
> 			printf("age = %d\n", pArr[i].age);
>       printf("name = %s\n", pArr[i].name);  
> 		printf("score = %f\n", pArr[i].score);
> 	
> 		printf("\n");
>     }
>   }
> }
> ```
>
> `scanf("%s", pArr[i].name);  //name是数组名，本身就已经是数组首元素的地址, 所以pArr[i].name 不能改成 &pArr[i].name`     **看不懂**

#####165-166 枚举

> **枚举**
>
> ​         **什么是枚举**
>
> ​            **把一个事物所以可能的取值一一列举出来**
>
> ```c
> //自定义了一个数据类型，并没有定义变量，该数据类型的名字 enum WeekDay
> enum WeekDay
> {
> 	//MonDay, TuesDay, WednesDay, ThursDay, FriDay, SaturdDay, Sunday
> 	  MonDay=10, TuesDay, WednesDay, ThursDay, FriDay, SaturdDay, Sunday
> 
> };//分号
> 
> int main(void)
> {
> 	//int day;//day定义成int类型范围太大不合适，day的取值只可能有7个(0-6)，浪费空间
> 	enum WeekDay day = FriDay; //初始化一个enum WeekDay 类型变量 day
> 	printf("%d\n", day);
> 	
> 
> 	return 0;
> }
> 
> /*
> -----------在VC++6.0输出结果：
> 4
> 
> 14
> */
> 
> ```
>
> ```
> 怎么使用枚举
> /*
> 	日期：2011-05-04
> 	目的：枚举2
> */
> 
> #include <stdio.h>
> enum weekday
> {
> 	MonDay, TuesDay, WednesDay, ThursDay, FriDay, SaturdDay, Sunday
> 	 
> };
> 
> void f(enum weekday i)//本函数的目的只是期望接受0-6之间的数字，将形参定义为枚举
> {
> 	switch (i)
> 	{
> 		case 0:
> 			printf("MonDay !\n");
> 			break;
> 		case 1:
> 			printf("TuesDay !\n");
> 			break;
> 		case 2:
> 			printf("WednesDay !\n");
> 			break;
> 		case 3:
> 			printf("ThrusDay !\n");
> 			break;
> 		case 4:
> 			printf("FriDay !\n");
> 			break;
> 		case 5:
> 			printf("ThursDay !\n");
> 			break;
> 		case 6:
> 			printf("SunDay !\n");
> 			break;
> 	}
> 
> }
> 
> int main(void)
> {
> 	f(FriDay);//虽然FriDay本质上就是5，但直接写出f(5);就是错的，也不可能写成Friday  大小写敏感 
> 	return 0;
> }
> 枚举的优缺点
> 优点：代码更安全（强制输入），比较直观（有意义）
> 缺点：书写麻烦，不能出错。
> 总结：当是有限个元素时，用枚举更安全，高效。
> 
> ```
>
> 

##### 167进制转换

>  汇编里
>
> 1101**B** 二进制
>
> 1357**O** 八进制
>
> 2049**D** 十进制
>
> 3FB9**H** 十六进制
>
> **一个十六进制位，要用4个二进制数表示，(1)16 = （0001）2
> 前面补齐**
>
>  (2E)16->(0010 1110)  ,每一位用 4 个 2 进制表示,
>
> 八进制不能直接转换成 16 进制

#### 168补码

> **补码**   
>
> **地址是内存单元编号从 0到4G-1**
>
> **即 2的32次方-1   总线若是32位，则有32个0，1**
>
> ​    主要解决整数的存储 int 4字节 32位个0，1
>
>  
>
> A **已知十进制求二进制**
>
> **求正整数的二进制**   
>
> ​    **除2取余，直到商为零，余数倒序排列**
>
> ​            
>
> **求负整数的二进制**   
>
>    **`先求出与该负数相对应的正整数的二进制代码`，**
>
>    `然后，将所有位取反末尾加1，不够位数时，左边补一`
>
> 4字节int -5 先求5的二进制  
>
> 0000 0000   0000 0000     0000 0000  0000 0101  所有位取反，末尾加1
>
> 1111 1111   1111 1111     1111 1111  1111 1011   16进制：FFFFFFFB  
>
> ​       2字节  short int(-3) 先求3的二进制
>
> 0000 0000 0000 0011      所有位取反，末尾加1  
>
> 1111 1111 1111 1101     用十六进制表示：  FFFD
>
> **求零的二进制**
>
> ​     **全是零**
>
>  
>
> **B** **已知二进制求十进制**    
>
>    `如果首位是0，则表明是正整数，`
>
>    **按普通方法来求**
>
> 
>
> `如果首位是1，则表明是负整数，`
>
>    **将所有位取反末尾加1，所得数字就是该负数的绝对值**
>
> ​      习题：FFFFFFF5 已知二进制  求其代表的整数是多少？
>
> 1111 1111 1111 1111 1111 1111 1111 0101 
>
> ​        由于最高位是1，所以最终是负数，先对其所有取反
>
> 0000 0000 0000 0000 0000 0000 0000 1010 末尾加1后
>
> 0000 0000 0000 0000 0000 0000 0000 1011  该值为11 所以最终结果：-11
>
> ​         
>
>    **如果全是零，则对应的十进制数字就是零**
>
> 0000 0000  — 0
>
> 0111 1111 — 127
>
> 1000 0000 —  -128 
>
> 1000 0001 — -127
>
> 1111 1111 — -1
>
> 不同类型 转换 跟补码有关系,
>
> > **学习后应掌握：**
> >
> > ​      **在在VC++6.0中一个int类型变量所能存储的数字的范围是多少**
> >
> > ​      32位系统，32个0，1组合表示的内存单元，8个十六进制数组合）
> >
> > ​      int类型变量所能存储的最大正数用十六进制表示： 7FFFFFFF
> >
> > ​       int类型变量所能存储的绝对值最大负整数用十六进制表示：80000000            
> >
> > ​         **最小负数的二进制代码是多少**   1（0-0 31个0）
> >
> > ​         **最大正数的二进制代码是多少**  0（1-1 31个1）
> >
> > ​            
> >
> > ​         **已知一个整数的二进制代码求原始的数字** 
> >
> > 按“已知二进制求十进制”求
> >
> > ​      **数字超过最大正数会怎样**  变成负数 0111 1111=127 1000 0000 -128
> >
> >  
>
> 

#### 链表 

> **链表专业术语****：**
>
> ​       **首结点**：
>
> ​           存放**第一个有效数据**的结点
>
>  
>
> ​       **尾结点：**
>
> ​           存放**最后一个有效数据**的结点，指针域的指针为NULL，尾结点的标志
>
>  
>
> ​       **头结点：**
>
> ​           头结点的数据类型和首结点的类型是一模一样的
>
> ​           头结点是首结点前面的那个节点
>
> ​           头结点并**不存在有效数据**
>
> ​           设置头结点的目的是为了方便对链表的操作
>
> ​       **头指针：**
>
> ​           存放头结点地址的指针变量
>
>  
>
> ​      **确定一个链表需要一个参数，****头指针**
>
> **对于每个链表元素，分为左右两部分，左边为数据单元，右边为下一元素地址。**
>
> **例****：**
>
> **# include <stdio.h>**
>
> **# include <malloc.h>**
>
> **# include <stdlib.h>**
>
>  
>
> **struct Node**
>
> **{**
>
>    **int data; //****数据域**
>
>    **struct Node \* pNext; //****指针域**
>
> **};**
>
>  
>
> 头指针  -  >  头结点 - >  首节点  - > 尾结点
>
> ​    每一个结点 有俩部分   : 数据源 和 指针域



