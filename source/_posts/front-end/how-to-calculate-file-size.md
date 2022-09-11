title: 在mac OS/windows/linux操作系统中文件存储计算方式
date: 2021-02-25 09:43:16
categories: 
- 技术研究
tags: 
- 存储计算
- 文件大小
- macOs/windows
language: zh-CN
cover: /img/202102/compute-store.jpg
thumbnail: /img/202102/compute-store.jpg
---


计算机中用来表示内存储器容量大小的基本单位是：字节（Byte）。字节是二进制数据的单位，是计算机信息技术用于计量存储容量的一种计量单位，也表示一些计算机编辑语言中的数据类型和语言字符。

在不同的操作系统中，文件数据大小计算规则并不一样，具体如下：
```
windows / linux

1Byte(字节) = 8bit(位)
1Kib = 1024Byte
1Mib = 1024Kib
1Gib = 1024Mib
1Tib = 1024Gib
——————————————————————————
macOS

1Byte(字节) = 8bit(位)
1Kb = 1000Byte
1Mb = 1000Kb
1Gb = 1000Mb
1Tb = 1000Gb

```

### 为什么它们规则不一样？
这个要说到国际单位制和硬盘。
在国际单位制中是以'1000进制'为标准，为此，IEC（国际电工协会）拟定了'Kib、Mib'的二进制单位，专门用来标志'1024进制'的数据大小
硬盘存储也是以'1000进制'为基准的。
但是计算机系统是以'1024进制'为基准的。
苹果操作系统为了让用户体验更佳（买了1TB硬盘，看到的就是1TB），选择了'1000进制'来处理容量。

也正是因为这种标杆差异，造成了买回了1TB的硬盘，但在电脑上查看（苹果除外）容量时，发现容量变小了。

参考资料：
* [这个你肯定不知道：1KB=?byte；1MB=?KB；1GB=?MB](http://celeron633.blog.sohu.com/263502449.html)
* [Mac OS下储存大小的计算方式是否和Windows下不一样？](https://www.zhihu.com/question/29131863)
