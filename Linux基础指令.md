# 热键

在讲指令之前，先来说一下Linux系统中的快捷键

>   1.   ctrl+insert—复制
>   2.   shift+insert—粘贴
>   3.   tab—自动补全指令或文件目录名
>   4.   ctrl+c—强制终止程序
>   5.   ctrl+d—键盘输入结束(EOF)，也可以表示exit
>   6.   上档键—重读前一次的指令，可以连续按

# Linux基础指令

Linux不同于Windows的图形化界面，Linux是通过指令控制操作系统

## ls指令

**语法:**`ls[选项][目录或文件]`
**功能:**对于目录，列出该目录下的所有子目录和文件。对于文件，将列出文件名以及其他信息
**常用选项:**

>   ​	-l	列出文件的详细信息

**示例：**![image-20230725170436462](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725170436462.png)

>   **注意：**`ls -l` 指令等价于 `ll`指令![image-20230725170616643](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725170616643.png)

**对比Windows：**该指令类似于Windows中的![image-20230725170954392](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725170954392.png)



---

## cd指令

**语法**:`cd 目录名`
**功能**：改变工作目录。将当前工作目录改变到指定的目录下。
**示例：**![image-20230725171842717](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725171842717.png)

**对比Windows:**<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725171913891.png" alt="image-20230725171913891" style="zoom: 67%;" /><img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725171915461.png" alt="image-20230725171915461" style="zoom:50%;" />

**扩展：**

1.    `.` 表示当前路径, `..` 表示上级路径， `cd .`表示进入当前路径，`cd ..`表示进入上级路径（根目录的上级路径还是根目录）

2.   `cd /root/test_7_25/dirname`：进入绝对路径

3.   `cd ../day02`：进入相对路径（进入相对于当前目录的上层路径下的day02目录）

4.   `cd ~`：进入用户家目录

5.   `cd -`：返回最近访问的目录

     ![image-20230725172748487](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725172748487.png)

6.   Linux系统上，磁盘的目录和文件被组织为一颗多叉树，每个节点都是目录或者文件![image-20230725172912407](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725172912407.png)

     -   文件一定是树的叶子节点
     -   目录可能是叶子也可能不是叶子

---

## pwd指令

**语法**: `pwd`
**功能**：显示用户当前所在的目录
**示例：**![image-20230725173743564](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725173743564.png)

>   注意：这里cd 后面可以不要 `./`,因为cd默认从当前路径开始寻找目录，若像不从当前路径开始寻找则使用绝对路径或者相对路径

**对比Windows：**![image-20230725173821470](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725173821470.png)

## man指令

Linux的命令有很多参数，我们不可能全记住，我们可以通过查看联机手册获取帮助。访问Linux手册页的命令是man
 **语法**: `man [选项] 命令`
**常用选项：**

>   -   -k 根据关键字搜索联机帮助
>   -   num 只在第num章节找
>   -   -a 将所有章节的都显示出来，比如 man printf 它缺省从第一章开始搜索，找到就会停止，如果使用-a则会向后接着找知道所有章节检索完毕
>
>   手册一共分为8章
>
>   1 是普通的命令
>   2 是系统调用，如open，write之类的（通过这个，至少可以很方便的查找到调用这个函数需要什么头文件）
>   3 是库函数，比如printf，fread
>   4 是特殊文件，也就是/dev下的各种设备
>   5 是指文件格式，比如passwd，就会说明这个文件中各个字段的含义
>   6 是留给游戏的，由游戏自己定义
>   7 是附件还有一些变量,比如向environ这种全局变量在这里就有说明
>   8 是系统管理用的命令,这些命令只能由root使用,如ifconﬁg 

**示例：**

>    ![](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725220649882.png)
>
>    ![image-20230725220655071](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725220655071.png)



>   ![image-20230725220815784](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725220815784.png)

---

# 新建文件目录指令

## mkdir指令

