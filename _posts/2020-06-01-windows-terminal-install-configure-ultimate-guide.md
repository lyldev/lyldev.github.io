---
title: Windows Terminal 安装配置终极指南-2020
tags: Windows-Terminal 开发工具 教程
key: a2020-06-01-windows-terminal-install-configure-ultimate-guide
layout: article
aside:
  toc: true
show_edit_on_github: false
mathjax: true
mathjax_autoNumber: true
mermaid: true
chart: true
# sidebar:
#   nav: sidebar
---
![Windows Terminal 配置结果](/_illustrations/2020-06-01_213803-windows_terminal_final_result.png)

“众所周知” `Windows` 系统终端，包括 `命令行` 和 `PowerShell` 一直饱受开发者诟病，微软正在努力改变这种状况，本文介绍到的 `PowerShell Core` 和 `Windows Terminal` 就是微软这一努力的两大结果。经过一定的配置之后，`Windows Terminal` 无论从易用性和观感上都足以令人满意。 

本指南将实现 `Windows Terminal` 从安装到字体更改、主题设置以及添加到鼠标右键菜单的终极配置过程。

## 一、 PowerShell Core 安装和配置
_需要注意的是 `PowerShell Core` 并**不是**安装和使用 `Windows Terminal` 所必需的，但我强烈建议你安装 `PowerShell Core`，它是新一代的跨平台工具，具有更好的观感和可用性。_
### 1.1 PowerShell Core 安装
从[此链接](https://github.com/PowerShell/PowerShell/blob/master/README.md)中下载系统相应的的安装包，这里建议下载对应的 `stable` 版本。安装过程中一路`下一步`即可。
### 1.2 PowerShell Core 主题设置
为了实现上面图中的 `红-蓝-绿` 条状主题，我们需要安装 `ohmyposh` 。首先以管理员权限打开刚刚安装的 `PowerShell Core` ，输入以下命令：

{% highlight powershell %}
Install-Module posh-git
Install-Module oh-my-posh
{% endhighlight %}

上面的模块安装成功后，你可以先输入以下命令进行测试：

{% highlight powershell %}
Import-Module posh-git
Import-Module oh-my-posh
Set-Theme Paradox
{% endhighlight %}

运行后，你会发现 `PowerShell Core` 的主题已经改变，如下图所示：

![PowerShell Core 主题设置结果](/_illustrations/2020-06-01_213803-powershell_core_set_theme_result.png)

但是这样运行命令只能保证本次使用是这个主题，下一次打开时又需要重新运行。为了避免这样的重复操作，我们需要创建配置文件，这样我们每次打开都会是这个主题了。首先找到文件夹：  
`C:\Users\你的用户名\Documents\PowerShell\`  
在此文件夹中新建名为 `Microsoft.PowerShell_profile.ps1` 的配置文件。在文件中写入以下内容：

{% highlight powershell %}
Import-Module posh-git
Import-Module oh-my-posh
Set-Theme Paradox
{% endhighlight %}

### 1.3 PowerShell Core 字体更改
在上一步中，如果你没有对字体做过更改，你会发现设置主题后出现了乱码现象，这是由于普通字体无法与主题兼容所致。你可以选择下载 [更纱黑体](https://mirrors.tuna.tsinghua.edu.cn/github-release/be5invis/Sarasa-Gothic/) 或 更多的 [Poweline 字体](https://github.com/powerline/fonts)，安装后设置相应的字体即可。

_注意：这里下载安装的字体后面 `Windows Terminal` 的配置中还会用到_

## 二、 Windows Terminal 安装和配置
###  Windows Terminal 安装
