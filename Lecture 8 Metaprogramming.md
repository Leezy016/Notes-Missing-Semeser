
build systems
从源码到可执行文件
dependencies

### make
1.无需自己写命令控制输入输出的走向
2.自动检查是否需要更新（最小化工作量）

### repositories
版本号：不同版本号提供的功能集不同。运行时在仓库中的对应版本找。

### semantic version
8.1.7    major（删除/重命名功能，原功能不可使用）.minor（添加新功能，原有功能仍可使用）.patch（无接口变化/只修改漏洞）
依赖：同一个major相等或更高minor版本均可运行，较低则可能不行

### lock file
避免意外更新
使用之前生成的文件

### vendor
将依赖的文件内容包含在软件中