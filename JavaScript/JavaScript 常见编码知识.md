---
title: JavaScript 常见编码知识
date: 2021-11-08
tags: JavaScript
categories: 前端-JavaScript
---

# JavaScript 常见编码知识

最近在看文件操作相关的知识，里面涉及到字符编码相关的知识，想接触计算机以来，接触过各种编码：ASCII、GB2312、UTF-8、Base64 等等。为什么有这么多种编码方式？编码发展历程又是怎么样呢？下面就一起去学习一下。<br />​

下面是自己整理的一个编码相关的流程示意图：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/369637/1636105411716-6c316751-1ce0-4178-8a58-b2a527f3274c.png#clientId=u5b960f05-d672-4&from=paste&height=282&id=u371a69d4&margin=%5Bobject%20Object%5D&name=image.png&originHeight=778&originWidth=1658&originalType=binary&ratio=1&size=102489&status=done&style=stroke&taskId=u5106c15e-da5e-4b2b-a35a-1ea0e89f8f0&width=600)<br /><br />

<a name="LtgKC"></a>
# 1 &nbsp;[ASCII 字符集](http://17de.com/library/c/ascii.html)

<br />**ASCII：美国信息交换标准代码**。20 世纪 60 年代，美国人发明的。

- 收录 128 个字符，0~31 和 127 是非打印字符，32~126 是 打印字符。
- 为什么是 128 个字符，使用二进制标识，是使用 1 个 Byte（8 个 Bite）进行标识，2^8 = 128。

<br />

