# Linux权限的概念

**Linux下有两种用户：超级用户(root)和普通用户。**

-   超级用户：可以在Linux系统下做任何事情，不受限制
-   普通用户：在Linux下做有限的事
-   超级用户的提示符是“#”,普通用户的提示符是“$”
    ![image-20230806165553469](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230806165553469.png)

**命令su用来切换用户**
语法：su 用户名
功能：切换用户
例如，从root切换为sy,只需要`su sy`即可，若从普通用户切换为超级用户可以`su root`,root可以省略(切换为超级用户时需要输入root密码)

# Linux权限管理

我们针对一件事可不可以被做时需要考虑两方面，一是这件事针对的不同的对象是否可以被做，二是这件事本身是否可以被做。

Linux中的权限也应该从这两方面考虑

1.   文件访问者的分类（人）
2.   文件类型和访问权限（事物属性）

## a. 文件访问者的分类

访问者一般分为以下3类

-   文件和目录的所有者：u—User
-   文件和目录的所有者所在的组的用户：g—Group
-   其他用户：o—Others

## b. 文件类型和访问权限

文件信息：

![image-20230806171024029](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230806171024029.png)

**文件类型：**
>d：文件夹
>
>-：普通文件(源文件、可执行文件)
>
>l：软链接（类似Windows的快捷方式）
>
>b：块设备文件（例如硬盘、光驱等）
>
>p：管道文件
>
>c：字符设备文件（例如屏幕等串口设备）
>
>s：套接口文件

**基本权限：**

>   i.读（r/4）：Read对文件而言，具有读取文件内容的权限；对目录来说，具有浏览该目录信息的权限
>
>   ii.写（w/2）：Write对文件而言，具有修改文件内容的权限；对目录来说具有删除移动目录内文件的权限
>
>   iii.执行（x/1）：execute对文件而言，具有执行文件的权限；对目录来说，具有进入目录的权限
>
>   iv.“-”表示不具有该项权限	

## c. 文件权限表示方法

**字符表示**

| Linux表示 |             说明             |
| :-------: | :--------------------------: |
|   -\-\-   | 文件目录不可读不可写不可执行 |
|  r \-\-   |        文件目录只可读        |
|    -w-    |        文件目录只可写        |
|   \-\-x   |       文件目录只可执行       |
|    rw-    |       文件目录可读可写       |
|    r-x    |      文件目录可读可执行      |
|    -wx    |      文件目录可写可执行      |
|    rwx    |    文件目录可读可写可执行    |

**进制表示**

| 权限符号 | 8进制表示 | 二进制表示 |             说明             |
| :------: | :-------: | :--------: | :--------------------------: |
|  -\-\-   |     0     |    000     | 文件目录不可读不可写不可执行 |
|  r \-\-  |     4     |    100     |        文件目录只可读        |
|   -w-    |     2     |    010     |        文件目录只可写        |
|  \-\-x   |     1     |    001     |       文件目录只可执行       |
|   rw-    |     6     |    110     |       文件目录可读可写       |
|   r-x    |     5     |    101     |      文件目录可读可执行      |
|   -wx    |     3     |    011     |      文件目录可写可执行      |
|   rwx    |     7     |    111     |    文件目录可读可写可执行    |

>   若文件的权限符号是`rwxr-xr-x`，则该文件的拥有者对文件可读可写可执行，所属组对文件可读可执行，其他人对文件可读可执行。该权限可以用755表示

## d. 文件权限的设置

**chomd**
功能：修改文件目录的权限
格式：`chmod [参数] 权限 文件名`
参数：

>   R : 递归修改目录文件的权限
>
>   注意：只有root和拥有者可以更改文件权限

**chmod修改权限的格式**

1.   用户表示符+-=权限字符

     >   -   +:向权限范围增加权限代号所表示的权限
     >
     >   -   -:向权限范围取消权限代号所表示的权限
     >
     >   -   =:向权限范围赋予权限代号所表示的权限
     >
     >   -   用户符号：  
     >
     >       u：拥有者
     >
     >       g：拥有者同组用
     >
     >       o：其它用户
     >
     >       a：所有用户

 

![image-20230806191856310](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230806191856310.png)

2.   三位八进制数字

![image-20230806192531267](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230806192531267.png)

