# Linux命令对文本去重统计行数

>2018年01月11日 19:59:10

```shell
sort target.txt | uniq | wc -l
```