# git 命令备忘录

##1.关于如何创建项目，并书写readme.md(可用来介绍项目，以及一些技术工具的介绍分享)
###1.首先我们需要创建一个项目，有两种方式：
![image](https://github.com/tangliangdong/git/blob/master/write_readme/1.jpg)
![image](https://github.com/tangliangdong/git/blob/master/write_readme/2.jpg)

之后，我们会进入项目的创建页面

![image](https://github.com/tangliangdong/git/blob/master/write_readme/3.jpg)

这就是我们项目的首页，

![image](https://github.com/tangliangdong/git/blob/master/write_readme/4.jpg)

然后我们就需要clone到本地，进行项目的更新，修改。

当然在此之前，我们需要在电脑上下载 [git](https://git-scm.com/),还有一些需要配置的，可以参考 [git初始配置](https://git-scm.com/book/zh/v1/%E8%87%AA%E5%AE%9A%E4%B9%89-Git-%E9%85%8D%E7%BD%AE-Git);

![image](https://github.com/tangliangdong/git/blob/master/write_readme/5.jpg)

然后在你本地找一个文件夹当做存放git项目的仓库，在该文件夹下，单击右键选择 `Git Bash Here`，输入 `git clone git@github.com:tangliangdong/git-book.git`

![image](https://github.com/tangliangdong/git/blob/master/write_readme/6.jpg)

这样就算克隆成功了。这就算刚克隆下来的项目的根目录。

![image](https://github.com/tangliangdong/git/blob/master/write_readme/7.jpg)

用编辑器打开后就能用[markdown](http://www.jianshu.com/p/q81RER)语法进行书写，markdown可以去学习下，不难

![image](https://github.com/tangliangdong/git/blob/master/write_readme/8.jpg)

在我们完成后，就可以向仓库提交文件。

在我们的项目的根目录下，打开git(就是之前提到的打开步骤)，输入`git add .` (意思是将所有更新过的文件放到暂存库，等待提交)。

![image](https://github.com/tangliangdong/git/blob/master/write_readme/9.jpg)

再输入`git commit -m 'first'` (first代表的是我们给这个commit标注的信息)提交到本地仓库，我们可以通过输入`git log` 来查看我们提交的历史记录。

![image](https://github.com/tangliangdong/git/blob/master/write_readme/10.jpg)

然后我们可以将其提交到github远程仓库，输入`git push origin master`

![image](https://github.com/tangliangdong/git/blob/master/write_readme/11.jpg)

这样我们就成功的同步到了github上，我们可以去github上就会发现我们多了一次commit，

![image](https://github.com/tangliangdong/git/blob/master/write_readme/12.jpg)

这里讲的步骤比较简单，具体的可以看[git教程](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%85%B3%E4%BA%8E%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6)


##2.关于合并commit的步骤
如果是别人的项目，那就首先frok项目，然后克隆到本地，如果是自己的就直接clone到本地。

    $ git clone <版本库的网址>

![image](https://github.com/tangliangdong/git/blob/master/images/1.jpg)

若要合并`second commit`和`third commit`，则

    $ git rebase -i <first commit 的SHA-1>

其中，-i 的参数是不需要合并的 commit 的 hash 值，这里指的是first commit， 接着我们就进入 编辑模式
例如此例就是a的SHA-1 (可用git log查看该commit的版本号)

    $ git rebase -i 768d796670519c00600d99a90fcfad31182a0773

![image](https://github.com/tangliangdong/git/blob/master/images/2.jpg)

pick是会执行该commit，而squash会把这个版本的commit合并到前一个commit。
应该改成这样，会合并`third commit` 和 `second commit`

![image](https://github.com/tangliangdong/git/blob/master/images/3.jpg)

进入编辑模式，命名 合并后的新commit的信息，

![image](https://github.com/tangliangdong/git/blob/master/images/4.jpg)

一开始的三个commit,最后只剩下合并后的`first commit` 和 `second and third commits`，如图

![image](https://github.com/tangliangdong/git/blob/master/images/5.jpg)

###最后，
    $ git push origin develop --force
    
    --force 强制合并远程仓库，防止出现错误（因为本地合并之后的commit和远程还没有合并的commit之间会有冲突）

再发出合并请求


