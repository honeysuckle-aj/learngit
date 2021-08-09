# Git 学习笔记

## 命令

| 命令(本地)                                         | 作用                                                    |
| -------------------------------------------------- | ------------------------------------------------------- |
| mkdir                                              | 创建版本库                                              |
| cd                                                 | 进入                                                    |
| pwd                                                | 查看路径                                                |
| git init                                           | 初始化，把目录变成Git可以管理的仓库                     |
| ls -ah                                             | 查看隐藏目录                                            |
| git add                                            | 把文件提交到仓库                                        |
| git commit -m "说明、备注"                         | 告诉Git，把文件提交到仓库                               |
| git status                                         | 查看状态、结果                                          |
| git diff                                           | 查看difference                                          |
| git log                                            | 查看最近到最远的提交                                    |
| git log --pretty=oneline                           | 查看最近到最远的提交（好看一点）                        |
| git reset --hard HEAD^                             | 回退到上一版本                                          |
| git reset --hard HEAD^```^/git reset --hard HEAD~n | 回退到上n个版本                                         |
| git reset --hard 版本号                            | 找到相应版本                                            |
| git reflog                                         | 记录每一次命令，可以找到版本号                          |
| git checkout -- filename                           | 把文件恢复到上一次add或commit的版本（撤销工作区的修改） |
| git reset HEAD filename                            | 把暂存区的修改撤销，重新放回工作区                      |
| rm filename                                        | 删除文件                                                |
|                                                    |                                                         |

| 命令（上传到GitHub）                                         | 作用                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| git remote add origin git@github.com:<username>/<repo name>.git | 把一个本地库与github库相关联                                 |
| git push -u origin master                                    | 把本地库的所有内容推送到远程库上并相关联，在第二次push时就不用添加参数```-u``` |
| git remote rm origin                                         | 删除本地库和远程的绑定关系                                   |
| git clone                                                    | 克隆远程库                                                   |



## 提示

- 可以多次add之后再commit

- git log里看到的一长串字符是版本控制代码，每个人都不一样

- git log中，HEAD表示当前版本

- 要使用版本号回退，可以在窗口关闭后使用，因为版本号是唯一的，前提是你还记得

- Git的版本回退速度很快，因为使用了指针，回退时只是将HEAD指针指向不同的版本

- git checkout可以用版本库里的文件替换工作区的文件，因此也可以用来恢复误删除的文件。<font color=red>从来没有添加到版本库就被删除的文件是不能被还原的！</font>

  ### 工作区
  
  在电脑里能看到的目录
  
  ### 版本库
  
  工作区里有一个隐藏目录.git，里面有很多东西，其中最重要的是暂存区，Git自动创建的第一个分支```master```，以及它的第一个指针```HEAD```。
  
  ```git add```就是把文件放到暂存区。
  
  ```git commit```就是往```master```上提交修改。
  
  每次修改完，如果没有将修改add到暂存区，则新的修改就不会被提交。
  
  ### 如果想撤销某次修改
  
  1. 文件在工作区：git checkout -- filename
  2. 文件在暂存区：git reset HEAD filename
  3. 文件在版本库：git reset --hard 版本号
  4. 文件已经推到远程版本库：等死
  
  ### Windows系统使用GitHub
  
  1. 创建SSH Key
  
     ```
     $ ssh-keygen -t rsa -C "youremail@example.com"
     ```
  
     然后一路回车使用默认值，不放心可以设置密码，完成后可以在用户目录找到```.ssh```目录，里面有```.id_rsa```（私钥）和```.id_rsa.pub```（公钥）两个文件。
  
  2. Github设置SSH
  
     登录GitHub，打开settings  ->SSH and GPG keys
  
     Title任意，Key复制上```.id_rsa.pub```中的公钥。
  
  3. 关联Github库与本地库
  
     创建repository，参考开头**命令（上传到GitHub）**
  
  
  
  