**语法**：`mkdir [选项] dirname...` 
**功能**：在当前目录下创建一个名为 “dirname”的目录
**常用选项:**

>   mkdir -p test/test1:递归建立多个目录

**示例:**![image-20230725171427225](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725171427225.png)

**对比Windows：**<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725171537758.png" alt="image-20230725171537758" style="zoom:50%;" /><img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725171547468.png" alt="image-20230725171547468" style="zoom:67%;" />

## touch指令

**语法**:`touch [选项]... 文件...` 
**功能**：touch命令参数可更改文档或目录的日期时间，包括存取时间和修改时间，或者建立一个新的不存在的文件
**常用选项:**

>-a  或--time=atime或--time=access或--time=use只更改存取时间。
>
>-c  或--no-create 不建立任何文档。
>
>-d 使用指定的日期时间，而非现在的时间。
>
>-f 此参数将忽略不予处理，仅负责解决BSD版本touch指令的兼容性问题。
>
>-m  或--time=mtime或--time=modify 只更改变动时间。
>
>-r 把指定文档或目录的日期时间，统统设成和参考文档或目录的日期时间相同。
>
>-t 使用指定的日期时间，而非现在的时间

**示例（建立新文件）:**![image-20230725174409378](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725174409378.png)

**对比Windows：**<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725174512172.png" alt="image-20230725174512172" style="zoom:50%;" />

![image-20230725174516628](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725174516628.png)

---

# 删除移动指令

## rmdir指令

**语法：**`rmdir [-p][dirname]`
**功能：**与mkdir的功能相反，rmdir是删除命令，用来删除空目录。
**常用选项：**

>   -p 当子目录被删除后如果父目录也变成空目录的话，就连带父目录一起删除。



**示例:**![image-20230725213412788](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725213412788.png)

>   注意：rmdir只能删除空目录

**对比Windows：**<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725215221956.png" alt="image-20230725215221956" style="zoom:50%;" />



## rm指令

**语法：**`rm[-f -i -r ] [dirname]`
**功能：**删除指定目录或文件
**常用选项：**

>   -   -f 直接删除文件
>   -   -i 删除前逐一询问
>   -   -r 删除目录下及其所有文件

**示例：**![](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725214857253.png)

![image-20230725214825821](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725214825821.png)

>   注意：rm可以搭配-rf指令可以直接删除目录或者文件，不管目录内是否有内容

**对比Windows：**![image-20230725215345712](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725215345712.png)

## cp指令

**语法**：`cp [选项] 源文件或目录   目标文件或目录`
**功能：**复制文件或目录
**说明**: cp指令用于复制文件或目录，如同时指定两个以上的文件或目录，且最后的目的地是一个已经存在的目录，则它会把前面指定的所有文件或目录复制到此目录中。若同时指定多个文件或目录，而最后的目的地并非一个已存在的目录，则会出现错误信息
**常用选项：**

>-f 或 --force 强行复制文件或目录，不论目的文件或目录是否已经存在
>
>-i 或 --interactive 覆盖文件之前先询问用户
>
>-r递归处理，将指定目录下的文件与子目录一并处理。若源文件或目录的形态，不属于目录或符号链
>
>接，则一律视为普通文件处理
>
>-R 或 --recursive递归处理，将指定目录下的文件及子目录一并处理

**示例：**![image-20230725225309248](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725225309248.png)

复制多个文件：![image-20230725225536221](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725225536221.png)

---

## mv指令

mv命令是move的缩写，可以用来移动文件或者将文件改名（move (rename) ﬁles），是Linux系统下常用的命令，经常用来备份文件或者目录。

**语法：**`mv [选项] 源文件或目录 目标文件或目录`
**功能：**

1.   视mv命令中第二个参数类型的不同（是目标文件还是目标目录），mv命令将文件重命名或将其移至一个新的目录中

2.   当第二个参数类型是文件时，mv命令完成文件重命名，此时，源文件只能有一个（也可以是源目录名），它将所给源文件或者源目录**重命名**为目标文件名

