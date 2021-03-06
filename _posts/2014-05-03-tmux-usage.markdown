---
layout: post
title: "Tmux 使用"
categories:
- tech
tags:
- linux, git


---

主要参考自FreeBSDChina的[wiki](https://wiki.freebsdchina.org/software/t/tmux)。

###配置

-----

tmux里面所有操作都通过快捷键完成。为避免和shell命令行的readline快捷键冲突，
在触发所有快捷键操作前都必须先按**老板键**激活控制台。tmux安装后默认的**老板键**
是`Ctrl+b`， 这个组合键是shell命令行的退格键, 所以在tmux要按两下`Ctrl+b`才能退一格，
不慎方便。发现`Ctrl+x`这个组合键用得比较少，可以把tmux的老板键换成`Ctrl+x`。

* 永久修改：
    编辑用户级tmux配置文件`~/.tmux.conf`，添加如下几行

        set -g prefix C-x
        unbind C-b
        bind C-x send-prefix
    重新登录生效。

* 临时修改
     查看prefix现有绑定键（即老板键）：

         tmux show-options -g | grep prefix
     要在tmux内置命令中修改及时生效，可在终端中输入以下命令：

         tmux set -g prefix C-x
         tmux unbind C-b 
         tmux bind C-x send-prefix


###常用操作

----

* `C-b :` 进入命令行模式
* `C-b ?` 列出所有快捷键
* `C-b [` 进入赋值模式(太有用了!),按空格键开始复制,回车确认！
* `C-b ]` 粘贴


###Widdow操作
----


###Pane操作

----
* `C-b z` 最大/小化当前操作，I LOVE THIS!!!!!
* `C-b "` 水平分割
* `C-b %` 竖直分割
* `C-b %` 竖直分割
* `C-b Alt+Arrow` 调整Pane大小


##session操作

-----

* `C-b d`  deattch当前的session
* `C-b C-z` 挂起当前的session
* `$tmux ls` 显示tmux的所有session
* `C-b $` 可以重命名当前的session
* `tmux attach [-t sessionname]` 恢复session。（有了这个就不怕玩得忘了工作:smile:）




##其他资料

----
* [tmux](http://wiki.tankywoo.com/tool/tmux.html)
* [tmux-a-simple-start](http://www.sitepoint.com/tmux-a-simple-start/)