> 查看完整 ASCII 码对照表，可以查看：[脚本之家 - ASCII 码对照表](http://tools.jb51.net/table/ascii)

<br />

<a name="mIt2R"></a>
# 2  &nbsp;非 ASCII 字符集

<br />上面说 ASCII 编码一共是 128 个， 英语的表示是够了，但是表示其他语言的话，128 个字符远远是不够的。不同国家就同一个字母的表示方式是不同的，语言特有的字符更是数不胜数，就汉字来说，多达 10 万个，常用汉字多达六千多个。一个字节表示肯定是远远不够的，因此使用其他方式进行解决。<br />​<br />
<a name="YhZKA"></a>
## 2.1 &nbsp;[GB2312 字符集](https://zh.wikipedia.org/wiki/GB_2312)

<br />**GB2312：中国国家标准简体中文字符集。**中国计算机科学家设计了一种字符集，收录了汉字、拉丁文字母、希腊字母等多种文字及字母。公共包含汉字 6763 个，其他文字符号 682 个（注意：GB2312 字符集并没有收录 ASCII 字符集中的字符）。<br />
<br />具体编码方式与上面编码有所区别，因为涉及的字符太多了。使用的是 分区概念。一共划分 94 个区，每个区收录 94 个字符。所以定位方式就是放在第几区的第几个字符。汉字“啊”放在 16 区的第一位，因此对应的数字是 1601（即区位码是 1601）。

- 01~09区（682个）：特殊符号、数字、英文字符、制表符等，包括拉丁字母、希腊字母、日文平假名及片假名字母、俄语西里尔字母等在内的682个全角字符；
- 10~15区：空区，留待扩展；在附录3，第10区推荐作为 GB 1988–80 中的94个图形字符区域（即第3区字符之[半形](https://zh.wikipedia.org/wiki/%E5%8D%8A%E5%BD%A2)版本）。
- 16~55区（3755个）：常用汉字（也称一级汉字），按拼音排序；
- 56~87区（3008个）：非常用汉字（也称二级汉字），按部首/笔画排序；
- 88~94区：空区，留待扩展。

<br />

> 1. 查看 某个汉字的区位码，可以查看：[GB2312区位码查询与转换](http://www.mytju.com/classcode/tools/quweima.asp)​
> 1. 查看全部 GB2312 字符集，可以参考： [GB2312简体中文编码表](http://tools.jb51.net/table/gb2312)

​<br />
<a name="FgY06"></a>
## 2.2 &nbsp; [GBK 字符集](https://zh.wikipedia.org/wiki/%E6%B1%89%E5%AD%97%E5%86%85%E7%A0%81%E6%89%A9%E5%B1%95%E8%A7%84%E8%8C%83)

<br />**GBK： 汉字内码扩展规范。**中国汉字太多，许多不太经常使用的字符没有收录，台湾香港使用的繁体字也没有进行收录，GBK 字符集就是在 GB2312 字符集基础上，对收录字符进行了补充。<br />​<br />

- GBK 向下完全兼容 GB2312-80编码（包含 GB 2312 中的全部汉字、非汉字符号）
- [BIG5 字符集](https://zh.wikipedia.org/wiki/%E5%A4%A7%E4%BA%94%E7%A2%BC)中的全部汉字（普及于[台湾](https://zh.wikipedia.org/wiki/%E5%8F%B0%E7%81%A3)、[香港](https://zh.wikipedia.org/wiki/%E9%A6%99%E6%B8%AF)、[澳门](https://zh.wikipedia.org/wiki/%E6%BE%B3%E9%96%80)等繁体中文区域，但并非标准）
- 与 ISO 10646 相应的国家标准 GB 13000 中的其它 CJK 汉字，以上合计 20902 个汉字
- 其它汉字、部首、符号，共计 984 个

​<br />
<a name="bGxQI"></a>
## 2.3 &nbsp; [GB18030 字符集](https://zh.wikipedia.org/wiki/GB_18030)

<br />**GB 18030**：**国家标准 GB 18030-2005《信息技术中文编码字符集》。**是中华人民共和国现时最新的内码字集。<br />**​**<br />

- GB 18030 与 GB 2312-1980 和 GBK 兼容，共收录汉字70244个
- 采用多字节编码，每个字可以由 1 个、2 个或 4 个字节组成
- 编码空间庞大，最多可定义 161 万个字符
- 支持中国国内少数民族的文字，不需要动用造字区
- 汉字收录范围包含繁体汉字以及日韩汉字

​<br />

<a name="JbrZW"></a>
# 3  &nbsp; [Unicode ](https://zh.wikipedia.org/wiki/Unicode)
**Unicode：联盟官方中文名称为统一码，台湾官方中文名称为万国码，也译为国际码、单一码，是计算机科学领域的业界标准。**<br />**​**

就上面我们了解了这么多的编码方式，同一个二进制的数字能被解析成不同的符号。因为当打开一个文件必须准确的知道编码方式，否则就可能出现因编码方式错误，导致的乱码现象。<br />​

那么就需要有一种编码，能将世界上全部符号进行收纳，统一给每个符号一个独一无二的编码。这样才能彻底解决乱码问题。因此 Unicode【国际码】 成为了国际认可的编码标准。<br />
<br />Unicode 是个很大的集合，现在可容纳 100 多完符号，每个符号的编码都不同。汉字”花“编码为：U+82B1。<br />​<br />
> 1. 在线 Unicode 查询，可参考：[Unicode 查询](https://unicode.yunser.com/unicode)
> 1. 中日韩 Unicode 编码表，可查询：[中日韩文字 Unicode 编码表](http://www.chi2ko.com/tool/CJK.htm)

​

**虽然 Unicode 是编码标准，存在问题：**

1. 如何区分 Unicode 与 ASCII ？

❓ &：ASCII 编码：00100110；Unicode 编码：U+0026

2. 英文使用一个字节就能表示了，但是按照 Unicode 统一规定，每个符号要用三个或4个字节才能表示。对于存储来说太过浪费了，是无法接受的。


<br />**造成的后果：**

1. 出现了多种存储方式，有许多不同二进制格式表示 Unicode；
1. Unicode 很长时间不能推广。

<br />

<a name="edYTH"></a>
## 3.1 &nbsp; [UTF-8 ](https://zh.wikipedia.org/wiki/UTF-8)
** UTF-8：一种针对 Unicode 的可变长度字符编码，也是一种[前缀码](https://zh.wikipedia.org/wiki/%E5%89%8D%E7%BC%80%E7%A0%81)。互联网的普及促使出现一种统一编码，UTF-8 就是互联网上使用最广的一种 Unicode 的实现方式，其他的实现方式还包含了：UTF-16（使用 2~4 个字节表示）、UTF-32（使用4个字节表示），不过互联网上基本不使用。<br />​

**特点**：一种变长的编码方式（128 个 ASCII 字符集使用一个字节，其他随符号不同而变化）<br />​

**编码规则**

- 先把编号转成二进制，再按照下面规则填入，位数不够补 0
- 单字节符号，第一位设为 0；后边7位是这个符号的 Unicode 码，因此英语字母 UTF-8编码与 ASCII码相同
- 大于单字节n 位，第一个字节前n位都是1，n+1位是0，后边字节前两位都是10
- 其余没有提及的为禁止，全部是这个符号的 Unicode 码。

![image.png](https://cdn.nlark.com/yuque/0/2021/png/369637/1636102267021-f450cd12-b786-451d-be11-68f72875368c.png#clientId=u5b960f05-d672-4&from=paste&height=241&id=u25ab7ad6&margin=%5Bobject%20Object%5D&name=image.png&originHeight=472&originWidth=1174&originalType=binary&ratio=1&size=160192&status=done&style=none&taskId=u3665657a-6192-4c15-9e14-0b1513d1560&width=600)<br />
<br />**举例**

- 以大写字母 P 为例，Unicode 编号：U+0050，二进制是：101 0000，属于单字节符号。首位设为 0 即可。

      因此，UTF-8 编码为：0101 0000（即：50）。

- 以汉字 严 为例，Unicode 编号：U+4E25，二进制是：100 1110 0010 0101，占两个字节，属于上面第三行。那么编码需要 3 个字节，UTF-8 编码为：11100100 10111000 10100101（即：E4B8A5）。


<br />
<a name="FsxfO"></a>

## 3.2 &nbsp; [UTF-16](https://zh.wikipedia.org/wiki/UTF-16)

![image.png](https://cdn.nlark.com/yuque/0/2021/png/369637/1636104530700-ce2caa03-ea6a-4a4a-97dc-df2efe24ed73.png#clientId=u5b960f05-d672-4&from=paste&height=166&id=uec2b76f0&margin=%5Bobject%20Object%5D&name=image.png&originHeight=316&originWidth=1140&originalType=binary&ratio=1&size=101461&status=done&style=stroke&taskId=ufee0312d-275e-4734-bdc9-5e22da7f235&width=600)<br />
**概念**：编码规则实在没看懂，后边在进行补充吧！<br />
**优点**：大部分字符使用2个字节就能实现表示。<br />
**缺点**：不能兼容 ASCII 编码<br />

<br />
<a name="e3aBb"></a>

## 3.3 &nbsp;[UTF-32](https://zh.wikipedia.org/wiki/UTF-32)

![image.png](https://cdn.nlark.com/yuque/0/2021/png/369637/1636104251898-b65732ab-a045-456e-9598-0a8eb00100c5.png#clientId=u5b960f05-d672-4&from=paste&height=114&id=u0f779e2a&margin=%5Bobject%20Object%5D&name=image.png&originHeight=214&originWidth=1130&originalType=binary&ratio=1&size=66006&status=done&style=none&taskId=u34d20e3a-e14c-4f44-bcb2-8db6df089df&width=600)<br /><br/>
**概念**：使用固定长度的字节表示字符（4 个字节 - 32 个 Byte）。<br />
**缺点**：空间浪费极大，基本不会使用。<br />

<a name="upxHh"></a>
## 3.4 &nbsp; 字节顺序标记

- Be 编码（大端序）：高字节在左边，低字节在右边
- Le 编码（小端序）：高字节在右边，低字节在左边


<br />**对应编码及文件前缀，如下：**<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/369637/1636102405922-acdfda3d-6177-4b87-b813-ffe3a8e28f50.png#clientId=u5b960f05-d672-4&from=paste&height=275&id=ub559f978&margin=%5Bobject%20Object%5D&name=image.png&originHeight=550&originWidth=692&originalType=binary&ratio=1&size=111834&status=done&style=stroke&taskId=uc17abf17-0d79-46a0-bc63-9575cba9294&width=346)<br />​

**举例**<br />以严为例（Unicode 编号：U+4E25，二进制是：0100 1110 0010 0101）：

- 大端序编码：FE FF 4E 25
- 小端序编码：FF FE 25 4E
- UTF-8  编码（十六进制）：EF BB BF E4 B8 A5



<a name="xMsal"></a>
# 4 &nbsp; [Base64 编码](https://developer.mozilla.org/zh-CN/docs/Glossary/Base64)
Base64 是一组相近的二进制编码规则。为什么要使用 Base64 编码呢？主要是计算机的数据基本都是按照 ASCII 进行存储的，为了保证数据传输的完整性与传输过程中数据不丢失，会先将字符转成 Base64 之后再进行传输。<br />​

**特点：**每个字符占 6 个字符，不能整除的话补充 0。快速预览表 如下👇🏻：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/369637/1636211743367-d6ae6b08-093c-458c-aa10-24f12d0e6d5c.png#clientId=u5c44d8a6-cdc4-4&from=paste&height=452&id=uc5dbd5ca&margin=%5Bobject%20Object%5D&name=image.png&originHeight=495&originWidth=657&originalType=binary&ratio=1&size=382695&status=done&style=none&taskId=u2534b2a5-1214-4c77-bf34-9c239847861&width=600)<br /> （引用自：[https://mp.weixin.qq.com/s/QHi6BVM5Jt8XwZ_FKcRYsg](https://mp.weixin.qq.com/s/QHi6BVM5Jt8XwZ_FKcRYsg)）<br />​<br />
<a name="ptWlj"></a>
# 5 &nbsp; 编码转换 & 编码方法
<a name="n0C8y"></a>
## 5.1  &nbsp; 编码转换

- **Base64、UTF-8、ASCII 关系**
   - utf-8 -> base64(编码) -> ASCII
   - ASCII -> base64(解码) -> utf-8


<a name="TNc1I"></a>
## 5.2 &nbsp; 编码方法

- [encodeURI()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/encodeURI)：将特定字符进行转义编码，转义字符：除（保留类型 + 非转义字符 + 数字符号）之外。
- [decodeURI()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/decodeURI)：将👆🏻方法转义的字符进行解码，反转义字符同上。
- [encodeURIComponent()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent)：编码，转义字符：除非转义类型之外其他字符。
- [decodeURIComponent()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/decodeURIComponent)：解码，反转义字符同上。

​<br />
> **注**
> - **区别**
>    - encodeURI 和 decodeURI 函数操作的是完整的 URI；这俩函数假定 URI 中的任何保留字符都有特殊意义，所有不会编码它们。
>    - encodeURIComponent 和 decodeURIComponent 函数操作的是组成 URI 的个别组件；这俩函数假定任何保留字符都代表普通文本，所以必须编码它们，所以它们出现在组成一个完整 URI 的组件里面时不会解释成保留字符了。
> - **URL：称为统一资源标识符**，是用来标识互联网上的资源和怎么访问这些资源的传输协议的字符串。
> - 组成形式：_Scheme_ : _First_ / _Second_ ; _Third_ ? _Fourth_
> - 保留类型：; , / ? : @ & = + $
> - 非转义字符：字母 数字 - _ . ! ~ * ' ( )
> - 数字符号：#


<br />​<br />

- [btoa()](https://developer.mozilla.org/zh-CN/docs/Web/API/btoa)：返回 Base64 表示的字符串。btoa('P')   // 'UA=='
- [atob()](https://developer.mozilla.org/zh-CN/docs/Web/API/atob)：返回 ASCII 表示的编码。atob('UA==')  // 'P'

    **  注意：**以上两个方法对于非有效字符串，会抛出 DOMException<br />​<br />

- [charCodeAt()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt)：返回的是 0~65535 之间的整数。0x[字符/汉字的 Unicode 编码]<br /><br />

举例 1：【是】Unicode 编码：U+662F，'是'.charCodeAt() = 26159(0x662F)<br />举例 2：【s】Unicode 编码：U+0073，'s'.charCodeAt() = 115 (0x73)<br /><br />

<a name="he3pj"></a>

# 6 &nbsp; 总结

<br />以上就是涉及编码相关的全部知识，对于UTF-16、UTF-32 写的不是很详细，在我们实际运算中实际也是用的比较少的。大家有兴趣可以通过链接进行详细研究。<br />​

后续涉及到相关的知识，会在进行补充。希望大家读完本文有所收获，谢谢！<br />​

**最后举一个例子**

| 文本 | P | 严 |
| --- | --- | --- |
| Unicode 编码 | U+0050<br />二进制：0101 0000 | U+4E25<br />二进制：100 1110 0010 0101 |
| UTF-8 编码 | 0101 0000  | 11100100 10111000 10100101 |
| Base64 编码 | UOS4pQ== |  |
| ASCLL 编码 | 80 |  | /

<br />

> [在线编码解码工具](http://tool.haooyou.com/code)


​<br /><br />
<a name="yFkWW"></a>

# 7 &nbsp; 参考
> [阮一峰：字符编码笔记：ASCII，Unicode 和 UTF-8](https://www.ruanyifeng.com/blog/2007/10/ascii_unicode_and_utf-8.html)
>
> [字符集与编码](https://juejin.cn/post/6844903793553833998)
>
> [维基百科](https://zh.wikipedia.org/wiki/%E5%AD%97%E7%AC%A6%E7%BC%96%E7%A0%81)
>
> [常见的字符编码ascii、gb2312、utf-8和base64的规则](https://blog.csdn.net/gshtime/article/details/104510718)

