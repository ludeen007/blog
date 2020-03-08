+++
title = "Bash Shortcuts Cheat Sheet"
categories = ["cheat-sheet"]
tags = ["cheat-sheet","shortcut"]
date = 2020-03-08T09:46:09+08:00
+++

Bash Shell 快捷键

## 进程控制
* Ctrl + C 终止命令执行
* Ctrl + Z suspend command/send to background(use fg to bring forward)
* Ctrl + D 关闭Bash Shell

## 控制屏幕输出
* Ctrl + L 清屏
* Ctrl + S 停止输出到屏幕(for verbose commands)
* Ctrl + Q 允许输出到屏幕(undo Ctrl + S)
  
## 移动光标
   1. 行
      * Ctrl + A 或 Home键 移到行首
      * Ctrl + E 或 End键 移到行尾
      * Ctrl + XX 在行首和光标位置之间移动
   
   2. 单词
      * Alt + B 移到前一个单词的词首
      * Alt + F 移到下一个单词的词尾
      
   3. 字符
      * Ctrl + F 前进一个字符
      * Ctrl + B 后退一个字符
  
## 大小写操作
* Alt + C 从光标位置开始，第一个字符大写(Capitalize)到词尾
* Alt + U 从光标位置开始，全部字符大写(Upper case)到词尾
* Alt + L 从光标位置开始，全部字符小写(Lower case)到词尾
  
## fix typos
* Alt + T 交换当前单词和前一个单词
* Ctrl + T 交换当前字符和前一个字符
* Ctrl + _ 撤销上一次击键，可撤销多次

## 命令历史
* Ctrl + R 进入反向搜索命令历史模式
* Ctrl + O 执行反向搜索命令历史模式找到的命令
* Ctrl + G 退出反向搜索命令历史模式
* Ctrl + P 或 向上箭头键 回退一个命令
* Ctrl + N 或 向下箭头键 前进一个命令
* Alt + . 前一个命令的最后一个单词

## 剪切和粘贴
1. 剪切
    * Ctrl + U 从光标位置开始，剪切到行首
    * Ctrl + K 从光标位置开始，剪切到行尾
    * Ctrl + W 从光标位置开始，剪切到词首
    * Alt + D 从光标位置开始，剪切到词尾
    * Ctrl + D 或 Delete键 剪切光标所在位置的字符
    * Ctrl + H 或 Backspace键 剪切光标所在位置的前一个字符
2. 粘贴
    * Ctrl + Y 在光标位置之后，粘贴剪切或剪切的文本

## 感叹号(!)命令
* !! 执行前一个命令
* !!foo 执行前一个以foo开头的命令
* !foo:p 打印前一个以foo开头的命令

源自 <https://www.bigocheatsheet.com/>
<https://www.howtogeek.com/howto/ubuntu/keyboard-shortcuts-for-bash-command-shell-for-ubuntu-debian-suse-redhat-linux-etc/>