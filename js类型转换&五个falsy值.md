# js类型转换&五个falsy值

> 
>
> |          | number |     string      | boolean   | symbol | null | undefind | object |
> | -------- | ------ | :-------------: | --------- | ------ | ---- | -------- | ------ |
> | number   |        |        y        | 1t/0f     |        |      |          |        |
> | string   |        |        y        | 有 t/空 f |        |      |          |        |
> | boolean  |        |        y        |           |        |      |          |        |
> | symbol   |        |                 |           |        |      |          |        |
> | null     |        |    ==``n``==    | false     |        |      |          |        |
> | undefind |        |       `n`       | false     |        |      |          |        |
> | object   |        | [object Object] | true      |        |      |          |        |
>
> Uncaught TypeError:Cannot read property 'toString' of null
>
> Uncaught TypeError:Cannot read property 'toString' of undefind
>
> ```js
> console.log(1)  //实际上是输出字符串   如下:
> console.log((1).toString())  //1 
> var a =1 
> a.toString();
> ```
>
> 
>
> `老程序员字符串转换方法`
>
> > +''
> >
> > ```js
> > 1 + ''
> > true + ''
> > var obj = {}
> > obj + ''
> > ''+null  //可以反过来写
> > ''+undefined 
> > 
> > 1 + '1'  相当于  (1).toString() + 'i'  // + 是连接相同类型的数据,遇到不同会优先转换
> > ```
> >
> > window.String(1)  //方法 2 字符串转换
>
> boolean 转换
>
> 
>
> > Boolean(1) //true
> >
> > Boolean('')//false
> >
> > Boolean(' ')//true
> >
> > Boolean(null)//false
> >
> > Boolean(undefined)//false
> >
> > --------
> >
> > !true 
> >
> > !!1   //true     方法 2 用!!  
> >
> > !!null   // false   
> >
> > `记忆五个 falsy 值`
> >
> > ```js
> > 	number  : 0 和 NaN 是 false
> >   string : '' 是 false
> >   null 和 undefined:是 false
> >   object : 是 true
> >  	
> > ```
> >
> > 

#### `转换为 number`

> 1. Number('1')  === 1
>
> 2. parseInt("1",10) ===1
>
> 3. parseFloat('1.23') ===1.23
>
> 4. '1'-0 === 1
>
> 5. +'1'  
>
>     +'-1' ===1
>
>    -'-1'   // 1
>
>      -(-'-1' )  //-1
>
> 

#### `内存图`

> 代码区和数据区
>
> 数据区分为:stack 栈内存和heap堆内存,栈是一条一条的, 堆类似于堆排序
>
> | 代码                       | stack 栈内存   | Heap 堆内存 |
> | -------------------------- | -------------- | ----------- |
> | var a =1                   | 占64 位00000…1 |             |
> | var b = 2                  |                |             |
> | var o ={name:"jjj",age:18} | ADDR 100       | 100         |
> |                            |                |             |
>
> 如果 var o 是存在栈内存, 后面加属性会造成空间向下移,速度会变慢,该对象很麻烦;所以用堆内存
>
> `字符是 16 位的 ,数字是 64 位` ECMAscript 规定的
>
> 简单的存 Stack ; 复杂的存 Heap ,地址 存 Stack 
>
> #### `循环引用`
>
> ```js
> var a 
> a = {self:a}  //{self:undefined}    这个不是循环引用
> -----
> var a ={}
> a.self =a //{self:{...}}    这个是还是循环引用
> 
> 是先算右边的
> ```
>
> `考题`
>
> ```js
> var a ={n:1}
> var b = a;
> a.x = a ={n:2}   //
> alert(a.x) //undefined
> alert(b.x) //[object Object]
> ```
>
> `垃圾回收`
>
> > 如果一个对象,没有被引用就是垃圾,将被回收
> >
> > ```
> > var a ={name:a}
> > var b = {name:b}
> > a=b  //原来 a的应用会被回收
> > ```
> >
> > `考题`
> >
> > ```
> > var fu = function(){}
> > document.body.onclick =fn
> > fn = null
> > ```
> >
> > 如图
> >
> > ![image-20190528165144367](/Users/nj/Library/Application Support/typora-user-images/image-20190528165144367.png)
> >
> > 1
> >
> > 
>
> `IE的bug`
>
> ```js
> var fu = function(){}
> document.body.onclick =fn
> fn = null
> 
> //如果页面关闭 ,这应该会变成垃圾, 但是 IE6 不知道是垃圾,除非关闭整个浏览器
> ```
>
> ```js
> ie 内存泄漏解决办法
> window.onunload = function(){
> 	document.body.onclick = null
> }//所以的都 null
> ```
>
> 
>
> #### `深拷贝和浅拷贝`
>
> > ```js
> > `深拷贝`
> > var a = 1
> > var b = a 
> >  b = 2
> >  b变不影响 a 就是深拷贝,基本类型 赋值就是深拷贝
> >  对象的深拷贝就是,b 指向了另一个和 a 相同的堆内存
> > 
> > ```
> >
> > ```js
> > 浅拷贝
> > var a ={name:'a'}
> > var b = a
> > b.name = 'b'  
> > b 变 a 也变 就是浅拷贝,
> > ```
> >
> > 

>   . 运算的优先级最高
>
> 所以 a.x = a = {n:2}; 先运行 a.x
>
> a 变成 {n:1,x: undefined}
>
> 然后 从右向左
>
> a = {n:2};
>
> 此时  b 是 {n:1,x: undefined}
>
> 然后继续执行  a.x = a
>
> 因为 . 的优先级 最高
>
> 所以 a.x 已经初始化过 它是 {n:	fined}.x = a

> 补充 toString  
>
> ```js
> var n = 1 
> n.toString()
> 
> var  n = null 
> n.toString()  //报错
> ```
>
> 

