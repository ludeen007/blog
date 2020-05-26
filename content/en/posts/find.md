+++
title = "grep"
categories = ["Bash命令"]
tags = ["Bash命令", "find"]
+++

find 使用例子 使用技巧等

find /opt -name "README\*" -exec wc -l {} +

Features of find
• path: may have multiple paths, eg. find /usr /opt -iname "\*.so"
• criteria
• -name, -iname, -type (f,d,l), -inum <n>
• -user <uname>, -group <gname>, -perm (ugo)
• -size +x[c], -empty, -newer <fname>
• -atime +x, -amin +x, -mmin -x, -mtime -x
• criteria may be combined with logical and (-a) and or (-o)
• action
• -print : default action, display
• -ls : run ls -lids command on each resulting file
• -exec cmd : execute command
• -ok cmd like exec except that command executed after user confirmation

find Examples
• find . -type f -name "_.txt" #all text files
in current dir
• find . -maxdepth 1 #equivalent to ls
• find ./somedir -type f -size +512M -print #all
files larger than 512M in ./somedir
• find . \( -name “_.c” -o -name “\*.h” \) #all
files that have either .c or .h extension
