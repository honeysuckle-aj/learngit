# Git 学习笔记

## 命令

| 命令(本地)                                                   | 作用                                                    |
| ------------------------------------------------------------ | ------------------------------------------------------- |
| mkdir                                                        | 创建版本库                                              |
| cd                                                           | 进入                                                    |
| pwd                                                          | 查看路径                                                |
| git init                                                     | 初始化，把目录变成Git可以管理的仓库                     |
| ls -ah                                                       | 查看隐藏目录                                            |
| git add                                                      | 把文件提交到仓库                                        |
| git commit -m "说明、备注"                                   | 告诉Git，把文件提交到仓库                               |
| git status                                                   | 查看状态、结果                                          |
| git diff                                                     | 查看difference                                          |
| git log                                                      | 查看最近到最远的提交                                    |
| git log --pretty=oneline                                     | 查看最近到最远的提交（好看一点）                        |
| git reset --hard HEAD^                                       | 回退到上一版本                                          |
| git reset --hard HEAD^```^/git reset --hard HEAD~n           | 回退到上n个版本                                         |
| git reset --hard 版本号                                      | 找到相应版本                                            |
| git reflog                                                   | 记录每一次命令，可以找到版本号                          |
| git checkout -- filename                                     | 把文件恢复到上一次add或commit的版本（撤销工作区的修改） |
| git reset HEAD filename                                      | 把暂存区的修改撤销，重新放回工作区                      |
| rm filename                                                  | 删除文件                                                |
| git checkout -b <pointername>          /git switch -c <pointername> | 创建分支，并切换到该分支                                |
| git checkout <pointername>                     /git switch <pointername> | 切换到已有分支                                          |
| git branch <pointername>                                     | 创建分支                                                |
| git branch                                                   | 查看当前分支情况                                        |
| git merge <pointername>                                      | 将指定分支合并到当前分支                                |
| git branch -d <pointername>                                  | 删除指定分支                                            |
| git branch -D<pointername>                                   | 删除未被合并过的指定分支                                |
| git log --graph                                              | 查看分支合并图                                          |
| git log --graph --pretty=oneline --abbrev-commit             | 查看分支合并图                                          |
| git stash                                                    | 储藏工作现场                                            |
| git stash list                                               | 查看被储藏的工作                                        |
| git stash apply                                              | 恢复stash中的工作                                       |
| git stash drop                                               | 删除stash中的内容                                       |
| git stash pop                                                | 恢复stash中的工作并删除stash                            |
| git stash apply stash@{<number>}                             | 恢复指定工作区                                          |
| git cherry-pick <版本号>                                     | 复制一个指定的提交到当前分支                            |
| git rebase                                                   | 把未push的分叉提交历史整理成直线                        |
| git tag <name>                                               | 在最新提交的commit上打一个标签                          |
| git tag <name> <id>                                          | 给指定id打上标签                                        |
| git tag -a <name> -m"description" <id>                       | 用-a指定标签名，-m指定说明文字                          |
| git tag                                                      | 查看所有标签                                            |
| git show <tag name>                                          | 查看标签信息                                            |
| git tag -d <tag name>                                        | 删除标签                                                |
| git push origin <tag name>                                   | 推送某个标签到远程库                                    |
| git push origin --tags                                       | 一次性推送尚未推送到远程的所有本地标签                  |
| git push origin :refs/tags/<tag name>                        | 删除远程库的特定标签                                    |



| 命令（上传到GitHub）                                         | 作用                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| git remote                                                   | 查看远程库的信息                                             |
| git remote -v                                                | 更详细的信息                                                 |
| git remote add origin git@github.com:<username>/<repo name>.git | 把一个本地库与github库相关联                                 |
| git push -u origin master                                    | 把本地库的所有内容推送到远程库上并相关联，在第二次push时就不用添加参数```-u``` |
| git remote rm origin                                         | 删除本地库和远程的绑定关系                                   |
| git clone                                                    | 克隆远程库                                                   |
| git branch --set-upstream-to=<remote repository branch> <local repository branch> | 指定本地分支与远程分支的链接                                 |
| git pull                                                     | 将最新的提交从远程库抓下来                                   |
|                                                              |                                                              |



## 提示

- 可以多次add之后再commit

- git log里看到的一长串字符是版本控制代码，每个人都不一样

- git log中，HEAD表示当前版本

- 要使用版本号回退，可以在窗口关闭后使用，因为版本号是唯一的，前提是你还记得

- Git的版本回退速度很快，因为使用了指针，回退时只是将HEAD指针指向不同的版本

- git checkout可以用版本库里的文件替换工作区的文件，因此也可以用来恢复误删除的文件。<font color=red>从来没有添加到版本库就被删除的文件是不能被还原的！</font>

- git branch命令会列出所有分支，且当前分支前会有‘*’

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

  ### 分支管理

  #### 创建与合并分支

  在主分支中，master指向最新的提交，而HEAD指向master，每次提交，master分支都会向前一步，线越来越长。

  如果创建新的分支```new```，Git会创建一个新的指针`new`，指向master相同的提交，再把HEAD指向`new`，就表示当前分支在`new`上。

  <font color=red>这之后，对工作区的修改就针对`new`分支，master指针位置不变。</font>

  在完成`new`的工作之后，再把master指向当前提交，即可合并两指针。

  合并后可以删除分支。

  switch指令可以代替checkout用以转换分支。

  #### 解决冲突

  两个分支之间有可能发生冲突，即内容不相同的情况，此时无法直接合并分支，只能试图把各自的修改合并起来，若还是存在冲突，就需要手动解决冲突后再提交。
  
  如果是本地分支与远程分支存在冲突（合作伙伴的提交与本地提交冲突），则先指定本地分支与远程分支的链接（如果已有则跳过），再将新提交抓取下来，在本地解决冲突。
  
  若没有建立链接，则会提示`no tracking information`。
  
  #### 分支管理策略
  
  通常，Git在合并分支时会丢失分支信息，可以用`--no-ff`参数强制禁用该模式，在merge时生成一个新的commit，这样从分支历史上就能看出分支信息。
  
  在实际开发中：
  
  1. master分支是非常稳定的，平时不在上面干活，只是用来发布新版本。
  2. dev分支不稳定，是工作的地方。
  3. 开发者们都在dev上干活，每个人都有自己的分支，平时往dev上合并，知道发布新版本时才将dev合并到master分支。
  4. 开发一个新功能最好新建一个future分支
  
  #### Bug分支
  
  修复bug时，通过新建bug分支进行修复，然后合并、删除。
  
  当手头工作没有完成时，先将工作现场隐藏，然后去修复bug，修复后再回到工作现场。
  
  想要在两个分支中都修复bug，可以只将特定提交合并到另一分支（因为git提交的的更改，所以其实就是将特定的更改合并到另一分支）。
  
  在工作中可以多次stash，恢复的时候，先查看list，再恢复指定的stash。
  
  #### Rebase
  
  把分叉的提交历史整理成一条直线，看上去更直观，缺点是本地分叉提交已经被修改过了。
  
  ### 标签管理
  
  标签（tag）与commit相似，tag可以和某个commit绑在一起，方便分辨和查找。
  
  标签的排序是按照字母表顺序而非时间顺序，标签本身没有时间记录，标签标记的commit有时间记录。
  
  标签本身不会自动推送到远程库，所以可以安全的在本地删除；若标签已经被推送到远程，则现在本地删除，再从远程删除。要看看是否从远程库删除了标签可以打开GitHub查看。
  
  
  
  
  
  

