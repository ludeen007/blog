+++
title = "Bash Shortcuts Cheat Sheet"
categories = ["cheat-sheet"]
tags = ["cheat-sheet","shortcut"]
date = 2020-03-08T09:46:09+08:00
+++

Bash Shell 快捷键

## 进程控制

- Ctrl + C 终止命令执行
- Ctrl + Z suspend command/send to background(use fg to bring forward)
- Ctrl + D 关闭 Bash Shell

## 控制屏幕输出

- Ctrl + L 清屏
- Ctrl + S 停止输出到屏幕(for verbose commands)
- Ctrl + Q 允许输出到屏幕(undo Ctrl + S)

## 移动光标

1.  行

    - Ctrl + A 或 Home 键 移到行首
    - Ctrl + E 或 End 键 移到行尾
    - Ctrl + XX 在行首和光标位置之间移动

2.  单词

    - Alt + B 移到前一个单词的词首
    - Alt + F 移到下一个单词的词尾

3.  字符
    - Ctrl + F 前进一个字符
    - Ctrl + B 后退一个字符

## 大小写操作

- Alt + C 从光标位置开始，第一个字符大写(Capitalize)到词尾
- Alt + U 从光标位置开始，全部字符大写(Upper case)到词尾
- Alt + L 从光标位置开始，全部字符小写(Lower case)到词尾

## fix typos

- Alt + T 交换当前单词和前一个单词
- Ctrl + T 交换当前字符和前一个字符
- Ctrl + \_ 撤销上一次击键，可撤销多次

## 命令历史

- Ctrl + R 进入反向搜索命令历史模式
- Ctrl + O 执行反向搜索命令历史模式找到的命令
- Ctrl + G 退出反向搜索命令历史模式
- Ctrl + P 或 向上箭头键 回退一个命令
- Ctrl + N 或 向下箭头键 前进一个命令
- Alt + . 前一个命令的最后一个单词

## 剪切和粘贴

1. 剪切
   - Ctrl + U 从光标位置开始，剪切到行首
   - Ctrl + K 从光标位置开始，剪切到行尾
   - Ctrl + W 从光标位置开始，剪切到词首
   - Alt + D 从光标位置开始，剪切到词尾
   - Ctrl + D 或 Delete 键 剪切光标所在位置的字符
   - Ctrl + H 或 Backspace 键 剪切光标所在位置的前一个字符
2. 粘贴
   - Ctrl + Y 在光标位置之后，粘贴剪切或剪切的文本

## 感叹号(!)命令

- !! 执行前一个命令
- !!foo 执行前一个以 foo 开头的命令
- !foo:p 打印前一个以 foo 开头的命令
- !$ change command keep last argument:
  cat states.txt # file too long to fit screen
  less !$ # reopen it with less
- !\* change command keep all arguments:
  head states.txt | grep '^A1' # should be tail
  tail !\* # no need to type the rest of the command

## IO 流和重定向

- 终端的 3 个流及其文件描述符: stdin 0, stdout 1, stderr 2
- 尖括号用来重定向:
  - > 发送到流
  - < 从流获取
  - > > 追加到流
  - << 原地追加 heredoc
- & is used to "write into" a stream, eg. &1 to write into stdout
- eg.
  - read from stdin as output of a command:
  - diff <(ls dirA) <(ls dirB)
- 管道|:
- eg. the top 10 frequently used commands
- history | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | sort -rn | head
- xargs: 1. converts standard input to commands into literal args 2. partitions the args to a permitted number and runs the command over them repeatedly
- eg. create files with names on the somelist.txt file:
- xargs touch < somelist.txt

源自 <https://www.bigocheatsheet.com/>
<https://www.howtogeek.com/howto/ubuntu/keyboard-shortcuts-for-bash-command-shell-for-ubuntu-debian-suse-redhat-linux-etc/>
