change format
```bash
# 注意 uniq 只能过滤相邻的行，所以必须先排序
# 排序->去重->根据重复次数降序排列
grep something| sort | uniq -c | sort -gr

# 取以's结尾的补集
grep -v "'s$'"
```
