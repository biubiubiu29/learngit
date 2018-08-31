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
asdf