3.   当第二个参数是已存在的目录名称时，源文件或目录参数可以有多个，mv命令将各参数指定的源文件均移动至目标目录中。

**常用选项：**

>   -   -f：如果目标文件已存在，不会询问直接覆盖
>   -   -i：若目标文件存在，则会询问是否覆盖

**示例：**<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230725231422292.png" alt="image-20230725231422292" style="zoom:50%;" />

---

# 查看文件的指令

## cat指令

**语法**：`cat [选项] [文件]`
**功能**： 查看目标文件的内容
**常用选项：**

>   -   -b 对非空输出行编号
>   -   -n 对输出的所有行编号
>   -   -s 不输出多个空行

**补充：**

1.   cat默认从键盘读取数据
2.   tac指令可以从后往前查看文件

**示例**<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230726175720813.png" alt="image-20230726175720813" style="zoom:50%;" />

---

## more指令

**语法**：more [选项] [文件]
**功能**：more命令，功能类似 cat，more用来查看大文件
**常用选项：**

>   -   -n 对输出的行进行编号
>   -   q 退出more

**示例：**<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230726183346310.png" alt="image-20230726183346310" style="zoom:50%;" />

---

## less指令

-   less 工具也是对文件或其它输出进行分页显示的工具，应该说是linux正统查看文件内容的工具，功能极其强大。

-   less 的用法比起 more 更加的有弹性。在 more 的时候，我们并没有办法向前面翻， 只能往后面看
-   但若使用了 less 时，就可以使用 `pageup pagedown`等按键的功能来往前往后翻看文件，更容易用来查看一个文件的内容！

-   除此之外，在 less 里头可以拥有更多的搜索功能，不止可以向下搜，也可以向上搜。

**语法：**`less [参数] 文件`
**功能：**less与more类似，但使用less可以随意浏览文件，而more仅能向前移动，却不能向后移动，而且less再查看之前不会加载整个文件
**选项：**

>   -   -i 忽略搜索时的大小写
>
>   -   -N 显示每行的行号
>
>   -   /字符串：向下搜索“字符串”的功能
>
>   -   ?字符串：向上搜索“字符串”的功能
>
>   -   q:quit 

**示例：**

![image-20230727091507833](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727091507833.png)

向下搜索：![image-20230727091619063](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727091619063.png)![image-20230727091620805](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727091620805.png)

向上搜索：![image-20230727091659463](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727091659463.png)![image-20230727091700853](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727091700853.png)

---

## head指令

head指令用来将文件开头的某个区块显示到标准输出中。

**语法：** `head [参数] [文件]`
**功能：**head用来显示档案的开头至标准输出中，默认head显示文件的前10行。
**选项：**

>   -n<行数> 显示的行数

**示例：**
<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727092250570.png" alt="image-20230727092250570" style="zoom:67%;" />

<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727092255957.png" alt="image-20230727092255957" style="zoom: 50%;" />

## tail指令

tail指令会将文件内容从后往前输出到标准输出文件上，tail默认输出10行

**语法：** `tail [必要参数] [选择参数] [文件]`
**功能：**用于显示指定文件末尾内容，不指定文件时，作为输入信息进行处理。常用查看日志文件。
**选项：**

>   -   -f 循环读取
>   -   -n<行数>显示的行数

**示例：**<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727093534292.png" alt="image-20230727093534292" style="zoom:50%;" />

## 输出重定向

以上查看文件的所有指令都是默认输出到标准输出文件(显示器)。我们可以通过输出重定向更改内容的输出位置，正如和C语言一样，printf默认输出到显示器上，但是fprintf可以更改输出位置。Linux下输出重定向符号为 `>`

`cat big.txt > a.txt`表示将big.txt的内容输出到a.txt上

>   ![image-20230727094223191](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727094223191.png)![image-20230727094224906](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727094224906.png)

