# git怎样进行代码回退

## 1. 概述

git能帮助我们高效地进行代码托管，在使用git进行代码托管的时候，有时候我们需要回退版本。本文我们将一起来研究代码回退的方法。


在git中，`HEAD`指针指向我们当前分支的最后一次提交。比如我们提交过三个版本，那么此时`HEAD`指针位置如下图

![note-03-1](../img/note-03-1.png)

git版本回退会变更HEAD指针的位置，本文中，我们分别介绍两种代码回退的方式


## 2. git revert

`git revert` 指令会撤回某次提交（commit），这个指令触发的代码回退并不会真正地删除掉代码提交历史，而是将撤回操作作为新的一次提交记录。相关指令如下


如果要撤回当前版本的提交，可以使用以下指令
```shell
git revert HEAD
```


如果要撤回上一个版本的提交，可以使用以下指令
```shell
git revert HEAD^
```

回退到上上个版本
```shell
git revert HEAD^^
```

或者写成以下这个格式
```shell
git revert HEAD^2
```

以此类推...可以撤回到很多版本之前


如果要撤回具体某个版本的提交，可以使用以下命令格式
```shell
git revert 版本ID
```

## 3. git reset

`git reset`的作用是修改HEAD的位置，即将HEAD指向的位置改变为之前存在的某个版本。命令语法格式如下：

```
git reset [--soft | --mixed | --hard] [HEAD]
```
其中，HEAD的传参方式和`git revert`指令一样。

--mixed 为默认，可以不用带该参数，用于重置暂存区的文件与上一次的提交(commit)保持一致，工作区文件内容保持不变。如下示例

```shell
$git reset HEAD^            # 回退所有内容到上一个版本  
$git reset HEAD^ hello.php  # 回退 hello.php 文件的版本到上一个版本  
$git  reset  052e           # 回退到指定版本
```

--soft 参数用于回退到某个版本。如下示例
```shell
$git reset --soft HEAD^2 # 回退上上一个版本
```

--hard 参数撤销工作区中所有未提交的修改内容，将暂存区与工作区都回到上一次版本，并删除之前的所有信息提交。如下示例
```shell
$git reset –hard HEAD^3  # 回退上上上一个版本  
$git reset –hard bae128  # 回退到某个版本回退点之前的所有信息。 
$git reset --hard origin/master    # 将本地的状态回退到和远程的一样 
```
> 注意：谨慎使用 –hard 参数，它会删除回退点之前的所有信息。


上面几个参数可以存在以下区别

- --soft：取消提交更改，将更改暂存(索引)。
- --mixed(默认)：取消提交+取消暂存更改，更改留在工作树中。
- --hard：取消提交+取消登台+删除更改，一无所有。



