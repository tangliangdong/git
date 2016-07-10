# git 命令备忘录

首先frok项目，然后克隆到本地

	$ git clone <版本库的网址>
<<<<<<< HEAD

![image](https://github.com/tangliangdong/git/blob/master/images/1.jpg)

若要合并`second commit`和`third commit`，则

	$ git rebase -i <first commit 的SHA-1>
	
其中，-i 的参数是不需要合并的 commit 的 hash 值，这里指的是first commit， 接着我们就进入 编辑模式
例如此例就是a的SHA-1 (可用git log查看該commit的版本號)

	$ git rebase -i 768d796670519c00600d99a90fcfad31182a0773
	
![image](https://github.com/tangliangdong/git/blob/master/images/2.jpg)

pick是會執行該commit，而squash會把這個版本的commit合併到前一個commit。
应该改成这样，会合并`third commit` 和 `second commit`

![image](https://github.com/tangliangdong/git/blob/master/images/3.jpg)

进入编辑模式，命名 合并后的commit信息

![image](https://github.com/tangliangdong/git/blob/master/images/4.jpg)

完成后的三个commit最后只剩下合并后的`first commit` 和 `second and third commits` 

###最后，
	$ git push origin develop --force
	
	--force 强制合并远程仓库，防止出现错误
	
再发出合并请求





 
=======
	![image](https://github.com/tangliangdong/git/images/1.jpg)
>>>>>>> 613635d... Update README.md
