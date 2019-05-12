#### 简历 CSS

@import url(./b.css)

style 

link

> 导航栏
>
>   1. 用 float  把 li 变成横向,
>
>   2. 去除 ul 的 margin \padding\list-styhle:none
>
>   3. 给父元素清楚浮动,  并包住子元素
>
>      ```
>      .clearfix::after{
>        content:'',
>        dispaly:block;
>        clear:both;
>      }
>      ```
>
> 	 4. 添加a字体颜色,去下划线,大小颜色
>
> 	 5. a 和 nav 加 float,  父加 clearfix
>
> 	 6. 给 a 加:hover ,用 border出现下滑线 ,但是会出现左右抖动
>
>      	 1.  方法提前添加 border ,用 transparent
>      	 2.  取色可强制触发 hove
>
> 	 7. `增加 a 与下边线的距离,用 padding,但是 li 会的高度会小于 a`
>
>      	 1. 解决方法是,用把a 变成display:block  
>
>  

####制作 logo

> inherit  继承
>
> 1. a 标签默认是自带颜色的(蓝色)  ,  color:inherit 继承上级
>
> 2. RS card 俩个 span 的继承, 相同的设置可以在父元素上
> 3. 主要 span 和span 的空格问题
>
> 4. 对齐 rscard 和 nav  , nav 要加 border-top,刚才加 Hover 的下划线
> 5. 整个导航 在向下移动  ,最好上下对称
> 6. 去掉 body 的 margin,   加左右padding

##### 高度与文档流

> <https://alpha.wallhaven.cc/>  背景图
>
> 1. div 的高度还是有文档流高度总和决定的
>
> -  背景图要加 height,
>
> 2. 内联元素从左往右
>    - 文本过长会存在`中文`上下分身
>    - 文本过长会存在`英文`上下分身
>      - word-break:break-all   英文可以断行
> 3. 块级元素站一行
> 4. span 的字体有建议的行高 ,  这就是 span 的高度
>    - 一行多种不同字体的 span, 安装最高的算 
>    - 在字体小的时候, div 的行高大于字体,是生效的,如字体大,line-height 小则会发生一些不理解 的情况.  ,可以 line-height 好 height 一起设置.
>
> 

#### position fixed

> ![image-20190510133827000](/Users/nj/Library/Application Support/typora-user-images/image-20190510133827000.png)
>
> 过滤器  ,点击 img 找图片
>
>  ```
> .banner{
>   height:515px;
>   backgroud-imge:ulr(./img)
>   
> }
>  ```
>
> 1. 把导航栏脱离文档流   position:fixed;
>    - 产生的问题 导航栏的宽度没了,   
>    - 这时加 width:100%,会产生超出天际的问题 ,因为要加 padding,向右移动了, 但是去掉 padding 又不好看
>    - 解决办法,在导航栏重新套一个 div ,给这个外面 div 加 padding,里面的是 100%
> 2. 添加遮罩 .mask

CSS 三角形

> userCard 设置
>
> ​    max-width:940  ,可以自适应,同事 margin:auto ;可以居中
>
> ```css
> .userCard {
>   max-width: 940px;
>   margin-left: auto;
>   margin-right: auto;
>   background-color: #ffffff;
>   box-shadow: 0px 1px 5px 0px rgba(0, 0, 0, 0.5);
> }
> ```
>
> - hell 用 padding 来居中,
>
> - 变出一个三角形
>
>   - 用 border 
>   - 在 span 里套 span 做三角形
>
> - .welcom { display:inline-block}  这个必须写 
>
>   ```css
>   .userCard .welcome .triangle {
>     display: block;
>     border: 10px solid transparent;
>     width: 0px;
>     border-left-color:black;
>     border-top-width: 0px;
>     border-right-width:0px;
>     position: absolute;
>     left: 4px;
>     top: 100%; //不能是 bottom:0;
>   }
>   
>   ```
>
>   - 注意的问题 : 是文本段落过长 ,回换到下一行
>   - display:inline-block ,会阻止 magin 合并
>   - 设置 上下 hello间距   ,  hr 的间距
>
> - 设置 dl dt  
>
>   - 全部 float 
>   - 利用自动换行的特性, 宽度 50%
>
> - footer 的图标
>
>   - iconfont
>   - 居中
>   - fill      svg 语法 背景白色
>   - `vartical-align:top`

