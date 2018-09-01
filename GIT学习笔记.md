# GIT学习笔记
> wodexuxi

## 创建版本库
1.创建一个空目录：

```
$ mkdir learngit
$ cd learngit
```
pwd命令用于显示当前目录

通过`git init`命令把这个目录变成Git可以管理的**仓库**：

```
$ git init
```

2.把文件添加到版本库


* 编写一个readme.txt文件放到learngit目录下（子目录也行），用命令git add告诉Git，把文件添加到仓库：


```
$ git add readme.txt
```


* 用命令`git commit`告诉Git，把文件提交到仓库：
 
``` 
$ git commit -m "wrote a readme file"

```

-m后面输入的是本次提交的说明，`commit`可以一次提交很多文件。

##更新状态


`git status`命令可以让我们时刻掌握仓库当前的状态，有没有需要提交的内容。如果`git status`告诉你有文件被修改过，用`git diff`可以查看修改内容。

##退回之前版本

我们要把当前版本回退到上一个版本，就可以使用`git reset`命令:

``` 
$ git reset --hard HEAD^
HEAD is now at e475afc add distributed
``` 
上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。

也可以用`git log`命令显示从最近到最远的提交日志，找到退回版本的`commit id`是`1094adb...`，于是就可以指定回到未来的某个版本：

``` 
$ git reset --hard 1094a
HEAD is now at 83b0afe append GPL
```
版本号没必要写全，前几位就可以了，Git会自动去找。

如果版本退回后，又想找回最新版本，命令`git reflog`可以找回你的每一次命令的commit id。

``` 
$ git reflog

e475afc HEAD@{1}: reset: moving to HEAD^

1094adb (HEAD -> master) HEAD@{2}: commit: append GPL

e475afc HEAD@{3}: commit: add distributed

eaadf4e HEAD@{4}: commit (initial): wrote a readme file

```

`git diff HEAD -- readme.txt`命令可以查看工作区和版本库里面最新版本的区别

`git checkout -- readme.txt`意思就是，把readme.txt文件在工作区的修改全部撤销，这里有两种情况：

* readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

* readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

总之，就是让这个文件回到最近一次git commit或git add时的状态

##删除/恢复文件
通常直接在文件管理器中把没用的文件删了，或者用rm命令删了：

`$ rm test.txt`

这是在工作区进行的操作，此时工作区和版本库就不一致了，接下来有两种情况：

* 确实要从版本库中删除该文件，那就用命令`git rm`删掉，并且`git commit`：

```
$ git rm test.txt
rm 'test.txt'
```

```
$ git commit -m "remove test.txt"
[master d46f35e] remove test.txt
 1 file changed, 1 deletion(-)
 delete mode 100644 test.txt
```
* 删错了，但版本库里还有，所以可以把误删的文件恢复到最新版本:

```
$ git checkout -- test.txt
```
`git checkout`其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。

