# Linux基础开发工具

## 软件管理包–yum

### 什么是软件包？

-   Linux下下载软件可以下载程序得源码，并进行编译，得到可执行程序(需要自己编译)
-   另一种方式是使用别人提前编译好软件，需要时只需要下载该软件包(类似于Windows上安装程序)，软件包放在服务器得包管理器上，通过包管理器可以获得这个编译好的软件包，直接进行安装。
-   软件包和包管理器得关系类似于app和应用商店
-   `yum`是Linux服务器上的一种包管理器。主要应用在Fedora，RedHat，Centos等发行版本上。

### 注意事项

关于`yum`的所有操作必须保证主机(虚拟网络)畅通！

可以通过`ping`指令验证

```shell
ping www.baidu.com
```

### 查看软件包

`yum`中的软件包非常多，我们可以通过管道和`grep`指令搜索我们需要的软件包，例如

```shell
yum list | grep lrzsz
lrzsz.x86_64                             0.12.20-36.el7                @os 
```

**注意事项**

-   软件包名称: 主版本号.次版本号.源程序发行号-软件包的发行号.主机平台.cpu架构
-   "x86_64" 后缀表示64位系统的安装包, "i686" 后缀表示32位系统安装包. 选择包时要和系统匹配
-   "el7" 表示操作系统发行版的版本. "el7" 表示的是 centos7/redhat7. "el6" 表示 centos6/redhat6
-   最后一列, os 表示的是 "软件源" 的名称, 类似于 "小米应用商店", "华为应用商店" 这样的概念

### 如何安装软件

我们可以通过`yum`完成对gcc的安装

```shell
sudo yum  install lrzsz
```

出现“complete”字样说明安装完毕。

**注意:**

-   安装软件通常会想系统目录写入文件，因此安装软件必须是root用户或者普通用户通过`sudo`对`yum`进行提权
-   yum同时安装多个软件时会报错

### 如何卸载软件

同样通过`yum`进行卸载软件

```shell
sudo yum remove lrzsz
```

---

## 编辑器–vim

Windos平台下的编辑器有记事本、Visual Studio、CodeBlock等，Linux下的编辑器有vim/vi。vim是vi的升级，vim兼容vi的所有指令，并且在此基础上增加了语法高亮等，它的操作不仅可以在终端进行，也可以运行于Linux、macOS、windows上。

### vim的基本概念

vim有12种模式，下面主要介绍三种常用的模式:`正常/命令模式`、`插入模式`、`底行模式`。

-   命令模式

    >   控制光标的移动，字符、行的删除，移动复制到某区段，进入插入模式及底行模式

-   插入模式

    >   在插入模式下进行文本编辑，按`[ESC]`退回到命令模式

-   底行模式

    >   进行文件的保存,控制vim编辑器的退出，也可以进行文件替换，找字符串，列出行号等操作。在命令模式下按住`shift+;( : )`可以切换为底行模式，底行模式按`[ESC]`退回到命令模式

    在底行模式下输入`help vim-modes`可以查看vim下的12种模式

**注意：**
通过vim打开文件时默认进入命令模式，需要切换为插入模式才可以进行编辑文本

### vim的基本模式切换

命令模式切换为插入模式：键盘按键`a/i/o`;插入模式切换为命令模式：键盘按键`ESC`
命令模式切换为底行模式：键盘按键`:`;底行模式切换为命令模式：键盘按键`ESC`
插入模式和底行模式无法直接切换，必须先切换为命令模式，再通过命令模式切换为插入/底行模式

### vim基本操作

**命令模式操作**

-   移动光标

    -   按`小键盘上下左右`进行光标的控制，如果没有小键盘则通过`h j k l`分别控制光标的左 下 上 右
    -   按`G(shift+g)`控制光标移动到文本最后一行
    -   按`gg`控制光标移动到文本第一行
    -   按`#G`控制光标移动到第#行
    -   按`^`控制光标移动到当前行头
    -   按`$`控制光标移动到当前行第一个非`blank`字符
    -   按`0`移动到当前光标行头
    -   按`w`控制光标移动到下一个单词头部
    -   按`e`控制光标移动到下一个单词的最后面
    -   按`b`控制光标移动到前一个光标头部

-   删除文字

    -   按`x`删除光标所在位置的一个字符
    -   按`#x`删除光标所在位置的后面#个字符（包括光标所在位置的字符）
    -   按`X`删除光标所在位置前面的一个字符
    -   按`#X`删除光标所在位置前面#个字符（包括光标所在位置的字符）
    -   按`dd`删除光标所在的行
    -   按`#dd`从光标所在行开始向下删除#行

