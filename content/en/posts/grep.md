+++
title = "grep"
categories = ["Bash命令"]
tags = ["Bash命令", "grep"]
+++

grep 使用例子 使用技巧等

## 递归查找特定文件中的字符串

grep -r -i --include \*.json \"moment\" /some/dir/

grep -i -n 'col' states.txt
Useful grep Options
• -i: ignore case
• -n: display line numbers along with lines
• -v: print inverse ie. lines that do not match the regular expression
• -c: print a count of lines of matches
• -A<n>: include n lines after the match
• -B<n>: include n lines before the match
• -o: print only the matched expression (not the whole line)
• -E: allows "extended" regular expressions that includes (more later)

grep Examples
• Lines that end with two vowels:
grep '[aeiou][aeiou]\$' prose.txt
• Check 5 lines before and after the line where term 'little' occurs:
grep -A5 -B5 'little' prose.txt
• Comment commands and search later from history
some -hard 'to' \remember --complex=command #success
history | grep '#success'
• find+grep is one very useful combination
find . -iname "\*.py" -exec grep 'add[_-]item' {} +
