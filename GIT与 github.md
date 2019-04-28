# GIT与 github

###第一步配置钥匙

New ssh key 只需有一个就行,可以访问所以的库

  配置 key

1. 设置  ->ssh 和 GPG keys
2.  [generating SSH keys](https://help.github.com/articles/generating-an-ssh-key/)
3. ![image-20190427203514426](/Users/nj/Library/Application Support/typora-user-images/image-20190427203514426.png)

#####-找到 新建 key

> ### [Generating a new SSH key and adding it to the ssh-agent](https://help.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

#####-在 terminal  终端中

> $ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
>
> email 要改成自己的
>
> 在连续 3 次回车
>
> 自动在~/.ssh 创建了id_rsa  和 id_rsa.pub 俩个文件
>
> ​        id_rsa 是钥匙, id_rsa.pub 是锁
>
>  - 需要把 id_rsa.pub里的密码上传上去  到 github 的 key 中,名字可以电脑型号^
>
> 

测试能不能连接 github

> rm ~ /.ssh/known_hosts
>
> ssh -T git@ithub.com   第一次建立连接



###配置git

>```
>git config --global user.name 你的英文名                                                   #此英文名不需要跟GitHub账号保持一致
>git config --global user.email 你的邮箱                                                      #此邮箱不需要跟GitHub账号保持一致
>git config --global push.default matching
>git config --global core.quotepath false
>git config --global core.editor "vim"
>```

>找到查看git配置文件  

###使用 git

>本地使用
>
>- git init
>
>-  touch 1.txt
>
>-  git add 1.txt 提交缓存
>
>- git status   -sb 查看状态
>    - add 后会变成绿色
>  - git commit -m "第一次提交"  存到 git 仓库
>      - tree .git  查看结构
>      - history 命令历史
>
>- 如果文件内容修改这回变成红色,(前面有 M)
>  - git log 变动历史
>- git status -sb 和 git status 的区别
>  - 加-sb 结构更容易看懂,
>  - 简写 gst
>
>如果删除了文件也要提交
>
>  rm js/main.js
>
>  git status -sb
>
>  git add  js/main.js
>
>  git status -sb
>
>  git commit -n "删除delete" 
>
>  

总结

> ### 总结
>
> 至此，我们来总结一下用到的命令
>
> 1. git init，初始化本地仓库 .git
> 2. git status -sb，显示当前所有文件的状态
> 3. git add 文件路径，用来将变动加到暂存区
> 4. git commit -m "信息"，用来正式提交变动，提交至 .git 仓库
> 5. 如果有新的变动，我们只需要依次执行 git add xxx 和 git commit -m 'xxx' 两个命令即可。别看本教程废话那么多，其实就这一句有用！先 add 再 commit，行了，你学会 git 了。
> 6. git log 查看变更历史



##上传到 github



#### 上传

>```
>git init
>git add README.md
>git commit -m "first commit"
>git remote add origin git@github.com:bingtangniangao/node_demo.git
>git push -u origin master
>```
>
>​      master 默认的分支  origin 是名字  可以修改么

#### 下载

>新建个仓库
>
>   ![image-20190427212930740](/Users/nj/Library/Application Support/typora-user-images/image-20190427212930740.png)
>
>选择 ssh 地址
>
>
>
>- `git clone`  git@github.com:bingtangniangao/node_demo.git
>- 下载后可以查看下   ls -la

#### 上传更新

>## 如何上传更新
>
>你在本地目录有任何变动，只需按照以下顺序就能上传：
>
>1. git add 文件路径
>2. git commit -m "信息"
>3. git pull （相信我，你一定会忘记这一个命令）
>4. git push
>
>`git pull` 使用情况: 如果远程改变的话,需要先下载下来,用 pull

![image-20190427233243071](/Users/nj/Library/Application Support/typora-user-images/image-20190427233243071.png)

### 总结

>1. git 和 github 之间有一个钥匙和锁
>
>2. 配置钥匙和锁
>
>   - github 设置  ->ssh 和 GPG keys
>
>   - 终端中  $ ssh-keygen -t rsa -b 4096 -C "邮箱地址"
>
>   - 连续 3 次回车后
>
>     自动在~/.ssh, 创建了id_rsa  和 id_rsa.pub 俩个文件
>
>     ​        id_rsa 是钥匙, id_rsa.pub 是锁
>
>     - 需要把 id_rsa.pub里的密码上传上去  到 github 的 key 中,名字可以电脑型号^
>
>上面是配置之间关系
>
>   接下来
>
>1. 创建本地 git 库
>
>2. 上传 github
>   1.  找到 github 的仓库,建立连接如下
>   2. git remote add origin git@github.com:bingtangniangao/node_demo.git
>         git push -u origin master