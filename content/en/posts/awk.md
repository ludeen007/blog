+++
title = "awk"
categories = ["Bash命令"]
tags = ["Bash命令", "awk"]
+++

awk 使用例子 使用技巧等

awk: Extract and Manipulate Data
• A programmable filter that reads and processes input line by line
• Rich built-in features:
• explicit fields ($1 ... $NF) & records management
• functions (math, string manipulation, etc.)
• regular expressions parsing and filtering
• Features like variables, loops, conditionals, associative arrays,userdefined functions

Highly recommended book: The awk programming language by Aho, Kernighan and Weinberger, ia802309.us.archive.org/25/items/pdfy-MgN0H1joIoDVoIC7/The_AWK_Programming_Language.pdf

Anatomy of an awk program

Often used as one-line idiom of the form:
awk 'awk_prog' file.txt
OR
command | awk 'awk_prog'

where awk_prog is:
BEGIN{actions} #run one time before input data is read
/pattern or condition/ {actions} #run for each line of input
END{actions} #run one time after input processing

At least one of the BEGIN, /pattern or condition/, {}, END section needed

awk patterns and actions
• A pattern is a regex that matches (or not) to an input line, eg.
/New/ # any line that contains ‘New’
/^[0-9]+ / # beginning with numbers
/(POST|PUT|DELETE)/ # has specific words
• An action is a sequence of ops, eg.
{print $1, $NF} #print first and last field/col
{print log($2)} #get log of second field/col
{for (i=1;i<x;i++){sum += $3}} #get cumulative sum
• User defined functions may be defined in any action block

awk Examples
• awk '{print $1}' states.txt
• awk '/New/{print $1}' states.txt
• awk NF>0 prose.txt #skip blank lines
• awk '{print NF, $0}' states.txt #num fields
• awk '{print length($0)}' states.txt #num chars
• awk 'BEGIN{print substr("New York",5)}' #York
