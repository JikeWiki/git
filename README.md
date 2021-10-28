# Git 的基本操作

## 一、Git 简介

### 1. 架构

Git 是一个分布式的代码托管工具，我们可以基于同一套代码，在不同电脑上进行项目开发，最终都可以可以把代码同步到 Git 服务器上。如下图：

![01.png](./img/01.png)

### 2. 工作流

下面是一张基于 Git 托管的代码流向图
![02.svg](./img/02.svg)

**Working Directory (工作区)**：
**Stating Area (缓存区)**：
**Respository (仓库)**：

## 二、安装

### 1. Linux

在 Debian、Ubuntu、Deepin 等操作系统上安装命令如下

```shell
sudo apt install git
```

### 2. Mac

Mac 可以使用`homebrew`进行安装，如下命令

```shell
# 安装homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
# 安装git
brew install git
```

或者安装 [xcode 工具包](https://developer.apple.com/xcode/)，`xcode`工具包包含了`git`，要注意的是，xcode 安装时间可能比较长

## 三、基本使用

## 四、示例