-   复制

    -   `yw`从光标位置到单词尾部复制到缓冲区中
    -   `#yw`复制#个单词到缓冲区
    -   `yy`复制当前行到缓冲区
    -   `#yy`复制从当前行往下#行到缓冲区

    -   `p`将复制的内容粘贴到光标所在位置

-   替换

    -   `r`替换光标当前所处的字符	
    -   `R`进入替换模式，按`ESC`退出为命令模式

-   撤销上一次操作

    -   `u`撤回上一条指令
    -   `ctrl + r`反撤销

-   批量化注释

    -   `ctrl + v`->j/k两个按键上下选中区域 ->`shift + i`->输入// ->`ESC`

-   批量化删除注释

    -   `ctrl + v`->hjkl选中区域->d/x


**底行模式操作**

-   列出行号
    -   底行输入`set num/set number`，会在文件每一行最前面列出行号
    
-   跳转文件某一行
    -   第行输入要跳转的行号`#`，紧接着按回车就会跳转到#行
    
-   查找字符
    -   底行输入`/(?)要查找的内容`，如果第一次不是你所想要的内容,按`n`往后寻找你所需要的关键字,找到后按回车就会跳转到所查找内容处
    
        >   **?和/的区别:**
        >
        >   /会从内容第一行开始往下查找,?会从内容最后一行开始网上查找
    
-   保存文件
    -   底行输入`w`后回车可以保存文件，`w!`可以强制保存文件
    
-   执行命令
    底行模式下输入`!+命令`可执行Xshell命令
    
-   同时打开多个文件
    底行模式下输入`vs 文件名`可以打开其他文件,`ctrl+w+w`可以在文件中切换光标
    
-   退出底行模式
    -   底行输入`q`后回车可以回到命令模式，`q!`可以强制退出，退出通常和保存连用`wq!`

### vim的配置

**vim配置文件的位置**

-   /etc路径下的隐藏文件`.vimrc`是**系统所有用户**的vim配置文件，更改该文件内容对所有用户的vim都会生效
-   每一个用户的家目录下存在一个`.vimrc`文件(不存在的自己可以创建一个)，该文件是当前用户的vim配置文件，只对该用户生效![image-20231126151139304](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231126151139304.png)

-   使用vim创建文件时,vim不仅会读取当前文件,还会读取vimrc配置文件


    **常用vim配置**

-   设置语法高亮：`syntx on`
-   显示行号:`set nu`
-   设置缩进格式:`set shiftwidth=4`

下面是配置后imrc文件的部分内容
![image-20231126151351850](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231126151351850.png)

**一件化部署vim配置**

了解上述内容后,我们可以自己配置vimrc文件,但是自己配置的比较麻烦,因此下面提供一种方法针对c++代码的vimrc文件配置
在 shell 中执行指令(想在哪个用户下让vim配置生效, 就在哪个用户下执行这个指令. 强烈 "不推荐" 直接在 root 下执行):

>   curl -sLf https://gitee.com/HGtz2222/VimForCpp/raw/master/install.sh -o ./install.sh && bash ./install.sh

需要按照提示输入 root 密码. 您的 root 密码不会被上传, 请放心输入.  	 

---

## 编译器-gcc/g++

### 背景

-   运行c/c++时往往需要编译、链接的过程，将源代码最终转换为可执行的机器指令才能运行程序，编译过程具体包括`预处理、编译、汇编`
-   编译器是一款软件，编译该软件的代码也需要一款编译器，例如C语言的编译器可能是通过汇编语言实现的，当C语言编译器实现后，我们就可以使用C语言重新编写一款C语言编译器，再用这款编译器编译C语言，这种方式叫做**编译器自举**

### gcc如何完成

**预处理**

-   预处理会进行头文件的包含，宏替换，取消注释，条件编译等
-   预处理指令以#开头
-   实例：`gcc -E code.c -o code.i`
-   选项-E的作用是让gcc在预处理结束后停止编译
-   选项-o作用是让预处理后的文件存放在code.i中
-   ![image-20230913202945159](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230913202945159.png)

**编译**（生成汇编代码）

-   在这个阶段gcc会检查代码是否有语法错误，无误后将**语言代码->汇编语言**
-   用户可以用`-S`选项进行查看，该选项只进行编译而不进行汇编
-   实例：`gcc -S code.i -o code.s`
-   >   汇编代码:<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230913203325268.png" alt="image-20230913203325268" style="zoom:67%;" />

**汇编**（生成机器可识别代码）

-   汇编将编译阶段生成的.s文件转换为目标文件.o(windows下为.obj ),将**汇编语言->可执行二进制代码**
-   选项-c 可以看到汇编代码转换为二进制指令
-   实例：`gcc -c code.s -o code.o`
-   <img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230913203406521.png" alt="image-20230913203406521" style="zoom: 50%;" />

