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

**`单击 a 标签在 iframe 标签中打开`**

```html

<iframe src="#" frameborder="0" name="xxx"></iframe>
<a href="http://qq.com" target=xxx>qq</a>
也可以是绝对路径  ,
```

####targer

```html
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
>  - `<a href="http://qq.com" download> 下载</a>`
>  - 如果是Content-Type: text/html 用上面
>
> 2  用  http 协议
>
>  - Content-Type: application/octet-stream
>

#### href使用

> `<a href="qq.com"> 下载</a>`
>
> -  http://   , 不能去掉, 否则是当成文件
>
> ​     `<a href="//qq.com"> 下载</a>`   //file 文本文件
>
> - 不写当成 file 协议,按本身来 ,
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
> `#`qq.com 是跳转,不发生请求
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
>   - `写#是不发起请求的`,
>       - 如果有 10 个h1 标签,页面会跳
>
> ####`伪协议` 点击后不跳转
>
> ​      JavaScript: 类似 http:  ,但没有这个协议
>
> ​	a 标签没有href 就是 span
>
> ​	a 标签 的 href 是`""  `会刷新页面
>
> `	<a href="JavaScript:alert(1);"> 下载</a>`  
>
> `	<a href="JavaScript:;"> 下载</a>`   避免#跳转

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
> from必须有` submit`,才能提交
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

> 密码是中文时,  
>
> `Content-Type: application/x-www-form-urlencoded`
>
> ​     www-form-urlencoded   会把除英文外的字符转换成 utf-8编码

####intut

> `<input type="submit" value="button">`
>
> `<button>提交</button>`  //自动升级为 submit 按钮  ,如果 type 为 button,就不会提交
>
> submit 会自动提交,如回车后,   普通按钮不会
>
> checkbox  复选框
>
> `<label for="xxx"> 用户名</label> <input type="text"  id="xxx"`
>
> 改 : `<label > 用户名 <input type="text" name="xxx"</label>` name 必须写
>
> radio 单选框
>
> ​	- name 要相同, value 值要写
>
> select 分组
>
> option  
>
> ​       disabled 禁用
>
> ​       selected 默认
>
> ​	multiple 多选
>
> ```
> <select name="分组" multiple>
> 	<option value="">-</option>
> 	<option value="1">1</option>
> 	<option value="2"  disabled>2</option>
> 	<option value="3" selected>3</option>
> ```
>
> 
>
> textarea
>
>    style="resize:none"  控制放大缩小  
>
>    可以 加 width 和 height
>
>  - cols 列
>  - rows 行
>
> ​       



####table

> <table border=1>
>
> thead
>
> tbody
>
> tfoot
>
> tr
>
> ​     th  td
>
> colgroup 
>
> `     <col width=100 bgcolor=red>`  不用写 px
>
> 自动纠正顺序
>
> ```
> <table>
> 	<colgroup>
> 		<col width=100>
> 		<col width=70>
> 	</colgroup>
>  <thead>
>  	<tr>
>  		<th>项目</th>
>  	</tr>
>  </thead>
>  <tbody></tbody>
>  <tfoot></tfoot>
> </table>
> ```
>
> 

table合并  border-collapse:collapse   

​    不应该就合并,应该是跨列

  



 

