---
layout: post
title: WSL2 color scheme config
subtitle: Each post also has a subtitle
gh-repo: beefbill/beefbill.github.io
gh-badge: [star, fork, follow]
tags: [note, wsl2, zsh, vim]
comments: true
---

# WSL2 主题配色记录

## 前言

最近在学习[计算机教育中丢失的一课](https://missing.csail.mit.edu/)，需要使用到 bash 以及 vim 。 由于笔者使用的是 win10 系统并且没有安装虚拟机，因此采用的是微软的 WSL２系统。由于对默认的主题设置不太满意，所以笔者开始了漫长的配置设置之旅。先后完成了 **zsh的主题设置， windows terminal 的配色方案设置以及 vim 的主题设置**。整个过程细节还蛮多的，因此记录一下，方便以后进行查阅。

另外，本文只涉及到有关主题和配色方案的设置， 

有关 wsl 的安装请参考官方文档 [在 Windows 10 上安装 WSL | Microsoft Docs](https://docs.microsoft.com/zh-cn/windows/wsl/install-win10)

有关 Oh My Zsh 的安装与配置我具体参考的是 [Oh My Zsh, 『 安装 & 配置 』 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/35283688)

[Oh-My-Zsh及主题、插件安装与配置 - Mr_Doer - 博客园 (cnblogs.com)](https://www.cnblogs.com/misfit/p/10694397.html)

## 效果展示

![image-20210610221020241.png](https://i.loli.net/2021/06/11/b9oc6a5tuf2PIQF.png)

![image-20210610221205400.png](https://i.loli.net/2021/06/11/Vajtbfygv8hi9ql.png)

![image-20210610221256647.png](https://i.loli.net/2021/06/11/yR7neuYJg6oipFL.png)

![image-20210610221433206.png](https://i.loli.net/2021/06/11/LW12MTOIYJ6c8E3.png)

## Zsh 主题配置 —Powerlevel10k

在挑选了很多主题之后，最终确定了 Powerlevel10k 主题， 主要是比较美观而且配置起来比较轻松。

### 安装 与配置Powerlevel10k
#### 安装

使用如下命令安装主题

```
git clone --depth=1 https://gitee.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

安装之后修改 `~/.zshrc`

```
ZSH_THEME="powerlevel10k/powerlevel10k"
```

![image-20210610222643017.png](https://i.loli.net/2021/06/11/wSF19qoXvEKCtUL.png)
#### 补充字体下载

修改完之后还需要下载 nerd字体 才能正常显示所有的字符 [Nerd Fonts](https://www.nerdfonts.com/font-downloads) 官方推荐的是 `Meslo Nerd Font` 具体按需要进行下载, 笔者使用的是 `JetBrainMono Nerd Font`

下载安装之后，打开 `Windows Terminal`~~(没有直接在微软商店里面下载就行了)~~

#### Windows terminal终端设置

打开设置

![image-20210610223848987.png](https://i.loli.net/2021/06/11/12kbOSyZcDnUEA7.png)

**选择对应的分发版本，并选择外观，更改字体即可**

![image-20210610225712225.png](https://i.loli.net/2021/06/11/sypwzYFNlPLUhuG.png)

后续修改配色方案也需要在这里进行

#### 配置

安装主题之后，在终端中输入命令

```
p10k configure
```

按照提示进行配置即可

## 终端配色方案

~~难以相信竟然会有人不去搜现成的配色方案而是自己一个个拿取色器取 vscode 的 onedark主题里面的颜色~~

在调配色方案的时候，由于 vim 默认主题虚拟模式的颜色过于晃眼，因此改来改去改了好久才勉强满意。最后才想起来可以直接改 vim的主题。。。。。。。。

下面是我自己设置的配色方案

![image-20210610225615756.png](https://i.loli.net/2021/06/11/cd9hViRwOnKarvb.png)

这里可以通过　JSON 文件方便的进行修改

选择上图左下角的打开　JSON　文件

找到　`profiles` 条目下自己创建的配色方案（直接搜配色方案名字）

### 添加亚克力效果 调整边距

亚克力效果能使得终端看起来有像玻璃一样的材质，个人觉得对颜值提升比较大

但是这部分设置是非必需，完全看个人喜好，不需要请直接跳过

在里面添加如下几行

```json
"acrylicOpacity": 0.84999999999999998, //设置亚克力效果的不透明度
"padding": "10,10,10,10",//设置边距
"useAcrylic": true //使用亚克力效果
```

（注意如果添加在最后，最后一行是没有逗号的）

### 配色方案配置

接着在 `schemes` 条目里面修改对应的配色方案

按顺序一般为最后一个

我的配置如下

```json
        {
            "background": "#282C34",
            "black": "#282C34",
            "blue": "#268BD2",
            "brightBlack": "#767676",
            "brightBlue": "#A3B8BA",
            "brightCyan": "#65C8D9",
            "brightGreen": "#5AA879",
            "brightPurple": "#D984F2",
            "brightRed": "#F24C5A",
            "brightWhite": "#F0F0F0",
            "brightYellow": "#FFD700",
            "cursorColor": "#FAF0F8",
            "cyan": "#56ABB9",
            "foreground": "#9FB1BF",
            "green": "#859900",
            "name": "vscode",
            "purple": "#C678DD",
            "red": "#E06053",
            "selectionBackground": "#8BD2D6",
            "white": "#CCCCCC",
            "yellow": "#C19C00"
        }
```

到此为止终端配色方案就配置好了

## vim主题设置

### 查看当前主题

在终端中输入 `vim` 打开 vim 编辑器

在 vim 编辑器中输入 `:colorscheme`并按回车

默认 vim 会 打印 `default` 表示当前使用的是 默认主题

### 查看现有主题

在 vim 编辑器中输入 `:! ls $VIMRUNTIME/colors`

vim将会打印如下

![image-20210610232007660.png](https://i.loli.net/2021/06/11/9telKdSpwzon32q.png)

其中有 `.vim` 后缀的文件均为主题文件

### 设置主题

在 vim 编辑器中以`:colorscheme name` 的形式可以修改 vim 主题。

想要永久的更改主题，需要修改 vim 的配置文件`~/.vimrc`文件。

如果你的home文件夹没有这个文件，请自行创建一个。

在配置文件中添加 `colorscheme name` 即可修改主题

请注意，配置文件需要重新加载才能生效

笔者使用的主题是 `elflord`

## 参考网站

1. [在Windows 10中启动WSL2 并安装Linux（ Ubuntu 为例）并运行docker](https://blog.csdn.net/yushuzhen2008/article/details/104944579)
2. [在 Windows 10 上安装 WSL Microsoft Docs](https://docs.microsoft.com/zh-cn/windows/wsl/install-win10)
3. [Oh My Zsh, 『 安装 & 配置 』 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/35283688)
4. [Oh-My-Zsh及主题、插件安装与配置 - Mr_Doer - 博客园 (cnblogs.com)](https://www.cnblogs.com/misfit/p/10694397.html)
5. [在windows中ohmyzsh 的powerlevel10k主题及插件推荐_KeyBordkiller的博客-CSDN博客](https://blog.csdn.net/KeyBordkiller/article/details/109537610?utm_medium=distribute.pc_relevant_download.none-task-blog-baidujs-1.nonecase&depth_1-utm_source=distribute.pc_relevant_download.none-task-blog-baidujs-1.nonecase)
6. [史上最好看的 Windows Terminal 配色方案 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/163765431)