`head -20 big.txt > a.txt`表示将big.txt的前20行输出到a.txt上

>   <img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727094410215.png" alt="image-20230727094410215" style="zoom:67%;" />

## 管道

现在如果我们想显示一个文件的第20-50行可以怎么处理？

<font color=  blue>fun1.</font>先通过`head指令`将文件的前50行保存到临时文件`tmp.txt`中，再通过`tail指令`取出临时文件的后31行
<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727095057547.png" alt="image-20230727095057547" style="zoom:50%;" />

<font color = blue>fun2.</font>上述方法借用了临时文件`tmp.txt`,我们可以通过`管道`达成同样的效果。
`|`是Linux中的管道符，我们可以通过`|`将两个命令隔开，**`|`左边命令的输出结果作为右边命令的输入结果。**
因此上述任务可以这么完成

<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727095457211.png" alt="image-20230727095457211" style="zoom:50%;" />

---

# 时间相关的指令

## date指令

**语法：**`date [选项] [格式]`
**显示格式：**在date后面加上一个加号和格式设定可以设定显示的格式，常用的格式如下

>   -   %H : 小时(00..23) 
>   -   %M : 分钟(00..59) 
>   -   %S : 秒(00..61) 
>   -   %X : 相当于 %H:%M:%S 
>   -   %d : 日 (01..31)
>   -    %m : 月份 (01..12)  
>   -   %Y : 完整年份 (0000..9999) 
>   -   %F : 相当于 %Y-%m-%d 

**示例：**![image-20230727103818552](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727103818552.png)

**时间戳：**
时间戳是格林威治1970年1月1日(00:00:00GMT)至当前的总秒数。它也被称为Unix时间戳。

指令`date +%s`可以把当前时间转换为时间戳![image-20230727104648955](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727104648955.png)

指令`date -d@时间戳`可以将当前时间戳转换为时间![image-20230727104830705](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727104830705.png)

## cal指令

cal指令用来显示阳历日历,默认显示当前日期所在的日历

**语法：**`cal [参数] [月份] [年份]`
**选项：**

>   3 显示系统前一个月，当前月，下一个月的月历
>
>   -j 显示在当年中的第几天（一年日期按天算，从1月1号算起，默认显示当前月在一年中的天数）
>
>   -y 显示当前年份的日历

**示例：**![image-20230727105915245](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727105915245.png)

---

# 查找指令

## find指令

 Linux `find 命令`用于在指定目录下查找文件和目录。

**语法：**`find [path] [expression]`
**参数说明：：**

>   **path** 是要查找的目录路径，可以是一个目录或文件名，也可以是多个路径，多个路径之间用空格分隔，如果未指定路径，则默认为当前目录。
>
>   **expression** 是可选参数，用于指定查找的条件，可以是文件名、文件类型、文件大小等等。
>
>   expression 中可使用的选项有二三十个之多，以下列出最常用的部份：
>
>   -   `-name pattern`：按文件名查找，支持使用通配符 `*` 和 `?`。
>   -   `-type type`：按文件类型查找，可以是 `f`（普通文件）、`d`（目录）、`l`（符号链接）等。
>   -   `-size [+-]size[cwbkMG]`：按文件大小查找，支持使用 `+` 或 `-` 表示大于或小于指定大小，单位可以是 `c`（字节）、`w`（字数）、`b`（块数）、`k`（KB）、`M`（MB）或 `G`（GB）。
>   -   `-mtime days`：按修改时间查找，支持使用 `+` 或 `-` 表示在指定天数前或后，days 是一个整数表示天数。
>   -   `-user username`：按文件所有者查找。
>   -   `-group groupname`：按文件所属组查找。

**示例：**![image-20230727122614491](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727122614491.png)

## which指令

which指令会在环境变量$PATH设置的目录里查找符合条件的文件。

**语法：**`which [文件]`
**示例：**![image-20230727122838944](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727122838944.png)

>   which指令只能用来查找指令文件

## whereis指令

