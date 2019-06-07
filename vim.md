# vim

> esc -> normal
>
> 插入模式:
>
> ​		a后          i前         o下一行
>
> ​		A行尾      I行头     O上一行  
>
> 保存: wq 

>模式
>
>normal   方便`命令``操作`和`移动`   大部分情况是`浏览`而不是编辑
>
>Command(命令模式)     在 normal 输入 :  后  , 
>
>- :vs 竖分屏       :sp横分屏          :q 退出分屏
>- :% s/foo/bar/g  全局替换     s 是替换    把 foo 换成bar   g 全局   
>- :set nu  行号
>
>Visual 模式  v 进入        V 是选择行,   v 可批量选择  移动就是选择
>
>
>
>

> Vim 插入技巧   ——快速纠错
>
> ​	进入 Vim 的 a\i\o 模式后
>
> - ctrl+h：删除上一个字符
>
> - ctrl+w：删除上一个单词
>
> - ctrl+u：删除当前行
> - `gi`快速跳转到最后一次编辑的地方进入插入模式



>### Vim 快速移动大法
>
>####单词的移动:
>
>`w/W` 移动到下个单词的开头  `小写`是非空白分隔   `大写`是空白分隔的
>
>`b/B` 移动到上一个单词的开头
>
>`e/E` 移动到下一个单词的结尾
>
>`ge` 移动到上一个单词的结尾
>
>`f`{char} 快速跳转到当前行的第一个查找字符,` ;` 往后, `, `往前
>
>`F `  反过来搜索字符 ,在末尾时用
>
>`t`{char}到查找字符的前面一个字符, F{char} 反向查找
>
>#### 水平的移动
>
>  normal 模式下
>
> ` 0 到行首`, ^ 行首第一个非空白字符      ,一般用 0 和 $   
>
>  `$ 行尾`  , g_行尾第一个非空白字符
>
>#### 垂直移动
>
>​	()句子 {}  段落   了解
>
>​    :help   帮助查询
>
> 
>
>#### 页面移动
>
>`gg/G` 移动到开头和结尾    
>
>  ctrl + o 快速返回
>
>  H/M/L 跳转到屏幕上中下
>
>  ctrl + u/f 上下翻页  ,  zz 屏幕中间 (当前行移动到屏幕中间)
>
>  数字 + gg 移动到某一行  
>
>:syntat on

> ### vim 增删改查
>
> ​	\# 增删改查
>
> 1、增加
>
> Normal模式 a/i/o   A/I/O
>
> 2、删除
>
> Normal模式 
>
> `x` 删除一个字符
>
> `4x` 删除4个字符
>
> d(delete)
>
> `daw` 删除单词和周围空格（delete around word）  默认为 dw
>
> `diw` 删除单词（不带走空格）
>
> `dd` 删除行
>
> `dt`{char} 删除直到    `dt)  ` 表示删掉到)之前
>
> `d$` 删除到结尾
>
> `d0` 删除到开头
>
> `2dd` 删除两行
>
> `u` undo 恢复操作
>
> 
>
> ####Vim修改
>
> Normal模式下
>
> `r` replace 替换一个字符 
>
> ​    eg: 光标下g ra g->a 
>
> `c` change 
>
> ​    `cw `删除字符至之后的,进入插入模式 change word
>
>    ` ct`{char} 删除到字符，进入插入模式  ct"  删除 开始到"
>
>    `caw` 删除单词
>
> `s` substitute 删除并进入插入模式 eg: 4s 删除4个字符进入插入模式
>
> 
>
> `R` 不断替换多个字符
>
> `S` 删除整行进行插入 
>
> `C` 删除整行进行插入
>
> ###查询
>
> / 前向搜索
>
> ? 反向搜索
>
> n/N 下一个或者上一个
>
> \*/# 当前单词的前向和后向匹配
>
> 
>
> 搜索结果高亮 :set hls (high light search)
>
> :set incsearch

> ### Vim 如何搜索替换
>
> \# 搜索替换
>
> substitute 支持正则
>
> :[range]s[ubstitute]/{pattern}/{string}/flags      :% s/self/this/g
>
> **range** 范围 
>
> ​    eg:  
>
> ​		`10,20 表示10-20行`
>
> ​       ` % 表示全部`
>
> **pattern** 替换模式
>
> **string**  替换后文本
>
> **flags** 替换标志位
>
>    ` g` global 全局替换
>
>    ` c` confirm 确认
>
>    `  n` number 查询匹配次数而不替换
>
> eg:
>
> :% s/self/this/g  # 替换 self->this
>
> :1,6 s/self//n    # 查询  计算有1-6行有多少个self
>
> :% s/\<name\>/Name/g # 精确匹配单词
>
> :% s/\<quack\>/jiao/g    #精确匹配
>
> 

> ### Vim 多文件操作
>
> \# 多文件操作
>
> `Buffer`  打开一个文件的缓冲区
>
> `Window`  可视化分割区域
>
> `Tab`     组织窗口为一个工作区
>
> ![image-20190607150412784](/Users/nj/Library/Application Support/typora-user-images/image-20190607150412784.png)
>
> 
>
> 1、Buffer
>
> :ls  列举缓冲区
>
> :b n 跳转到第n个缓冲区
>
> :bpre :bnext :bfirst :blast
>
> :b buffer_name  tab补全
>
> 
>
> `:e filename` 打开文件
>
> 
>
> 2、Window
>
> 一个缓冲区可以分割为多个窗口
>
> 每个窗口也可打开不同缓冲区
>
> 窗口可以无限分割
>
> 
>
> （1）窗口分割
>
> <ctrl + w> + s 水平分割  :sp [filename]
>
> <ctrl + w> + v 垂直分割  :vs [filename]
>
> 
>
> （2）窗口切换
>
> <ctrl + w> + w 循环切换
>
> <ctrl + w> + h 切换到左边
>
> <ctrl + w> + j 切换到下边
>
> <ctrl + w> + k 切换到上边
>
> <ctrl + w> + l 切换到右边
>
> 
>
> （3）窗口移动
>
> <ctrl + w> + H 移动到左边
>
> <ctrl + w> + J 移动到下边
>
> <ctrl + w> + K 移动到上边
>
> <ctrl + w> + L 移动到右边
>
> 
>
> (4)重排窗口
>
> :h window-size
>
> <ctrl + w> + = 所有窗口等宽等高
>
> <ctrl + w> + _  最大化活动窗口高度
>
> <ctrl + w> + |  最大化活动窗口宽度
>
> n + <ctrl + w> + _ 把活动窗口的高度设为n 行
>
> n + <ctrl + w> + | 把活动窗口的宽度设为n 行
>
> 
>
> 3、Tab标签页
>
> 一系列窗口的容器:h tabpage
>
> `:tabnew` {filename}     新标签中打开
>
> :tabe[dit] {filename}  新标签中打开
>
> <ctrl + w> + T 当前窗口移动到一个新标签页
>
> :tabc[lose]  关闭当前标签页及其中的所有窗口 
>
> :tabo[nly]   只保留当前标签页，关闭其他标签页
>
> :tabn[ext] {N} {N}gt  切换到编号N 的标签页
>
> :tabn[ext]      ` gt`    切换到下一个标签页
>
> :tabp[revious]   `gT`    切换到上一个标签页
>
> 
>
> 插件：ctrlp nerdtree