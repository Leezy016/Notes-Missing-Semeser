光标选中内容，点击中键，内容复制到上次光标的位置


```bash
foo=bar
# not "foo = bar" no space between

echo “value is $foo”
# value is bar
echo 'value is $foo'
# value is $foo

vim mcd.sh
cat mcd.sh
# mcd(){
#     mkdir -p "$1"
#	  cd "$1"
# }

false || echo 'Oops fail'
# Oops fail
true && echo 'Things went well'
# Things went well

echo "It is $(date) now"
# It is Thu Jul 13 12:35:51 CST 2023 now

cat <(ls) <(ls ..)
# mcd.sh
# multiline_comment.sh
# ex6
# ex8
# hello.txt
# makelearning
# missingSemester
# testdir
# testfile
# touchCommandCanMakeANewFile.txt
```

example.sh
注意：if判断括号和条件用空格隔开
```bash
#!/bin/bash

echo "Starting program at $(date)"
echo "Running program $0 with $# arguments with pid $$"

for file in "$@"; do
	grep foobar "$file" > /dev/null 2> /dev/null
	if [[ "$?" -ne 0 ]]; then
		echo "File $file does not have any foobar, adding one"
		echo "# foobar" >> "$file"
	fi
done
```

```bash
ls *.sh
```

批量操作
```text
touch foo.{1,2,3,4,5}
leezy@ubuntu23:~/Documents/missingSemester$ ls -l
total 232
-rw-rw-r-- 1 leezy leezy      9 Jul 13 12:56 adding_foobar.txt
-rw-rw-r-- 1 leezy leezy  21308 Jul 13 14:24 eldenRing.jpg
-rw-rw-r-- 1 leezy leezy 189967 Jul 13 14:25 eldenRing.png
-rwxrwxrwx 1 leezy leezy    294 Jul 13 12:55 example.sh
-rw-rw-r-- 1 leezy leezy      0 Jul 13 14:29 foo.1
-rw-rw-r-- 1 leezy leezy      0 Jul 13 14:29 foo.2
-rw-rw-r-- 1 leezy leezy      0 Jul 13 14:29 foo.3
-rw-rw-r-- 1 leezy leezy      0 Jul 13 14:29 foo.4
-rw-rw-r-- 1 leezy leezy      0 Jul 13 14:29 foo.5
-rw-rw-r-- 1 leezy leezy      7 Jul 13 12:55 have_foobar.txt
-rw-rw-r-- 1 leezy leezy     39 Jul 13 11:57 mcd.sh
-rw-rw-r-- 1 leezy leezy    116 Jul 13 12:11 multiline_comment.sh
leezy@ubuntu23:~/Documents/missingSemester$ rm foo.{1,2,3,4,5}
leezy@ubuntu23:~/Documents/missingSemester$ ls -l
total 232
-rw-rw-r-- 1 leezy leezy      9 Jul 13 12:56 adding_foobar.txt
-rw-rw-r-- 1 leezy leezy  21308 Jul 13 14:24 eldenRing.jpg
-rw-rw-r-- 1 leezy leezy 189967 Jul 13 14:25 eldenRing.png
-rwxrwxrwx 1 leezy leezy    294 Jul 13 12:55 example.sh
-rw-rw-r-- 1 leezy leezy      7 Jul 13 12:55 have_foobar.txt
-rw-rw-r-- 1 leezy leezy     39 Jul 13 11:57 mcd.sh
-rw-rw-r-- 1 leezy leezy    116 Jul 13 12:11 multiline_comment.sh
```

```bash
diff <(cat foo.txt) <(cat bar.txt)
# 1c1
# < ring
# ---
# > bing
```

运行python3的一个方法
script.py
```bash
#!/usr/bin/env python3
import sys
for arg in reversed(sys.argv[1:]):
    print(arg)
```
使用./运行
```bash
./script.py 1 2 3
# 3
# 2
# 1
```

检查shell语法错误：
```bash
shellcheck filename.sh
```


```bash
# 文件名搜索 find/locate
 find ~ -size +50k -name '*.tar.*' -exec rm {} \;
 
# 目录查看
# 按顺序给出pathName目录下和子目录中的所有文件夹/文件详细信息
ls -R -l pathName

# 目录查看
# 树形结构查看，带路径
tree -f pathName

# 文档搜索
grep -R bing ~/Documents/
# /home/leezy/Documents/missingSemester/bar.txt:bing
# /home/leezy/Documents/ex6/hello.txt:hello bing

```
### Exercises
##### 1
```bash
ls -chlt
# total 244K
# -rwxrwxrwx 1 leezy leezy  353 Jul 13 15:32 example.sh
# -rwxrwxr-- 1 leezy leezy   85 Jul 13 15:21 script.py
# -rw-rw-r-- 1 leezy leezy   19 Jul 13 15:05 bar.txt
# -rw-rw-r-- 1 leezy leezy   19 Jul 13 15:04 foo.txt
# -rw-rw-r-- 1 leezy leezy 186K Jul 13 14:25 eldenRing.png
# -rw-rw-r-- 1 leezy leezy  21K Jul 13 14:24 eldenRing.jpg
# -rw-rw-r-- 1 leezy leezy    9 Jul 13 12:56 adding_foobar.txt
# -rw-rw-r-- 1 leezy leezy    7 Jul 13 12:55 have_foobar.txt
# -rw-rw-r-- 1 leezy leezy  116 Jul 13 12:11 multiline_comment.sh
# -rw-rw-r-- 1 leezy leezy   39 Jul 13 11:58 mcd.sh
```
##### 2
```
```

##### 3
```bash
# 在脚本中执行另一个脚本，先把被执行脚本状态改为可执行
chmod 774 target.sh

# 脚本中引用
./target.sh


#!/usr/bin/env bash
count=0
echo "success output" > out.log
while true
do
	./target.sh &>> out.log
	if [[ $? -ne 0 ]]; then
		echo "failed after $count times"
		break
	fi
	((count++))
done
```

##### 4
```bash
# 找到当前目录下所有.sh文件并打包为myshell.tar
# xargs 命令可以把管道左侧命令的输出流赋给右侧的命令
find *.sh | xargs tar -cf myshells.tar
```