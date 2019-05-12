## js

键盘快捷键,  用数组 就是哈希.

	> 结构:
	>
	> ​	三组哈希[q,we…]   [a,s,d...]
	>
	> ​	没个键对应一个值 ; q:qqzone.com   w : weibo.com

###数据结构的使用

> 1. 主体页面 3 个标签,header  main footer
>
> 2.  26 个字母键 用 div 里套kbd 一个一个写,
>    - 但是可以用 js 生成
>      - 0:['q','w','e'…]  也可以用:0:{0:'q',1:'w'..lenght:10} 数组本质就是哈希,数组也是对象
> 3. 每个键添加一个网站
>    - q:'qq.com'
>
>  ` q \ 0 lenght 可以加'',也可以不加`
>
> 下一步   插入 div 标签
>
>    把js 创建好的数组和网站传到 main 中
>
> ```
> 		div1 = document.createElement('div')  创建 div 标签
>     x.appendChild(div1)  mian 的 id 是 x ,在这个里面添加 div
> ```
>
> 
>
>    

### 生成多个 div

> 1.用循环
>
> - keys 是 3 个数组,用他的 length循环,每次把div 放到 y中,
>
>   ```
>   index=0
>   while(index<keys['length']){
>     divxx = document.createElement('div')
>     minxx.appendChild(divxx)
>     row = keys[index]
>     index2=0
>     while(index2<keys['lenght']){
>       kbdxx = document.createElement('kbd')
>    	 	kbdxx.textContent = 'hi'
>     	divxx.appendChild(kbdxx)
>     	index2++
>     }
>     index++
>   }
>   ```
>
>   解析 : 俩个循环, 第一个是 3 个数组, 第二循环是给每个数组添加每行字母
>
>   - 每行的长度是通过每个数组的 lenght 长度,
>
>   - 先用 row = keys[index]  ,获取素数 
>   - 用 row['lenght'] ,获取长度, 
>   - 添加 kbd.textContent='row[index2]'  就可以输出每行的字母了
>   - ![image-20190508125119436](/Users/nj/Library/Application Support/typora-user-images/image-20190508125119436.png)
>   - ![image-20190508125257625](/Users/nj/Library/Application Support/typora-user-images/image-20190508125257625.png)
>
>   ###### 添加 css样式
>
>     kbd 是内联元素 如果居中要变成 display:inline-block
>
>     text-transform:uppercase,变成大写
>
>      移动第 2 行和第三行
>
>   ​	#mainxx>div:nth-child(2){ margin-left:1em;}
>
>   ​	 #mainxx>div:nth-child(3){ margin-left:2em;}
>
>   整体居中 
>
>      所以要在套一个 div,在 mian 里加 
>
>   ​	  main 用 text-align:center
>
>   ​	  div 变成 dispaly:inline-black
>
>   

监听键盘事件

> 上面就是变了 keys ,生成 kbd  ,在生成 26 个键
>
> docment.onkeypress = function(xzjcnxlkcjlk){
>
> ​	console.log('我发现你输入了一个键')
>
> }
>
> ​     用 docment 不用其他,否则监听不到
>
>    	    ` 怎么知道按了什么键` ,  当触发时所有的信息会传输到xzjcnxlkcjlk
>
> ​     	   用 `console.log(xzjcnxlkcjlk['key']) ` 就可以找到那个按的那个值
>
> ​       	 这个键存起来  `key = xzjcnxlkcjlk['key']`
>
> ​           
>
> ​            website = hash[key]      //就是 hash.q 对应的网站给 website ,当按键就可以输出了
>
> ![image-20190508141107531](/Users/nj/Library/Application Support/typora-user-images/image-20190508141107531.png)
>
> ​          ` location.href = 'http://'+website`   地址栏显示
>
> ​            `window.open('http://'+website,'_blank')`另一种方法 在新的窗口打开,  

编辑 hash

> 1. 在 kbd 中添加button
>
>    - buttonX = docment.createElement('button')
>
>    - butoonX.textContent = '编辑'
>    - kbdXX.appendChild(buttonX)
>
>    同时设置,css ,添加定位等
>
> 2. 添加button点击事件
>
>    ```
>    buttonX.onclick = function(jjjjj){console.log('我被点击了')}
>    但是 jjjjj 里没有点击属性
>    buttonX.id = row[index2] //目的是查看 button
>    但有 jjjjj.target 这个属性  
>    console.log(jjjjj['target']['id']) 获取点击的 id
>    ```
>
>    当用户点击时添加一个输入的网址
>
>     ```
>    buttonX.onclick = function(jjjjj){
>    	key = jjjjj['target']['id'])  //先拿到用户 id
>    	x = prompt("请输入网址")
>    	hash[key] = x
>    }
>     ```
>
>    

#### localStorage

> 防止刷新 消失  
>
> 思路, 每次编辑都备份下, 当刷新后再替换 , 这地方就是localStorage
>
> ` locationStorage.setItem('uuu',JSON.stringify(hash))`  存到localStorage里 uuu 是名字,必须是字符串,用 json