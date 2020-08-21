+++
title = "sed"
categories = ["Bash命令"]
tags = ["Bash命令", "sed"]
+++

sed 使用例子 使用技巧等

sed: parse and transform text
• sed is a stream editor
• Looks for a pattern in text and applies changes (edits) to them
• A batch or non-interactive editor
• Reads from file or stdin (so, pipes are good) one line at a time
• The original input file is unchanged (sed is also a filter), results are
sent to standard output
• Most frequently used idiom is for text substitution

sed 's/New/Old/g' states.txt

Options
• address: may be a line number or a range, defaults to whole file
• command: s:substitute, p:print, d:delete, a:append, i:insert, q:quit
• regex: A regular expression
• delimiter: Does not have to be /, can be | or : or any other
character
• modifier: may be a number n which means apply the command to nth
occurrence, g means apply globally in the line
• Common sed flags: -n (no print), -e (multiple ops), -f (read sed
from file), -i (in place edit [careful])

Useful sed Examples
• sed -n '5,9p' states.txt #print lines 5 through 9
• sed -n '$p' states.txt #print last line
• sed '1,3d' states.txt #delete first 3 lines
• sed '/^$/d' states.txt #delete all blank lines
• sed '/York/!s/New/Old/' states.txt #substitute except York
• kubectl -n kube-system get configmap/kube-dns -o yaml | sed
's/8.8.8.8/1.1.1.1/' | kubectl replace -f -
