# CSS布局

---



####高度与文档流

---

> wall haven 背景天堂
>
> - `div 高度或块级元素` 尤其内部`文档流元素` 的`高度 `总和决定
>
> - `文档流`:文档流元素的流动方向
>
>   - `内联元素`从左往右流
>
>     - 文字会被截断
>
>     - 文字过长英文不会换行;中文会换行.英文单词不能分开
>
>       - word-break:break-all;英文可以换行
>
>         
>
>   - `块级元素`从上往下,单独一行
>
> - display:inline-block;  新属性为解决 float ,但是个设计失误
> - dody 是块
>
> ##### *难点*`span` 的高度
>
> > `内联元素的高度`  是由字体和设计师设计的参数相关,很难确定
> >
> > - 默认有 x 基线对齐,
> >
> > - 可以给 div 确定的高度 height
> >
> > - 上面是文字过大,line-height 过小, 但正常是 line-height 要大于文字高度,  div 的高度就等于 line-height 了
> >
> >   
>
> 1. 文字的居中不是中线,而是基线
> 2.  行和行之间会有建议的行高
>
> ```css
> span.first{border:1px solid red;
> 	font-size:100px
> 	}
> 
> span.first{border:1px solid red;
> 	font-size:100px;
> 	font-family:Tahome;
> }
> 
> ```
>
> 区别:因为字体不懂,所以二者的span 高度不同
>
> **font-size值**是*文字*差不多的高度.在 **span 的高度**就是在乘以设定的倍数,这样做的目的是增加点行距,好看.
>
> **`div 的高度`**就是line-height 加 padding   *近似于*
>
> 

#### 脱离文档流

> 就是高度会消失,
>
>  position-fixed
>
> 1. 高度消失
> 2. 宽度也缩小,案例中本来nav是在右边的,所以要加 width解决,但是加了宽度会出现新的 bug,超出了父,相当于宽度加了外边距,  如果吧 padding 去掉,则不好看.
>    - 因为原来的不能左右 float,可以重新套一个 div,就解决了
>
> 局对定位宽度出问题
>
> ​    不要写宽度 100%和高度;

其他

> background-color:rgba(0,0,0,0.8);
>
> background-position:center center;
>
>   background-size:cover;
>
> max-width: 94px;  自适应不写会出现自适应

#### 三角形制作

>思路 去掉 border 的三个边,
>
> 	使用属性 transparent,
>
>​        `注意`没有 border-top-height 这个属性;四个边的宽度用 border-top-width 表示,
>
>​	   用 border-top-width:0,隐藏边会失败,只能用transparent;
>
>```css
>div{
>  border:50px solid transparent;
>  width:0px;
>  height:0px; 
>  border-left-color:#E6686A;
>  border-top-width:0px;
> /* border-right-width:0px; */
>}
>```
>
>第二种定位
>
>​    position:relativ
>
>​    positon:absolute ,相对于祖先的第一个定位
>
>

>display:inline-block  margin 不合并
>
>css tricks shape  形状
>
>iconfont 
>
>vertical-align:top;



