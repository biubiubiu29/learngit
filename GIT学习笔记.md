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

我们要把当前版本回退到上一个版本，就可以使用git reset命令:

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

