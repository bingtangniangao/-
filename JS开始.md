### JS开始

> 7 种数据类型
>
>    数字  字符串  布尔  symbol(符号)  null  undefined  对象
>
> number string  boolean   symbol  null   undefined  Object(Array function)
>
> -
>
> 电话号码 最好是字符   
>
> `number `
>
> ​	8 进制 是 0 开头
>
> ​	2 进制 0b  
>
> ​	16 进制  0x
>
> `string`
>
> ​	'你好'   "你好"   
>
> ​	''  ""   空字符串    字符串长度 0
>
> ​	' '   " "   空格字符串    字符串长度 1
>
> 转义符 \
>
>  ```
> var a = ' \' '   单引号
> var a = ' \n '  回车
> var a = ' \t '  tab 
>  ```
>
> 多行字符串 
>
>    ```
>  var s = '123 \
>           8999'
>  var s2 = ' 123'+
>            '123'
>   第二种好 ,第一种 \ 后面有空格容易报错
>   
>   ES6 中的 ` 
>   var s4 = `123
>   456`   //7 个字符包含回车
>    ```
>
> `boolean`
>
> > && 与
> >
> > ​	同时满足才行    
> >
> > || 或  
> >
> > ​	有一个为真, 同时为假,这为假
>
> `null`
>
> ​     一个值 null
>
> `undefined`
>
> ​     一个值 undefined
>
> null 和 undefined  是什么也没有
>
>   区别 
>
> 1. 没有赋值 为 undefined
>
> 2.  有一个对象,现在不行赋值为null ,也可以是 undefined
>
>      有一个非对象 不想赋值为 undefined
>
>    var obj  = null
>
>     var n   //不用赋值undefined,直接就是  
>
>      null 空对象 , undefined 是空 非对象
>
> `object `
>
> ​    是复杂类型,  有简单类型组成.
>
> var Person = {'name':'fang','age':18}
>
> ```js
> var Person{
>   name : 'fang'
>   age : '18'
>   chidren:null,
>   er:{name:'jjj'},
>   小三:undefined,
>   self:Person,   //可以是自己
>   '':'frank' ,  //可以 
> }
> person['name']  //必须加单引号
> 
> 9a : 'frank'  //不对 , 9a 必须加引号,不加按变量名规则赋值
> 'a b':'qqq'  //可以
>   delete person['name']  //删除
> ```
>
> ```js
> 'name' in perso     //true
> ```
>
> `遍历`
>
> ```js
> for  in
> for(key in person){
>   console.log(key)
> }//  name  age
> for(key in person){
>   console.log(person[key])
> }fang  18
> ```
>
> -
>
> ###### `typeof 的 bug`
>
> > typeof null   // object
> >
> > typeof  fn  // function