#### 制作按钮

> ```css
> body > main .downloadResume-wrapper {  /*a 的父标签*/
>   text-align: center;
> }
> body > main .downloadResume {   //a 标签
>   border:1px solid seagreen;
>   font-size:14px;
>   line-height:16px;
>   padding: 21px 55px;
>   display: inline-block;      // 因为 span 没有 padding 的高度
>   background: #efefef;
> }
> ```
>
> 阴影
>
> ​	css shadow generator
>
>  添加 过渡属性
>
>   transiton:box-shadow 0.2s;
>
>  .selfIntroduction  自我介绍,  设置宽度 940px margin-left:auto 和 right:auto
>
> 
>
> 

#### 技能条

> 1.设置 section  的宽度,整体居中,还有间距     skills 技能
>
> 2.设置标题居中 ,颜色 ,字体大小,行高,粗细
>
> 3.设置 ol 背景,阴影 
>
> 4.添加下滑现 用俩个 div,一个背景一个前景
>
> - progressBar   进度条 
>
> - progress 进度 
>
> - 因为是 div 所以要加 height,不然没有高度,不显示
>
> - ol>li 浮动  
>
> - 进度条和h3标题的 margin
>
> - ol 的 padding 
>
> - `设置 li 之间的间距`   难点
>
>   - 因为已经 50%了,如果加margin 和 padding 会换行,  可以外面套一个 div,或者用box-sizing:border;
>
>   - 这里用的是左右浮动用,
>
>   - ```css
>     section.skills > ol > li:nth-child(even) {
>       float: right;
>     }
>     ```
>
>     

#### 作品集

> 1.标题 ,位置同上面的技能是一样的,     portfolio作品集
>
> 2.三个 li 浮动,
>
> `接下来结局居中的问题 `
>
> - 不需要居中 li  ,而是居中 li 的父亲,  但是 ol 的宽度是 100%
>
> - 解决思路,把要么加宽度,  或者把 ol 变成 display :inline-block;
>
>   - 虽然宽度 减小了,但是也增加了空隙, 要在加 vertical-align:top;
>
>     ```css
>     section.portfolio > nav > ol{
>       margin: 0 auto;
>       display: inline-block;
>       vertical-align: top;
>     }
>     ```
>
>     <u>*技能不是居中是 50%*</u>
>
> -  第二个问题是 : li 要加间距,margin 但是,居中会把左边的也包含进去,
>
> -  先用 text-align:center;把nav 的 lo 居中
>
>   - 去掉第一个 margin   :nth-child(1){margin-left:0} 来覆盖
>
> - 添加进度条   progressBar
>
>   - 默认进度条的宽度过大, 要把 nav 变成 inline-black. ,在居中
>
>     用 text-align:center;
>
>     - 设置进度条的样式
>
>     ````css
>     section.portfolio>nav .bar{
>       height: 5px;
>       background: white;
>       border-radius: 2px;
>       margin-top: 5px;
>     }
>     section.portfolio > nav .bar-inner{
>       height: 100%;
>       background: #E6686A;
>       border-radius: 2px;
>     }
>     ````
>
>     
>
> - 制作切换的下划线
>   - 制作三种不同的状态
> - 给要选中的 li  添加 id,方便 js 选取
> - 添加 js
>
> ```css
> <script>
>       portfolio1.onclick= function(){
>         portfolioBar.className = 'bar state-1'
>       }
>       portfolio2.onclick= function(){
>         portfolioBar.className = 'bar state-2'
>       }
>       portfolio3.onclick= function(){
>         portfolioBar.className = 'bar state-3'
>       }
>     </script>
> ```
>
> - 用绝对定位制作底下的 3 个图片的位置