whereis命令用于查找文件。
该指令会在特定目录中查找符合条件的文件。这些文件应属于原始代码、二进制文件，或是帮助文件。
该指令只能用于查找二进制文件、源代码文件和man手册页，一般文件的定位需使用locate命令。

**语法：**`whereis [-bfmsu][-B <目录>...][-M <目录>...][-S <目录>...][文件...]`

**参数**：

>    -b 　只查找二进制文件。
>
>   -B<目录> 　只在设置的目录下查找二进制文件。
>
>   -f 　不显示文件名前的路径名称。
>
>   -m 　只查找说明文件。
>
>   -M<目录> 　只在设置的目录下查找说明文件。
>
>   -s　只查找原始代码文件。
>
>   -S<目录> 　只在设置的目录下查找原始代码文件。
>
>   -u 　查找不包含指定类型的文件。

**示例：**

![image-20230727124716629](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727124716629.png)

## grep指令

`grep`是行过滤指令，用来在文档中搜索字符串

**语法：**`grep [选项] [搜索的字符串] [文件]`
**功能：**在文件中搜索字符串，将找到的行打印出来
**常用选项：**

>   -i ：忽略大小写的不同，所以大小写视为相同
>
>   -n ：顺便输出行号
>
>   -v ：反向选择，亦即显示出没有 '搜寻字符串' 内容的那一行

**示例：**![image-20230727125638635](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727125638635.png)

![image-20230727130813998](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727130813998.png)

![image-20230727125643919](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727125643919.png)

![image-20230727130830309](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727130830309.png)

![image-20230727125722117](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727125722117.png)

---

# 压缩指令

当我们需要传输大文件时，往往会先打包压缩它们，**打包的目的是将所有相关文件集成在一起防止某一个文件丢失**，**压缩的目的是将文件通过某种算法缩小体积，以便提高网络传输的效率。**Linxu中有多个与用压缩有关的指令，下面让我们来看看吧~

## zip/unzip指令

**zip**

**语法：**`zip 压缩文件.zip 目录或文件`
**功能：**将目录或或文件压缩成zip格式
**常用选项：**

>   -r 递归处理，将指定目录下的所有文件和子目录一并处理

**示例：**
<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727133833633.png" alt="image-20230727133833633" style="zoom:50%;" />

**unzip**

`unzip 解压文件 -d 解压到zipdir目录`

![image-20230727134411899](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727134411899.png)

<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727134415068.png" alt="image-20230727134415068" style="zoom:50%;" />

## tar指令

>   -c ：建立一个压缩文件的参数指令(create 的意思)；
>
>   -x ：解开一个压缩文件的参数指令！
>
>   -t ：查看 tarﬁle 里面的文件！
>
>   -z ：是否同时具有 gzip 的属性？亦即是否需要用 gzip 压缩？
>
>   -j ：是否同时具有 bzip2 的属性？亦即是否需要用 bzip2 压缩？
>
>   -v ：压缩的过程中显示文件！这个常用，但不建议用在背景执行过程！
>
>   -f ：使用档名，请留意，在 f 之后要立即接档名喔！不要再加参数！
>
>   -C ：解压到指定目录

**示例：**<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727175327735.png" alt="image-20230727175327735" style="zoom:50%;" />

# 其他指令

## bc指令

bc 命令是任意精度计算器语言，通常在linux下当计算器用。
![image-20230727180409529](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727180409529.png)

## uname指令

**语法：**`uname [选项]`
**功能：**uname用来获取电脑和操作系统的相关信息    
**补充说明：**uname可显示linux主机所用的操作系统的版本、硬件的名称等基本信息。
**常用选项**

>   -a或–all 详细输出所有信息，依次为内核名称，主机名，内核版本号，内核版本，硬件名，处理器类
>
>   型，硬件平台类型，操作系统名称 

**示例：**![image-20230727181136421](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230727181136421.png)

---

# 指令作业

1.   
  
     
