### 基本操作
#### 查找文件
> find

> 例: find /root -name 'arthas*.jar'
#### 授权执行
> chmod 

> 例: chmod 755 as.sh
#### 查看文本
> cat

> 例: cat a.txt
#### 解压tar
> tar

> 例: tar -zxvf arthas.tar.gz
#### 指定的文件的最后部分输出到标准设备
> tail [ -f ] [ -c Number | -n Number | -m Number| -b Number | -k Number ] [ File ]

```
-f 该参数用于监视File文件增长。
-c Number 从 Number 字节位置读取指定文件
-n Number 从 Number 行位置读取指定文件。
-m Number 从 Number 多字节字符位置读取指定文件，比如你的文件如果包含中文字，如果指定-c参数，可能导致截断，但使用-m则会避免该问题。
-b Number 从 Number 表示的512字节块位置读取指定文件。
-k Number 从 Number 表示的1KB块位置读取指定文件。
```
> 例: tail -f tmp.log 

#### 查看指定进程

> 例: ps -ef|grep java