**链接**（生成可执行文件或库文件）

-   链接过程会将所有的.o/.obj文件连接起来，并且将对应的文件链接函数库形成可执行文件

-   实例：`gcc code.o -o code`

>   **函数库：**
>
>   -   编译代码时，库函数的定义并不会存放在汇编阶段生成的.o/.obj文件，而是在链接过程中将函数库和生成的二进制文件连接在一起，因此**可执行程序=我们写的代码+头文件+函数库**
>
>   -   函数库分为静态函数库和动态函数库
>
>   -   静态函数库：c/c++或者其他第三方左右方法的集合，被所有的程序以拷贝的方式将需要的代码拷贝到自己的可执行文件中，静态库的后缀在Linux下为`.a`,windows下的后缀为`.lib`
>
>   -   动态函数库：c/c++或者其他第三方左右方法的集合，被所有的程序以链接的方式关联起来，这种连接的方式通常是将库函数的入口地址拷贝到程序中特定的位置，动态库的后缀在Linux下为`.so`，windows下的后缀为`.dll`
>
>   -   当我们安装gcc编译器时，系统上给我们自动将函数库拷贝到Linux下的`/lib64`目录下![image-20230913230806788](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230913230806788.png)
>
>       也会将头文件拷贝到Linux下的`/usr/include`目录下![image-20230913232637508](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230913232637508.png)
>
>   -   动态链接的优点：形成的可执行程序体积小，节省资源！缺点：需要通过入口函数的地址找到对应的函数，速度稍慢一点；强依赖动态库，动态库异常则程序异常。
>
>   -   静态链接优点：无视库，可以独立运行。缺点：体积太大，浪费资源。
>
>   ![](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230913232420182.png)
>   同一个文件采用静态链接和动态链接的大小相差100倍。
>
>   >   **默认情况下，编译器会选择动态链接**，因此函数库为动态函数库，云服务器默认下没有安装c静态库，只有动态库，如果要安装静态库输入`sudo yum install glibc-static`，c++的静态库`sudo yum install libstdc++-static`

总结：当我们安装一个开发环境时，**系统一定会安装下载并拷贝头文件和库文件到特定的路径中**
更细致点说：当我们安装案发环境时，系统会为我们做

1.   下载include和lib文件
2.   设置合理的查找路径
3.   规定链接方式(动态静态)

## 项目自动化构建工具-make/Makefile

### 背景

-   一个工程中的源文件不计数，其按类型、功能、模块分别放在若干个目录中，`Makefile`定义了一系列的规则来指定，哪些文件需要先编译，哪些文件需要后编译，哪些文件需要重新编译，甚至进行更复杂的功能操作
-   `Makefile`可以实现自动化编译，一旦写好编译指令，只需要`make`，整个工程就可以实现自动化编译，提高了软件开发的效率
-   `make`是一个命令工具，是一个解释`makeﬁle`中指令的命令工具，一般来说，大多数的IDE都有这个命令，比如：Delphi的make，Visual C++的nmake，Linux下GNU的make。可见，makeﬁle都成为了一种在工程方面的编译方法。
-   `make`是一条指令,`Makefile`是一个在当前目录下存在的具有特定格式的文本文件

### 初步使用make、makefile

![image-20230917103938969](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230917103938969.png)

![image-20230917104309445](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230917104309445.png)

### 原理

1.   为什么执行clean的依赖方法时需要`make clean`,而执行mybin对应的方法只需要`make`?
     执行目标文件对应的依赖方法可以通过`make 目标文件名`来完成，**直接make会执行Makefile中第一个目标文件的依赖方法**，上述中第一个目标文件是mybin,因此`make`指令会执行mybin的依赖方法`gcc code.c -o mybin`

2.   **`Makefile`可以识别文件的新旧**，若源代码没有改变，makefile不会让用户多次对同一个文件进行编译<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230917105924699.png" alt="image-20230917105924699" style="zoom:67%;" />
     -   那么`Makefile`为什么不让用户重新编译代码呢？
         因为编译过程是需要时间的，反复编译一个没有更改的文件是没有意义的，因此`makefile`只会让用户编译一个文件一次，除非该文件后续被更改过
         
     -   `Makefile`是怎么判断文件是否被修改过呢？
         通过判断源文件的修改时间是否大于前一次生成的可执行文件的修改时间，若大于则源文件一定被修改过
     
     -   查看文件的修改时间-`stat 文件名 `

![image-20230917132152333](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230917132152333.png)

-   文件的`Acess Time`的修改 限制访问次数
    因为一个文件被查看的频率是非常高的，如果每次查看文件都要更该文件的属性（Acess Time），由于属性是属于文件的一部分，因此更改属性这个操作需要访问磁盘，所以访问磁盘的频率也非常高，因此为了更高的访问效率，不会每次查看文件内容时更改Acess Time
    
