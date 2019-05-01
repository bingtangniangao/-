## css入门

**CSS** 指层叠样式表 (**C**ascading **S**tyle **S**heets)

 css 学习

- css spec  请搜索这个

- LESS CSS 

- sass  比上一功能多
- post css  css 纠正工具
- <https://css-tricks.com/>
- center css tricks    , css-tricks.com
- cordons film  ,tympanus.net
- CSS揭秘

#### 引入 css 的方法

   rel  relationship

> 内联 style 属性
>
> style 标签
>
> 外部文件 css link
>
> @import url(./b.css)

#### 项目

> `<ul style="list-style:none";margin:0;padding:0; class="clearfix">
>   <li style="float:left">
> </ul>`
>
> ul 的默认样式 padding-letf:40px  ;magin-top-butoom
>
> float 后会有 bug,要清楚浮动  , 给父亲家 clearfix
>
> `背会`
>
> - 给所有子元素加 float
> - 给父添加 clearfix

```
.clearfix::after{
  content:'';
  display:block;
  clear:both;
}
```

>`记忆点`
>
>- font-size  默认 16px
>- text-decoration:none;  文字装饰为空
>- margin    间距导航 标签与标签
>- font-weight:bold; 加粗
>- :hover  悬停
>  - 案例中会左右移动,所以要提前加透明的 border
>- transparent 透明
>- 强制触发 hover 的,开发工具中,选择:hov ->勾选>hover
>- padding  内边距   文字与下划线的距离
>- `a 标签的文字大于 li` 
>  - 所以给 a 标签加 display:block; 这样 li  就可以包裹 a 了
>- color :inherit  继承,
>  - 案例中a 标签有俩个颜色属性,一个是继承父body,但被划掉了,原因是第二的属性,为默认的浏览器给定样式,注意优先级
>  - 有的属性可以继承,有的不可以
>- 继承
>  - 案例中 rs  和 card   因为样式相同, 故在父设置样式,通过继承实现.
>- `空格`  回车换行 tab  多个都会变成 1个空
>  - 去空格方法 俩标签挨在一起写,之间距离可以通过
>- body有默认的 margin  8px
>- font-size
>- font-family
>
>  
>
>