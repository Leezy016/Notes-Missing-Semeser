### Debugging - debugger
pyflakes/mypy - 静态debug，可整合到vim中
pdb - python debugger
[GitHub - spiside/pdb-tutorial: A simple tutorial about effectively using pdb](https://github.com/spiside/pdb-tutorial)

1. `l(ist)` - Displays 11 lines around the current line or continue the previous listing.
2. `s(tep)` - Execute the current line, stop at the first possible occasion.
3. `n(ext)` - Continue execution until the next line in the current function is reached or it returns.
4. `b(reak)` - Set a breakpoint (depending on the argument provided).
5. `r(eturn)` - Continue execution until the current function returns.
















writegood
英语写作帮手
拼写检查，风格分析

根据用途搜索对应工具

### Profiling - prfililer
optimize the code

real/user/system time 

cpu profiler
	tracing：记录时间
	sampling：记录概率

python: cProfile

line profile

perf：统计程序的进程使用    汇编语言

图形化：FlameGraph (sampling profiler)

小心c/cpp内存泄漏
	In languages like C or C++ memory leaks can cause your program to never release memory that it doesn’t need anymore. To help in the process of memory debugging you can use tools like [Valgrind](https://valgrind.org/) that will help you identify memory leaks.

du -h
disk usage human readable 
htop 进程管理软件 CPU总用量查看  q退出
类似程序：ps


在vim中使用markdown
[使用 vim 开始 markdown 之旅 - 少数派 (sspai.com)](https://sspai.com/post/60305#!)