-   可以通过`touch`指令更改文件的`ACM时间`并不会修改文件内容

-   `.PHONY`文件被称为`伪目标`，`伪目标`是总是被执行的

-   `Makefile`具有依赖性的推导能力

    <img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230920223013164.png" alt="image-20230920223013164" style="zoom: 50%;" />

如果不是自动推导,我们可以**显示让`Makefile`推导**

<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230920224351437.png" alt="image-20230920224351437" style="zoom:67%;" /><img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230920224705171.png" alt="image-20230920224705171" style="zoom:50%;" />

### Makefile的语法扩展

1.   依赖方法最前面加上`@`,make时不会显示该语句执行过程<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230920230059384.png" alt="image-20230920230059384" style="zoom:67%;" />

2.   `Makefile`可以在文件开头编写变量,`val_name=内容`,使用变量时前面加上`$`符号,`$(变量名)`<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230920230956736.png" alt="image-20230920230956736" style="zoom:80%;" />
3.   `$^`可以被展开为依赖关系中所有的`依赖文件`,`$@`会被展开为依赖关系中的`目标文件 `<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230920231429471.png" alt="image-20230920231429471" style="zoom:67%;" />

---

## 调试器-gdb

### 背景

通过调试,我们可以快速定位代码中逻辑有问题的那一部分.调试功能对于项目的构建是非常重要的.
因此为了更好了写代码,我们需要掌握调试工具.

Linux下的c/c++代码的调试工具为`gdb`

-   程序的发布方式有两种:`debug模式`和`release模式`
-   Linux下gcc/g++编译出来的程序默认为`release模式`(gcc形成可执行程序时默认也是动态链接的)
-   若要使用`gdb`调试,必须在编译生成源代码时加上选项`-g`
    <img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231126210616454.png" alt="image-20231126210616454" style="zoom:80%;" />

debug模式下会在可执行程序中添加与程序调试相关的信息,而release模式不会在可执行程序中添加相关信息,因此debug模式的体积比release模式体积大.<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231126211049802.png" alt="image-20231126211049802" style="zoom:80%;" />

>   同时可以通过指令`readelf -S`查看可执行程序相关的debug信息
>   ![image-20231126211432256](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231126211432256.png)
>   只有加上`-d`选项生成的可执行程序才能读取到相关dubug信息

但是只有debug模式才可以进行调试,因此开发过程中程序使用的是debug模式,发布时是以release模式发布.

>   PS:项目开发过程中开发人员开发的是debug版本,测试人员测试的是release版本,用户使用的也是release版本.



### 调试功能

1.   `l + 行号`:显示指定行号后面的代码(直接按回车执行上一条gdb指令,gdb自动记录最近一条指令)

2.   `l + 函数名/文件名:函数名`:查看指定函数代码

3.    `b + 行号/函数名/文件:行号`: 在指定位置打断点

4.   `infor b`:查看所有断点信息 

5.   `d + 断点编号`:取消指定断点

6.   `disable/enable+断点编号`:可以禁用/启用 断点<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231126214529132.png" alt="image-20231126214529132" style="zoom:67%;" />>>>       >

     >   禁用断点后:调试时会跳过该断点<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231126214518918.png" alt="image-20231126214518918" style="zoom:67%;" />

7.   `n`:逐过程调试

8.   `s`:逐语句调试

9.   `p 变量名`:显示指定变量值

10.   `display 变量名`:常显示指定变量值

11.   `unsdiplay 变量编号`:取消指定变量常显示

12.   `c`(continue):从一个端点执行到下一个断点(范围查找)

      >   当我们程序逻辑出现错误时,我们首先应该进行范围排查,例如在100行的程序中将第50行设置一个断点,75行设置一个断点,当调试时程序运行到第50行时并且上下变量值符合预期,说明前50行的逻辑正确,接下来我们应该排查50-75行逻辑是否正确,应该让程序一次性到达75行的断点而不是我们一步一步调试到75行,这是我们就可以跳到下一个断点处观察变量值判断中间逻辑是否正确.

13.   `finish`:将一个函数运行结束就停下来

14.   `until 行号`:跳转到指定行

15.   `bt`:查看调用堆栈

16.   `set var 变量名 = 值`:修改变量的值(不改变源代码情况下进行多分支测试)
      <img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231127001211255.png" alt="image-20231127001211255" style="zoom: 50%;" />

---

## Linux第一个小程序-进度条

### 行缓冲

![image-20230921152023753](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230921152023753.png)

可以通过`fflush`提前刷新缓冲区

![image-20230921152534602](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20230921152534602.png)
