	230710

```bash
echo Hello\ world
echo "Hello world"
#使用\使得空格被忽略==使用""括起有空格的名称

which echo
#环境变量 environment variable

echo $PATH
#打印所有搜索路径

#root directory: /

#rwx: 
#read write execute
#for dir, x means you can change into the dir

cd -
#back to the premise dir

pwd
#print working directory

man ls
ls --help
#man has more info and reading friendly

echo hello > hello.txt
#ctrl+L: clear and go to top

xdg-open filename
#opan a file

```


##### Ex10
Use `|` and `>` to write the “last modified” date output by `semester` into a file called `last-modified.txt` in your home directory
```bash
# answer:
./semester | grep -i last-modified > ~/last-modified.txt
```
