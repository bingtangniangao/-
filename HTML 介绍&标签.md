## HTML 介绍

常用标签

> `<!DOCTYPE html>`   声明
>
>  html  head  body   当为空时,没有注释,可以不写,但不推荐
>
> a form input button h1
>
>  paragraph   un-ordered list     ordered list
>
> small 
>
> divide   span   这俩没有特殊含义
>
> kbd  键盘键
>
>  video audio  svg不规则的图像
>
> 
>
> 标签都有默认样式
>
> 语义标签  strong   

###简历代码解析

> navigation   导航
>
> alternative  可选
>
> UNordered ilst 无序
>
> list item   列表一项
>
> description list  描述列表
>
>  - description trem
>  - descripton definition

```
<img src="#" alt="logo">
<nav class="topNavBar">
	<ul>
		<li><a href="#">about</a></li>
	</ul>
<nav>
<div class="banner" style="background-image:url(#)">  用背景不用 img
<main>
  <div class= "card">
    div
        <div class="pictur">
          <img src="" alt="头像">
        </div>
        <div class="text">
          <span></span>
          <h1></h1>
          <p></p>
          <hr>
          <dl>
            <dt>年龄</dt>
            <dd>18</dd>
         <div>
     /div
     		<footer class="media">
     				<a href="#"><img src="#" alt="..."></a>
     		</footer>
	 </div>
	   <a class="button" href="#"></a>
	   <p>
	   
</main>

<section>
		<h2></h2>
		<ol>
			<li> &amp </li>
		</ol>
</section>

```

> ###总结
>
> ​	`重点 css 支持横向 和纵向布局`
>
> ​		 - grid 布局不规则布局
>
> ​      网页布局时要思考: 是导航条 \列表\段落\图片\背景\标题等
>
> 





###iframe和 a

```
<iframe src="#" frameborder="0" name="xxx"></iframe>
<a href="http://qq.com" target=xxx>qq</a>
也可以是绝对路径
```

####targer

```
  <a href="http://qq.com" target="_blank">_blank</a>
  <a href="http://baidu.com" target="_self">self</a>
  <a href="http://baidu.com" target="_parent">parent</a>
  <a href="http://baidu.com" target="_top">top</a>
  配合ifrme 测试
  		首先建立 3 个 iframe页面, 祖  ifrme 父  ,父 ifrme 子, 子里有 4 个 a 标签,  
  		b 新建页面 ,s 自身,p 父   ,t 爷   
```

#### a 标签的 download 属性

> 1 下载 页面, 但是我没成功!
>
> ​	- `<a href="http://qq.com" download> 下载</a>`
>
> 2  用  http 协议
>
>  - Content-Type: application/octet-stream
>
>    

> `<a href="qq.com"> 下载</a>`
>
> -  http://   , 不能去掉, 否则是当成文件
>
> ​     `<a href="//qq.com"> 下载</a>`   
>
> - 不写当成 file 协议,按本身来
>
>  

预览 lile 文件用小工具 为啥?

> http-server
>
> npm i -g http-server
>
> - http-server -c-1  不用缓存

> 我遇到的问题
>
> ​      `  WARN checkPermissions Missing write access to /usr/local/lib/node_modules`
>
> ​       安装npm后，在～/ .bashrc中添加以下行：
>
> ​	 	`npm set prefix ~/.npm`
>
> ​		 `PATH="$HOME/.npm/bin:​$PATH"`
>
> ​		` PATH="./node_modules/.bin:$PATH"`
>
> ​         更改后执行以下行：
>
> ​          	`source ~/.bashrc`
>
> ​    <https://stackoverflow.com/questions/52979927/npm-warn-checkpermissions-missing-write-access-to-usr-local-lib-node-modules>

问题

> 开启http-server ,为啥主页没是 index.html 而不是其他? 这个不懂
>
> 

> a 的href情况:
>
> 无协议地址  
>
> ​		//qq.com
>
> 相对地址
>
> ​	./xxx.com
>
> 其他情况
>
> ​	`<a href="?name=frank"> qq</a>`      
>
>   - 自动发起 get 请求
>   - 写#是不发起请求的,
>       - 如果有 10 个h1 标签,页面会跳
>
> 伪协议
>
> ​	a 标签没有href 就是 span
>
> ​	a 标签 的 href 是""  会刷新页面
>
> `	<a href="JavaScript:alert(1);"> 下载</a>`  
>
>  `	<a href=":;"> 下载</a>`  

总结

> ifrme 的 name 配合 a标签的target 使用
>
>  target 的四个值 blank self parent  top
>
>  download
>
> href :
>
> ​    //qq.com 
>
> ​    ?name=xxx
>
> ​     JavaScript:;
>
> 

#### from 和 table

> a 标签 是 get 请求
>
> form 是 post 请求
>
>  - 默认是 get 所以,要加 method="post"
>
>    get 是获取,post 是提交数据
>
> - `<form action ="index.html" method="post">`
> - `<form action ="users" method="post">`
>
> from必须有 submit
>
> from 不支持 put,只支持 get 和 post
>
> from 也可以有查询参数
>
> -  acton="users?zzz=3"
>
> get 不能有第四部分
>
> form 也有 target=''_blank''  也可配合 iframe

> `Content-Type: application/x-www-form-urlencoded`
>
> ​     www-form-urlencoded   会把除英文外的字符转换成 utf-8编码

####intut

> `<input type="submit" value="button">`
>
> `<button>提交</button>`
>
> submit 会自动提交,如回车后,   普通按钮不会
>
> checkbox  复选框
>
> `<label for="xx"> 用户名</label> <input type="text" name="xxx"`
>
> 改 : `<label for="xx"> 用户名 <input type="text" name="xxx"</label>` name 必须写
>
> radio 单选框
>
> select 分组
>
>    option  
>
> ​       disabled 禁用
>
> ​       selected 默认
>
> textarea
>
>  - cols 列
>  - rows 行
>
> ​       



####table

> thead
>
> tbody
>
> tfoot
>
>   tr
>
> ​     th  td
>
> colgroup 
>
> `     <col width=100 bgcolor=red>`
>
> 自动纠正顺序
>
> 

table合并  border-collapse:collapse   

​    不应该就合并,应该是跨列

  



 