**chown**
功能：修改文件的拥有者
格式：`chown [参数] 用户文件名`

![image-20230806193755364](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230806193755364.png)

**chgrp**
功能：修改文件或目录的所属组
格式：`chgrp [参数] 用户组名 文件名`
常用选项：-R 递归修改文件或目录所属组

![image-20230806194049268](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230806194049268.png)

## 权限掩码

新建的文件默认权限是666，新建的目录默认权限是777，但是实际看见的文件默认权限是664,目录权限是775,这是因为umask(权限掩码)的存在![image-20230806222946026](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230806222946026.png)

当前状态权限掩码的默认值为002(八进制)![image-20230806223333958](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230806223333958.png)

因此**实际权限=默认权限减去权限掩码**

>   这里的减去不是数学上的减，而是**将与权限掩码为1的位所对应的二进制位置为0**
>   例如文件最初权限二进制串是110110110,掩码二进制串000000010,将文件最初权限倒数第二个二进制位变成0就是110110100
>   用计算机语言就是**实际权限=默认权限&(~权限掩码)**
>
>   **ps:**
>   root用户的默认权限掩码是0022;普通用户的默认权限掩码是0002
>   ![image-20230807101451159](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230807101451159.png)

**为什么文件的最初权限是666呢？**
因为直接创建的文件都不可以直接执行，因此将最初权限设置位666
**为什么文件的最终权限是664？**
因为通常情况我们不希望other可以对文件的内容进行修改，只给other读文件的权限
**为什么目录的最终权限是775呢？**
首先，读目录就是查看当前目录下存在的文件，写目录就是在当前目录下删除/添加文件，执行目录就是进入该目录，任意创建的一个目录，我们并不希望others可以随意删除该目录下的内容，因此将other的w权限去掉，最初权限位775.

---

## file指令

功能语法：辨识文件类型
语法：`file [选项] 文件或目录`
常用选项：

>   -   -c 详细显示指令执行过程，便于排错或分析程序执行的情形
>   -   -z 尝试去解读压缩文件的内容

![image-20230807101945826](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230807101945826.png)

## 粘滞位

如果现在存在这样一种情况：你是老板，你命令手下的员工小王和小李在你所创建的目录dir下共同工作，小王在dir下创建了test1.txt,小李在dir下创建了test2.txt。test1.txt对other的权限是-\-\-,因此小李不可以查看text1.txt,但是dir对other的权限一定是rwx，也就是说小李在这种情况下可以删除text1.txt。小王的初衷就是不给小李查看自己写的文件，你倒好，直接把文件给删了，是不是不太合理？，在这种情况下，我们可以设置**粘滞位**

语法：`chmod +t 目录`

![image-20230807103843984](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230807103843984.png)

当目录被设置成粘滞位时，该目录下的文件只能被

-   超级管理员删除
-   该目录的所有者删除
-   该文件的所有者删除

---

# 权限总结

-   权限可以用字符表示：rwxrwxrwx；可以用进制表示：777
-   root用户或者文件目录的拥有者可以通过**chmod**改变权限
-   root用户可以通过**chown**改变文件的拥有者,**chgrp**改变文件的所属组
-   实际权限=最初权限&(~权限掩码)

**文件权限：**

1.   r权限表示是否可以读取文件内容
2.   w权限表示是否可以对文件的内容进行修改
3.   x权限表示是否可以执行该文件
4.   一般创建的文件都不具有可执行性，因此文件最初的权限是666

**目录权限：**

1.   r权限表示是否可以查看当前目录下所有的文件或子目录
2.   w权限表示是否可以在当前目录下创建/删除文件、子目录
3.   x权限表示是否可以cd到当前目录下
4.   目录的最初权限是777,普通用户创建的目录最终权限是775
5.   可以对目录设置粘滞位保证该目录下的文件不能随意被删除

---

# 权限作业

1.    以下哪个命令输出Linux内核的版本信息：
     ![](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231116223114543.png)

2.    linux查看cpu占用的命令是什么？
     ![image-20231116223722915](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231116223722915.png)

3.   在Linux系统中, 为找到文件try_grep含有以a字母为行开头的内容, 可以使用命令？
     ![image-20231116223757334](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231116223757334.png)

4.   
     ![image-20231116223854721](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231116223854721.png)

>   ![image-20231116223911916](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231116223911916.png)