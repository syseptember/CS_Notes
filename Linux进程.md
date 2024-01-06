>   **前言:**
>   硬件—冯诺依曼体系结构
>   软件—操作系统

# 冯诺依曼计算机体系结构

## 背景

什么可以称为计算机呢?

>   **百度百科:**![image-20231128111140923](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231128111140923.png)

计算机应该满足的功能:

1.   可进行计算(数字计算&&逻辑计算)
2.   具有存储记忆功能

人类历史上第一台计算机由约翰·冯·诺依曼(后面称为冯·诺伊曼)创造，冯·诺依曼提出了计算机制造的三个基本原则

-   采用二进制逻辑
-   程序存储执行以及计算机由五个部分组成（运算器、控制器、存储器、输入设备、输出设备），这套理论被称为冯·诺依曼体系结构。

<img src="https://img-blog.csdnimg.cn/img_convert/5a937adaa66d58b99ca5e0da2b389937.png" alt="img" style="zoom:80%;" />

冯·诺依曼体系结构在硬件上规定了计算机底层结构离不开输入设备，输出设备，存储器，中央处理器.

>   输入设备:键盘，磁盘，话筒等
>   输出设备:显示器，磁盘，扬声器等
>   存储器:特指内存，掉电易失，数据处理快
>   中央处理器(后面用CPU表示中央处理器):运算器+控制器

## 理解

1.   为什么从输入设备获取的数据不能直接交给CPU处理，处理完的数据不能直接传输给输出设备，必须经过中间存储器呢?

     >   计算机的不同存储空间有着不同的存储效率和访问效率
     >
     >   **存储金字塔:**![img](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhou1322310-20200328084130182-1706395900.png)**离CPU越近的存储器访问速度越快，单体容量小，成本高**
     >   **离CPU越远的存储器访问速度越慢，单体容量大，成本低**
     >
     >   如果输入输出设备直接和存储器进行数据传输，因为输入输出设备离CPU远，所以对数据处理速度低，但是CPU对数据的处理是非常快的，根据[木桶原则](https://baike.baidu.com/item/%E6%9C%A8%E6%A1%B6%E5%8E%9F%E5%88%99/1760482)，整个计算机处理数据的速度取决于效率低的输入输出设备，而不是CPU，同时更容易时CPU处于闲置状态.
     >
     >   相反，如果让内存和输入输出设备交互，CPU只负责对内存中的数据进行处理并把数据返还给内存，而内存对数据处理速度远大于硬盘等输入输出设备，所以这样可以减少因木桶原理而减少的效率.

2.   经过输入输出设备的数据通过存储器传是否可以加快计算机处理数据的速度呢?

     >   在CPU和输出输出设备间插入存储器，细心的朋友可以发现，在CPU-内存-输入输出三种设备中，对数据处理最慢的还是输入输出设备，木桶原则应该还存在，计算机整体效率仍然取决于输入输出设备，既然这样，引入内存不是多此一举吗?
     >
     >   我们可以通过预先加载和缓存技术解决上述问题:
     >
     >   -   **预先加载**:在CPU执行上一次指令时，提前将输入设备中的数据加载到内存里，当CPU执行完上次指令后，可以直接从内存中读取数据执行指令.
     >   -   **缓存**:CPU将处理完的数据写入到内存中，等计算机处于闲置状态时，再将内存中保存的数据刷新到输出设备.
     >       ==通过预先加载和缓存技术可以让CPU只和内存交互==，使计算机的效率取决于内存效率，提高计算机效率.
     >
     >   ps:预先加载和缓存的工作由操作系统来完成，因此我们可以将硬件上的问题转化为软件上的问题(操作系统).

3.   冯·诺依曼结构中引入内存的意义

     -   数据层面:通过将计算机效率取决于硬件拷贝数据的速度这种硬件层面的问题转换为操作系统预先加载和缓存这种软件层面的问题，进而提高计算机效率

     -   经济层面:内存的成本较为适中，所以在尽量不使用过高的成本提高计算机的效率.

         >   只有成本低了用的人才会多，互联网才会普及

解释:**运行程序首先要将程序加载到内存中**

>   根据冯·诺伊曼结构，CPU只能从内存中读取数据，而可执行程序的指令需由CPU来执行，因此必须将可执行程序从磁盘加载到内存中才能交给CPU执行

## 举例

请解释当我通过互联网像被人发送“在吗”时数据的流动
>![image-20231128181438375](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouoss-cn-hangzhouimage-20231128181438375.png)

**总结:**
冯·诺伊曼体系结构通过引入存储器让我们可以使用较低成本提高计算机的运行效率.
冯·诺伊曼体系结构将计算机效率取决于硬件转化为软件(操作系统)
数据传输时，外设和内存交互，内存和CPU交互.

---



# 操作系统(OS)

什么是操作系统?

![image-20231129084426210](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231129084426210.png)

**操作系统(后面称为OS)是一款对下层软硬件进行管理(手段)，对上层用户提高稳定，安全，高效的运行环境(目的)的软件.**

上面我们说过，程序运行时首先需要被加载到内存，而操作系统是一款软件，想要运行它也必须加载到内存中，而操作系统是用来对软件进行管理的，所以一定要先于所有软件加载到内存中.
所以**操作系统是第一个被加载到内存的软件.**

>Linux是一款操作系统，Linux操作系统主要由以下两部分组成
>
>-   Linux内核(kernal):是操作系统的核心，主要负责内存管理，进程管理，文件管理，驱动管理
>-   系统工具:用于管理系统和执行各种任务的软件，Shell(命令行解释器)，文件管理器，编辑器，编译器等

## OS的管理

操作系统负责对软硬件进行管理，那么什么是管理呢?
在这之前，我们需要知道`软硬件层次结构`
![image-20231129151544646](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouoss-cn-hangzhouimage-20231129151544646.png)

1.   **管理者直接和被管理者不一定直接进行交互**

     >   举个例子:你是一名学生，你们所做的工作全是由校长所规定的，但是你有经常和校长见面吗?并没有，校长只需要吩咐事项(做决策)，剩下的交给辅导员(假设只有你 辅导员 校长三方)来监督你们完成，所以管理者和被管理者不一定需要直接交互.

2.   **管理的本质是对数据进行管理**

     >   在你刚刚进入大学时，甚至连同学的名字都不知道，此时你已经被划分好在哪一个班，哪一个寝室了，你已经“被管理”起来了，但是管理者并没有见到你，只是投档时你的高中已经把你对应的档案袋交给了大学，校长已经拿到了你的档案袋，档案袋里面有你的各种信息，通过这些信息校长就可以将你分班，分寝…
     >
     >   所以管理不需要知道你是谁，只需要拿到你所对应的数据.
     >   上面说过，管理者不会直接和被管理者进行交互，那么管理者如何拿到被管理者的数据呢?
     >   实际上管理者会通过执行者拿到数据，让执行者去和被管理者交互，例如辅导员就是一个执行者，辅导员通过和你交互得到你的绩点，综测排名…再上交给校长，校长通过这些数据对你的数据决定你是否可以评优评先…
     >
     >   操作系统相当于管理者(校长):负责管理软(程序)硬(设备)件
     >   驱动程序相当于执行者(辅导员):驱动程序负责将与之对应的硬件操作打包，对操作系统提供操作硬件的接口
     >   底层硬件相当于学生(被管理者)

3.   **管理的方式—先描述，再组织**

     >   当被管理者数量很大时，管理者所需要面对的数据量是非常大的，如何管理大量的数据呢?
     >   可以通过**“先描述，再组织”**的方式管理数据，先将学生对应的数据用一个结构(struct)表示，在通过某一种组织方式(顺序表，链表等数据结构)将多个结构组织起来形成一个学生信息管理系统，此时对学生的管理(增删查改)转化为对数据结构的管理(增删查改)
     >
     >   回到操作系统:操作系统通过先描述，后组织的方式管理硬件.
     >
     >   假设操作系统以链表的方式组织数据
     >
     >   **描述:**Linux内核是C语言编写的，因此使用C语言的`struct`描述被管理者
     >
     >   ```c++
     >   struct Device
     >   {
     >       //硬件设备的属性
     >        Device* next;//指向
     >    }
     >    ```
     >   
     >   **组织:**
     >
     >   ![image-20231129094131324](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231129094131324.png)
     >
     >   以后当某一个设备出现故障，操作系统直接将链表中的该设备信息删除，也就是对链表的删除.

<font color='cornflowerblue'>注意</font>:先描述-再组织的管理方式会贯穿整个Linux学习周期，凡是涉及管理方式，均为“先描述-再组织.”

**总结:操作系统对硬件管理的本质是对硬件所对应的数据进行管理，管的的方式是先描述-再组织**

>   聊点别的:
>   数据结构这门学科本质上就是告诉我们将不同类型的数据如何组织起来更高效，C++STL库也提供了组织数据的方式，其实只要是面向对象语言，都应该提供类似STL的库，因为面向对象本质是描述数据，但是光有描述不足以管理数据，还需要通过一些方式将描述的数据组织起来，这样才可以通过这门语言更高的管理数据.

## 为什么要有操作系统?

如果没有操作系统，那么我们需要自己手动控制硬件(一只手打王者荣耀，一只手操控电路板(\~真是一场酣畅淋漓的体验啊\~).
操作系统的作用是

-   对下层软硬件进行管理(手段)
-   对上层用户提高稳定，安全，高效的运行环境(目的) 

那么操作系统是如何提供稳定，安全，高效的运行环境呢?

>   操作系统只对用户提供特定的`system call`(系统调用接口)保证用户不会直接访问操作系统，用户只能通过`system call`执行系统层面的操作，例如像显示器输出字符串，因为`system call`涉及了系统层面的知识，所以有些用户使用起来有困难，若对外提供的用户操作接口封装了系统调用，那么用户只需要会使用用户操作接口即可完成系统层面的操作，例如C语言中的库函数`pirntf`就是一个用户操作接口，其中封装的`system call`可以像显示器打印字符串.

# 系统调用与用户操作接口

## 系统调用

为了不让操作系统中的所有数据暴露给用户，操作系统只对用户提供`system call`使用户完成需要的操作

>   例如你需要去银行取钱，若不考虑使用取款机，会有一个银行窗口将你“挡在外面”，你只能通过银行窗口取钱，对于操作系统来讲，`system call`就相当于一个银行窗口防止你直接访问操作系统.

<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231129155156486.png" alt="image-20231129155156486" style="zoom:80%;" />
**系统调用在保证操作系统安全的情况下向用户程序提供了对底层硬件访问和执行系统级别任务的方法.**

>   因为Linux是用C语言写的，因此Linux的`system call`是使用C语言写函数的

既然用户必须通过`system call`才能访问操作系统，那么用户是否可以绕过操作系统直接访问硬件呢?

>   不可以
>
>   1.   硬件复杂性:现代计算机系统的硬件通常非常复杂，直接访问硬件需要深入了解硬件体系结构和寄存器级别的编程
>   2.   安全性:用户直接访问硬件可能导致系统容易受到恶意攻击，操作系统通过权限管理和隔离确保不同的应用程序只能访问其授权的数据
>   3.   稳定性:操作系统负责处理硬件抽象和资源管理，以确保多个应用程序可以在同一台计算机上共存而不相互干扰。如果用户直接访问硬件，可能会导致资源冲突、竞争条件和系统崩溃。
>
>   <font color='cornflowerblue'>注意</font>:在嵌入式设备中可能可以直接对硬件进行操作

<font color='orange'>总结</font>:任何人都不能直接访问操作系统，必须通过`system call`才能访问.
![image-20231129161205517](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231129161205517.png)

## 用户操作接口

### 引入:printf&&scanf的重新理解

我们都知道`printf`是像显示器打印字符串，也就是说`printf`函数需要访问硬件，之前说过，用户程序想要访问硬件必须通过操作系统，而对操作系统的访问又离不开`system call`，所以`printf`函数底层一定是封装了可以让操作系统访问显示器的`system call`，同理，`sacnf`内会封装可以让操作系统读取键盘输入的`system call`.

### 库函数

既然`printf`和`scanf`中封装了对应的`system call`，我为什么不直接调用`system call`像显示器打印/键盘读取，而是要绕一层调用`printf`和`scanf`呢?

>   接着银行的例子，银行提供对应的窗口后，是不是所有人都会熟悉办理流程呢?当然不是~只有具备一定理解能力的人才能够顺利的办理业务，银行当然也知道这一点，因此他们又设立了一个服务层，不会使用银行窗口的人可以在服务层寻求帮助，通过服务层，不管你识不识字，你最后都可以取到钱.

`system call`是系统级别的接口，也就是说需要对操作系统有一定了解的人才会使用，而大多数用户并不了解操作系统，因此像用户提供类似于`printf`和`scanf`级别的库函数，同样可以使用户完成对硬件资源的使用.

>   C标准库(libc)具有跨平台性的原因之一是因为C的库函数中调用的`system call`是由当前操作系统所决定的.例如Windows下`printf`函数封装的`system call`是代码A，Linux下`printf`函数封装的`system call`是代码B，但是C的库函数`printf`实现时并没有指定是使用代码A还是代码B，具体情况取决于当前操作系统，如果是Windows则使用代码A，如果是Linux则使用代码B

**库函数是用户操作接口的一种，库函数可以调用`system call`**
用户操作接口还有:

1.   Windows下的GUI(图形化界面):通过图标我们可以访问顶层硬件
2.   Linux下的Shell(命令行解释器):GUI能做的Shell也能做
3.   部分指令:部分汇编指令可以访问底层硬件

![image-20231129164256076](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231129164256076.png)

有了上述知识，我们就将计算体系结构搭建起来了

# 计算机体系结构

![image-20231129164336374](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231129164336374.png)

**一方面，操作系统通过“先描述，再组织”的方式对软硬件资源进行管理，保证底层硬件及驱动程序是被有序的组织起来，另一方面，为了降低用户使用成本，操作系统通过一系列的系统调用，用户操作接口对用户提供一个稳定，安全，高效的运行环境.**

---

# 进程

## 进程概念

这是绝大多教材上的解释:
![image-20231130195103497](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231130195103497.png)
教材上的普遍观点是**正在执行的程序称为进程.**

这个结论当然是正确的，只是给出这么一个定义来还是会有点不好理解.下面我将引入上一章节的内容带大家理解到底什么是进程.

根据冯·诺伊曼体系结构，程序运行时一定要将可执行代码加载到内存中，既然可执行程序加载到内存了，那么我们的操作系统一定要管理加载的内存的程序，管理?如何管理呢?~先描述，再组织

>   -   **描述**:将加载到内存中的程序使用`struct`描述
>
>   ```c++
>   struct
>   {
>   	//唯一标识进程的id
>   	//进程执行的优先级
>   	//进程当前的状态(正在运行中/等待运行)
>   	//内存指针
>       //...包含进程几乎所有的属性
>   	struct* next;//存放指向下一个进程的地址
>   }
>   ```
>
>   1.   进程id
>        每一个可执行程序只会被加载到内存中一次，所以内存中不存在相同的可执行程序，为每一个正在执行的程序分配一个标识符id，当操作系统后期需要对该程序进行管理时，可以通过唯一的标识符找到该程序，因此标识符是为了让操作系统更方便地管理程序
>
>   2.   进程优先级
>
>        ![image-20231130201201828](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231130201201828.png)
>        你想想，当我们电脑同时打开多个软件时， 操作系统会为每一个软件分配相同的计算机资源吗?一般来说是不会的，比如如果你听歌的同时下载文件，操作系统很可能会因为听歌是在前台运行的程序，而下载文件时后台运行的程序，而对他们它们分配不同的的优先级(不考虑用户手动更改优先级)
>
>        进程优先级的概念旨在优化系统的整体性能，确保重要的任务能够更及时地得到处理
>
>   3.   进程状态
>
>        ![image-20231130202341659](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231130202341659.png)每一个正在执行的程序都会有自己所对应的状态，比如当我们运行一个程序时，刚开始该程序被加载到内存中进入开始状态，紧接着CPU读取并执行该进程的指令进入运行状态，如果代码中有于用户交互的部分(例如等待用户输入数据)此时程序进入阻塞状态，当用户输入完成后，程序进入就绪状态，最终程序结束时会进入退出状态
>
>   4.   内存指针
>        当多个可执行程序加载到内存中，操作系统需要知道每一个可执行程序加载到内存中的什么位置，因此需要通过需要一个东西有指向可执行程序加载所在位置的指针，该指针称为`内存指针`
>        ![image-20231130205811862](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231130205811862.png)
>
>   



## PCB(进程控制块)

上述`struct`描述了一个正在执行程序所对应的信息，因此为了更好的管理内存中的程序，操作系统将程序加载到内存中时也会为该程序创建一个`struct`存放程序所对应的信息(id，优先级，状态，内存指针)，这样的好处就是操作系统管理程序时不需要直接对二进制代码进行管理(操作系统也看不懂)，只需要对存放该程序的`struct`进行管理.
**存放正在执行程序所对应的信息的`struct`称为`PCB(process control block)`**

>   -   **组织:**
>       将每一个PCB通过链表(也可能是其他数据结构)组织起来，以后操作系统对正在执行的程序的管理转换为对PCB链表的管理(增删查改)

-   当有新的程序运行时，操作系统首先将可执行代码加载到内存中，然后为该程序创建一个PCB对象，并且将该PCB对象与之前的PCB链表链接起来
-   当有程序删除时，会先将加载到内存中的代码删除，然后将PCB对象从链表中移除.

程序运行时，内存中不仅有可执行程序的代码，还有描述该程序信息的PCB对象，因此我们给出进程的概念:
<font color='orange'>**进程=可执行程序和数据+内核PCB对象**</font>，可以将PCB对象抽象为数据结构

**通过引入PCB，可以让未来所有对进程的操作转化为对PCB的操作，而与可执行程序无关!!!**

>   举例:
>   运行程序时，CPU会创建一个`runQueue(运行队列)`，队行列中存放的是所有进程的`PCB`，当一个进程执行时，将该进程的`PCB`入队`runQueue`中 ，进程执行时只需要将`PCB`放在`runQueue`中，无需对可执行程序处理

加下来我将从**PCB的内部属性**&&**外部如何调用访问**PCB来详细介绍PCB

## PCB的内部属性

PCB是操作系统这门学科下进程控制块的叫法，Linux，Windows，MacOS下的PCB名称和属性有点不同

-   Linux:PCB通常表示为`task_struct`结构体，结构体中存放有关进程的各种信息(进程状态，调度信息，文件描述符)
-   Windows:PCB由进程环境快`PEB(Process Environment block)`和线程环境快`TEB(Thread Environment block)`组成.
-   macOS:类似于Linux的`task_struct`，表示进程信息的数据是`proc`结构体.

<font color='cornflowerblue'>注意:</font>本文所设计的PCB均为`task_struct`

`task_struct`的属性

-   标识符:区别于其他进程的标志
-   状态:进程所处的状态
-   优先级:相对于其他进程的优先级
-   内存指针:指向拷贝到内存中的可执行程序的指针
-   上下文数据
-   I/O状态信息: 包括显示的I/O请求，分配给进程的I／O设备和被进程使用的文件列表。
-   程序计数器:程序下一条被执行的指令地址
-   记账信息:可能包括处理器时间总和，使用的时钟数总和，时间限制，记账号等
-   其他信息

1)2)3)4上述已经解释，这里解释一下6)7)8

**I/O状态信息:**
当进程进入阻塞状态时，可能因为正在和硬件交互，此时如果交互的是输入输出设备，那么进程需要记录所使用的硬件状态以及使用的文件相关信息

**程序计数器:**
<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231201200253421.png" alt="image-20231201200253421" style="zoom:67%;" />因为CPU只会将`task_struct`置于运行队列中，不将可执行程序直接放入CPU中，所以CPU需要知道程序下一条指令的地址，解决方法就是将下一条指令地址存放在当前进程的`task_struct`中，同时CPU中也创建一个寄存器存放该地址，这样每次CPU只需要通过寄存器中的地址去执行对应的指令并更新计数器的值，该寄存器和`task_struct`中存放下一条指令的地址的属性叫做`程序计数器`.

**记账信息:**
CPU一次只能运行一个进程，因此对于每一个进程都需要记录其运行时间和占用资源等

>   关于上下文数据，后面再介绍

接下来讲解外部访问调用PCB的一些操作

# 查看系统进程

## 指令ps

>   ps ajx	//显示系统**所有用户**的正在运行的进程
>
>   ps aux       //显示系统**当前用户**正在进行的进程

我们编写一个程序，通过该命令查看该程序所对应的进程信息

```c++
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>
int main()
{
	while (1)
	{
	   printf("I am a process!\n");
	}
	return 0;
}
```

>   ![image-20231201205116307](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231201205116307.png)	

为什么`grep`过滤出来的有2个进程呢?

>   可以看见另外一个是`grep`所对应的进程，这是因为在执行`ps ajx | head - 1 && ps ajx | grep process`的一瞬间调用了`grep`指令，在Linux下一切接文件，`grep`当然也是文件，需要被加载到内存中，而grep过滤的是包含“process”信息，因此在执行`grep`指令时，grep进程中需要存放`process`信息表示当前过滤的是“process”关键字，所以`grep`进程中会出现“process”关键字

可以加上指令`grep -v grep`反向过滤包含grep的进程
![image-20231202141438819](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231202141438819.png)

当Myprocess进程结束后，包含“process”关键字的进程减少一个.
![image-20231201212033078](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231201212033078.png)

<font color='orange'>总结:</font>通过指令`ps ajx | head -1 && ps ajx | grep process | grep -v grep`可以显示系统中正在执行的process进程.

## 指令ls /proc

>   ls /proc 可以查看系统中内核和正在运行的进程相关信息，这些信息以文件或子目录列出.

<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231202224326123.png" alt="image-20231202224326123" style="zoom:150%;" />
proc目录下一个数字都代表一个进程的pid
当我们运行程序时，可以看见相应的进程对应的目录在/proc目录下建立
<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231202225657543.png" alt="image-20231202225657543" style="zoom:150%;" />
我们查看该进程对应目录里面的具体内容
![image-20231202230010517](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231202230010517.png)

-   exe文件指向当前进程的位置
-   cwd文件指向当前进程的工作目录
    process进程在文件夹/home/sy1/12_1下，因此工作目录即cwd指向的就是/home/sy1/12_1.

1.   exe文件:在进程运行时将可执行程序删除但是不结束进程时，此时当前进程下得`exe`文件会发出警告:可执行文件已被删除![image-20231202231232841](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231202231232841.png)2. cwd文件:进程运行时会将**程序启动时的目录**设置为cwd指向目录
     <font color = cornflowerblue>注意</font>:程序启动时的目录≠程序所在目录，也就是说后续程序位置发生改变，cwd的指向也不会改变 可以通过`chdir`系统调用改变进程当前工作目录![image-20231203002353150](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231203002353150.png)

     >   C语言函数fopen(const char* path， const char* mode)如果在当前工作路径下未找到该文件名，则会创建该文件，其中当前工作路径就是该进程cwd文件所指向的路径.可以通过代码验证
     >   <font color = red>代码演示:</font>
     >
     >   ![image-20231203010904852](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231203010904852.png)
     >
     >   <img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231203011925066.png" alt="image-20231203011925066" style="zoom:150%;" />

## 查看进程标识符

Linux下有两个函数可以帮助用户查看进程标识

-   `getpid()`:查看当前进程标识符

-   `getppid()`:查看当前进程的父进程的进程标识符

    可以通过`getpid`函数得到当前进程的标识符，通过`getppid`函数可以获得对应的父进程的标识符
    <img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231202144436960.png" alt="image-20231202144436960" style="zoom: 67%;" />

    >   这里`getpid/getppid`在`man手册`第二章，属于**系统调用**.
    >   前面说过，操作系统是负责管理软硬件的，进程可以看做一款软件，因此进程是被操作系统管理，而管理进程就是管理进程的`task_strut`，因此`task_struct`中的数据也是操作系统的数据，想要访问操作系统中的数据可以使用系统调用，这就是`getpid`和`getppid`是系统调用的原因
    >   <img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231202150437224.png" alt="image-20231202150437224" style="zoom: 67%;" />

    

1.   **Linux下每一个进程都有一个父进程**

<font color='red'>代码演示</font>:

```c++
#include <stdio.h>                               
#includ<unistd.h>
 #include <sys/types.h>
  int main()
  {
    pid_t id = getpid();
    pid_t fid = getppid();
      while (1)
      {
         printf("I am a child  process，id = %d\n"，    id);
         printf("I am a father process，id = %d\n"，    fid);
        sleep(1);
      }
      return 0;
  }
```

>   ![image-20231202151825479](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231202151825479.png)

2.   **当程序重新运行时，操作系统会给它们分配新的进程标识符**
  
     >   ![image-20231202152619450](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231202152619450.png)
     
3.   **终端下，同一个用户的所有进程都有一个相同的父进程bash**

     当进程的pid不同时，ppid却相同，说明了不同的进程会有一个p相同的父进程，父进程的pid是25268
     `ps ajx | head -1 && ps ajx | grep 25268 | grep -v grep`查看pid为25628的进程名称

>   ![image-20231202153519336](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231202153519336.png)



>   <font color = cornflowerblue>注意:</font>bash进程也有父进程，父进程为当前用户，当前用户也有父进程…最中所有进程的祖先是`Init`进程(PID为1)
>   ![image-20231202155625241](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231202155625241.png)



# 创建进程|fork初识

在此之前我们所遇见的进程全部是当程序运行起来是被动形成进程， 我们还可以调用`fork()`函数手动创建一个新进程.

`fork`介绍:![image-20231217220015407](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231217220015407.png)



**返回值**

-   成功创建子进程后:父进程收到返回值子进程的PID，子进程收到返回值0
-   创建子进程失败后:父进程收到返回值-1，没有子进程被创建
-   pid_t是无符号整型![image-20231217220503841](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231217220503841.png)

**例子:**![image-20231217224418288](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231217224418288.png)

通过该示例我们可以得知

-   在`fork()`创建完子进程之后，父进程和新创建的子进程都会执行后续的代码，我们往往通过父子进程会接收到不同`fork()`返回值来控制父子进程完成不同的任务.
-   新创建的子进程的`ppid`是原来父进程的`pid`
-   父进程的接受fork()的返回值为创建出来的子进程的`pid`
-   子进程接收到的fork()返回值是0

>   对于fork()是如何做到返回2个值/为什么要规定返回给父进程的是子进程的pid而返回给子进程的是0?/为什么一个变量可以接收2个不同的返回值?，我们后面会介绍，我们先看fork()的应用

通常来说，当子进程被创建出来后，我们往往希望父子进程可以做不同的任务，因为我们可以通过fork()返回值来控制父子进程做不同的任务，下面是一个示例

![image-20231217230031556](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231217230031556.png)

>   根据fork()的返回值，当id==0时表示此时所处的进程为子进程，就可以通过if分支控制子进程需要完成的任务

**注意:**父子进程都会执行fork()之后的语句，父子进程都会执行判断语句，只不过父子进程会被if分支分流，

**示例:**![image-20231217230915854](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231217230915854.png)

接下来我们看到的现象应该是:

1.   两个死循环同时进行
2.   指令`ps ajx` 可以查看到这两个父子进程

现象一:![image-20231218142320554](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231218142320554.png)

现象二:![image-20231218142957049](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231218142957049.png)

至此，我们学会了如何创建一个子进程并让父子进程完成不同的任务.

前面说过:进程=可执行程序代码和数据+内核数据结构PCB，当父进程创建子进程时，操作系统会将父进程PCB中大部分属性拷贝给子进程的PCB，此时子进程的PCB才会指向父进程的代码(text段)和部分数据(data段)

**总结:**子进程的创建是以父进程为模板!![image-20231218144810841](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231218144810841.png)

接下来我们来对`fork()`进行几点解释

1.   <font color = blue>fork()为何要设计成父进程返回子进程的PID，子进程返回0</font>

     每个子进程只有唯一一个父进程，而一个父进程可以有多个子进程，因此父进程需要唯一的标识符才能找到特定的子进程，所以父进程需要保存子进程的PID便于后续控制子进程，而子进程大部分情况下不需要父进程的PID，更多的是考虑自己是否成功创建，子进程返回0则表示成功创建.如若子进程想要访问父进程，可以通过系统调用`getppid()`

2.   <font color = blue>fork()是如何做到返回2个值?</font>
     在fork()调用前，只有一个进程即父进程，在fork()内部一定会有创建进程的核心逻辑，当父进程在执行到fork()最后`return`语句说明fork()函数的核心逻辑(创建子进程)已经做完.一旦子进程被创建，后续的代码父子进程就会共享，`return`语句也会共享，所以fork()函数会返回2个值

3.   <font color = blue>id是一个变量，该变量如何接受2个返回值，即等于另有大于零?</font>
     id变量是如何同时具备两个值的?![image-20231218150936990](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231218150936990.png)

      **进程之间是具有独立性的**

     >   例如当你的运行网易云和WeChat，你的网易云崩溃了，这会影响到QQ吗?~显然不会，如果在特殊一点，当父进程退出时，子进程会退出吗? \~也不会，因为父子进程是独立的执行实体，具有独立的地址空间
     >
     >   通过`kill -9 PID`杀掉指定的进程
     >   ![image-20231218154651270](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231218154651270.png)

     既然进程之间是具有独立性，那么当父子进程对数据进行写入时，是不能够按照最简单的方式直接写入，否则一个进程的修改会引起另一个进程的修改，OS设计进程时是如何保证让进程具有独立性的呢?~当进程想要对数据进行写入时，操作系统会进行"写时拷贝"
     **写时拷贝:**当父子进程只有一个进程相对共享数据进行写入时，OS会将该数据拷贝到新的空间中，让想要写入的进程PCB指向新开辟的空间.

     现在回归正题，同一个变量是如何表示2个值?
     当fork()返回值给id时，本质就是对父子进程得共享数据进行了写入，OS会为变量id分配两个新空间，一个空间存放父进程的值(子进程得PID)，另一个空间存放子进程返回的值(0)，此时id只表示一段空间的名称，而我们现在有两段名称都为id的空间，2个空间就可以存放2个值，所以在我们看来id表示了2个值，实际上是不同空间上的两个值.

     其实C/C++程序中的所有变量名在编译后会变成地址或者偏移量，实际上我们看到的这个地址是虚拟地址，最后会经过映射，被操作系统和硬件转换为物理地址.

     PS:后续在地址空间章节中会对这点进行补充

如果我们想一次创建多个进程可以这么做
**demo代码:**

![image-20231218165221562](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231218165221562.png)

创建进程:
![image-20231218165302263](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231218165302263.png)

进程退出:10个子进程全部退出[defunct]
![image-20231218165345697](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231218165345697.png)

---

# 进程状态 

前面我们对`进程标识符`进行了说明，加下来我们对PCB的另一个属性—`进程状态`进行说明

## 浅谈进程排队

进程不是一直在运行的，即使它被加载到CPU中也不会一直被运行

1.   当进程等待某种软硬件资源时，进程就会进入阻塞状态，会将CPU资源让给其他进程
2.   当多个进程同时存在时，操作系统需要合理分配CPU的时间给这些进程以便共享CPU资源，CPU资源是有限的，所以每个进程只会在被分配的时间片中执行一定的指令，所以即使进程被加载到CPU中也不会一直被运行，可能处于等待被分配时间片的状态

当进程已经准备好运行但是没有获得时间片时就会进入到`就绪队列`[^1]

进程排队本质上是进程的PCB(而不是代码)处于就绪队列中等待CPU资源分配

>   当你面试投递简历时，面试官手上会存放很多简历，此时面试官会将你们的简历设置优先级，此时相当于你的简历在排队而不是你本身

<font color = blue>前面说过，操作系统通过链表管理PCB，而PCB在就绪状态时会进入队列，那么怎么满足PCB同时处于链表和队列中呢?</font>
我们之前在介绍进程属性时说PCB中有一个属性为指向下一个PCB的指针用于组织进程，这样的说法是不准确的!!!
Linux中通过**双向循环链表**将PCB连接起来，实际上PCB中是有一个循环双链表的属性而不是单个指针.

```c++
struct list_head {
    struct list_head *next， *prev;
};


struct task_struct {
    // 进程控制块的其他字段
    // ...


    struct list_head tasks;  // 双向循环链表节点
};
```

![image-20231218225353016](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231218225353016.png)在一个结构中，我们可以通过某个成员的偏移量和地址求出该成员所在结构的地址
在该链表中，我们可以通过`list_node`的偏移量求出`task_struct`起始地址，从而可以访问进程中的其他属性
task_struct中，我们可以通过&tast_struct=(task_struct\*)((char*)&member-offsetof(task_struct member)[^2]

>   `offsetof`的实现:
>
>   ```c++
>   #define offsetof(type,member) (size_t)&((char*)0->member)
>   ```



一个task_struct中存在多个list_head对象，有的list_head对象按照队列方式连接起来，有的按照链表的方式连接起来，这就实现了进程同时以队列和链表的方式管理.![image-20231219084155662](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231219084155662.png)当进程准备好被运行时，该进程的一个list_head节点连接到就绪队列中
当新增加一个进程时，就会新增加进程的list_head连接到双链表中，当进程退出时，只需要将对应的`task_struct`中list_head在双链表中删除即可.

这样就将对进程的操作转化为对数据结构的操作

**总结:**

1.   进程在排队一定是在等待某种转硬件资源
2.   进程排队本质是`task_struct`加入到就绪队列中
3.   一个`task_struct`可以被多个`list_head`连接到多个数据结构中

[^1]:用于存储处于就绪状态的进程的数据结构。就绪队列中的进程已经准备好执行，但由于系统资源（通常是CPU）正在被其他进程使用，它们暂时不能被调度执行。
[^2]: offetof(type， member)`是求出member在type中对于首个成员的偏移量

## 进程状态-运行，阻塞，挂起

前面说过，进程在等待软硬件资源时会进入阻塞状态，进程就绪但没有被分配时间片时会进入就绪状态.阻塞，就绪…都是进程的状态
进程状态保存在进程对应的`task_struct`中

1.   **进程状态本质上是一个整型变量**，

```c++
#define New 1
#define Ready2
#define running 3
#define block 4
```

2.   **状态决定了你的后续动作**
     当一个进程处于运行状态，它就会等待CPU的资源等待被调度，一个进程处于阻塞状态，它就会等待硬件资源…

### 运行状态

当进程准备好被CPU调度时，该进程就会进入运行状态。OS会在进程进行运行状态时将进程放在`运行队列`[^3]中

**一个CPU管理一个运行队列**
运行对列的属性有:队列结构队列大小、进程优先级、时间片、调整算法……
当进程将硬件资源准备好后，OS会将该进程对应的`task_struct`的`list_head`节点连接到`运行队列`中，从而使进程处于运行状态

```c++
struct run_queue
{
    //队列其他属性
    task_struct * q;
}
```

![](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231219125616911.png)

虽然理论上来说进程状态具有就绪状态、执行状态……实际上就绪状态和执行状态都可以称为运行状态，因为他们都会处于运行队列中，具体情况取决于特定的操作系统，Linux中将就绪状态和执行状态都称为R状态（运行状态）

[^3]:运行队列是一个按照某种调度算法（例如先来先服务、轮转调度、最短作业优先等）维护的数据结构，用于存储等待CPU执行的进程。

### 阻塞状态

当执行中的进程需要访问某个硬件资源，例如磁盘、网卡或键盘时，可能会发生进程进入阻塞状态的情况。在操作系统中，当进程发出访问硬件资源的请求后，如果该资源当前不可用，操作系统将该进程从运行队列中移出，并将其状态更改为阻塞状态。

为了有效地管理硬件资源的访问，操作系统通常为每个硬件定义一个结构体，例如 `struct device`，其中包含硬件的类型、操作方法、状态信息以及一个用于组织等待该设备资源的进程的双链表（`struct list_head node`）。进程在等待硬件资源时，会从运行队列中被移除，并插入到与该设备对应的队列中，此时进程处于阻塞状态。

阻塞状态的进程将等待硬件资源就绪的通知，一旦资源可用，操作系统将其重新加入运行队列，使其继续执行。这种阻塞和唤醒的机制是操作系统有效管理硬件资源的重要组成部分。

**struct device:**

```c++
strcut device
{
	int type;//1.磁盘2.网卡 3.键盘
	//设备的操作方法
	//状态
	struct list_head node;//设备通  过双链表组织
	task_struct* q;//设备对应的运行队列
}
```

当正在被CPU执行的进程等待硬件资源时，会将该进程从运行队列中拿出来放入到所需硬件对应的队列中接受该硬件资源，设备对应队列中的进程处于阻塞状态

**总结:**
当进程需要某种硬件资源时，并且该资源没有准备好，操作系统会

1.   将该进程的状态设置为阻塞状态
2.   将task_struct连接到等待设资源提供的队列中

### 挂起状态

前提: 计算机内存资源比较紧张时。当进程不会被CPU调度时，先将进程对应的代码和数据写入到磁盘的[swap分区](https://baike.baidu.com/item/SWaP/2666174)中，调度进程时在将代码数据写入回来，这样的进程状态称为挂起状态。

>   swap分区可以把磁盘虚拟成内存使用解决内存不足的问题，类似于 Windows中的虚拟内存。

写入到swap分区称为换出；写回到实际内存称为换入。![阻塞挂起](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231219204106638.png)

>   好处: 减少操作系统崩溃的风险. 坏处: 该进程执行可能会慢一点

常见的挂起有两种
**阻塞挂起：**进程在等待某种事件发生时被挂起。例如，当进程等待某个输入/输出操作完成、等待信号量释放或等待其他资源时，它可能会被挂起。一旦等待的事件发生，进程就可以被解挂（恢复执行）。
**就绪挂起：**进程在等待分配到 CPU 执行时被挂起。这可能发生在多道程序设计环境中，当有更高优先级的进程需要执行时，低优先级的进程可能会被挂起，等待重新调度执行。

挂起状态的说明：

1.   OS创建一个进程时先创建进程的PCB，再将数据和代码从硬盘拷贝到物理内存中，根据代码和数据初始化PCB，如果在将数据和代码拷贝到内存中时遇见了内存不足的情况，可以将部分的代码数据拷贝到物理内存，剩下的留在磁盘上。（对于这点，我们以后会进行代码演示）
2.   swap分区不会特别大，一般为内存的$1/2$倍或者$1$倍。
     换出换入都是数据拷贝，访问外设速度较慢，挂起本质是用时间换取可用性（空间）。若swap分区大，则操作系统非常依赖swap分区，导致IO交互频率高->效率低

状态的变迁，引起的是PCB会被OS变迁到不同的队列中！

## Linux下具体的进程状态

Linux源代码

```c
/*
* The task state array is a strange "bitmap" of
* reasons to sleep. Thus "running" is zero, and
* you can test for combinations of others with
* simple bit tests.
*/
static const char * const task_state_array[] = {
"R (running)", /* 0 */
"S (sleeping)", /* 1 */
"D (disk sleep)", /* 2 */
"T (stopped)", /* 4 */
"t (tracing stop)", /* 8 */
"X (dead)", /* 16 */
"Z (zombie)", /* 32 */
};
```

-   R（Running）：运行状态![image-20231220113403949](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231220113403949.png)
-   S （sleeping）：休眠状态，是浅度睡眠，可中断。休眠状态是一种阻塞状态。![](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231220114031171.png)CPU执行的语句的速度非常快，所以我们每次查看该进程状态时CPU都已经将一轮循环的语句执行完毕，剩下的就是sleep函数在执行，因此每次查看进程时%99.999……概率会发现进程处于浅度睡眠状态。![image-20231220115752585](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231220115752585.png)
-   D（Disk sleeping）：磁盘休眠状态，阻塞状态的一种，是深度睡眠，不可中断。磁盘休眠状态是一种阻塞状态。
    磁盘休眠状态的意义是防止OS在内存资源紧张时杀掉某一个具有重要作用的进程，将该进程状态设置为“深度休眠”告诉OS这个进程不能杀掉。通常和磁盘进行I/O交互的进程会被设置为“深度睡眠状态”。
    如果杀掉了该进程，当磁盘上的数据写入失败时，写入失败的消息没办法告诉给对应的进程，导致没有成功写入的数据就会丢弃（磁盘一直在做换入换出，没有办法一直保存未写入的数据）。
    解决办法：当重要的进程处于与硬件资源交互时，OS会为该进程进程状态设置为D状态，处于D状态的进程不能被OS杀掉
-   T（Stop）：暂停状态，进程需要读取硬件资源时，但是对应的硬件当前不允许进程读取，此时操作系统会将进程设置为T状态。暂停状态是一种阻塞状。
    `kill -l`可以查看对信号的操作，`kill -19 PID`对指定的进程设置T状态，该进程会从前台进程转化为后台进程`kill -18 PID`将指定的进程从T状态恢复到原本的状态。![image-20231220121142144](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231220121142144.png)
-   t（tracing）：被追踪状态，通常是进程被调试器使用的状态。被追踪状态是一种阻塞状态。![image-20231220122551646](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouoss-cn-hangzhouimage-20231220122551646.png)

-   z（zombie）：僵尸状态
    一个进程结束时，代码和数据先从内存中删除，而PCB包含了该进程退出数据的属性，当父进程读取到这个进程的退出数据后，PCB才会销毁，这个进程才是真正意义的 死亡状态，当一个进程死亡但是没有被它的父进程或者其他进程读取退出状态时，该进程处于僵尸状态。![image-20231220195225647](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231220195225647.png)<font color = blue>为什么要有“z”状态？</font>~告诉操作系统当前进程的退出数据没有被处理，暂时保留内存中存放退出数据的PCB结构。
    如果父进程一直不读取子进程的退出数据，那么子进程的PCB会一直残留到内存中，造成内存泄漏。
-   x（dead）：终止状态，进程结束的一瞬间处于“x”状态

>   关于进程状态后面的+号用来区分前台进程和后台进程：
>
>   -   **前台进程：**[./程序名字启动前台进程]，进程状态有+号，不会执行控制台的命令，可以通过`ctrl+c`杀死（自己写程序）
>   -   **后台进程：**[ ./程序名字 + & ]启动后台进程，进程状态无+号，会执行控制台的命令，不能通过`ctrl+c`杀死，通过`kill -9 `杀死（批量化处理 下载）
>
>   信号和网络部分会再次提及前后台进程

Linux中的进程状态转化和操作系统中的进程状态转化有一点不一样：
**Linux下进程状态**![image-20231220200134799](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231220200134799.png)**操作系统进程状态：![image-20231221135857210](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231221135857210.png)**

## 孤儿进程

在父子进程中，若父进程先于子进程退出，那么子进程会变为孤儿进程。

-   **子进程变为孤儿进程时会将父进程设为1号进程：**子进程变为孤儿进程时，为了让子进程的退出数据可以被读取到，OS通常会让1号进程（操作系统对应的进程）领养该进程。
-   **子进程变为孤儿进程时会从前台进程变为后台进程**
    ![image-20231221142019288](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231221142019288.png)

---

# 进程优先级

在多任务操作系统中，<u>有多个进程同时运行，而资源（如CPU时间）是有限的</u>。为了有效地分配和利用资源，操作系统需要确定每个进程的优先级，以便在竞争资源时能够合理地进行调度。

>   优先级和权限的关系：
>   通俗讲，优先级是确顶谁先执行，权限是决定谁能执行，一般而言具有高优先级的进程通常而言都具备执行某种操作的权限。

进程的优先级保存至`task_struct`中，优先级用一个整形变量存储

-   优先级的范围是[60,99]，数字越小，优先级越高 

-   用户可以通过`top`在任务管理器中调整优先级，用户不是直接修改pri，而是修改nice值（优先级的修正值）

-   pri（new） = pri（old） + nice

    每次调整时，OS会将该进程之前的优先级设置为80，即pri=80 + nice
    
    >   nice值范围[-20.19]

<font color = blue>优先级调整为什么要受限？</font>
如果不加限制，则我们可以将自己的优先级调整非常高，别人的优先级调整的非常低。优先级高的进程优先得到进程，后续有源源不断地进程产生，<u>常规的进程很难享受到CPU资源！</u>，导致`进程饥饿`[^4]。
任何分时操作系统，在调度上要进行较为公平地调度。

[^4]:进程饥饿，即为Starvation，指当等待时间给进程推进和响应带来明显影响称为进程饥饿。当饥饿到一定程度的进程在等待到即使完成也无实际意义的时候称为饥饿死亡

# Linux下的进程调度与切换

## 进程调度

>   引入：如果一个进程在运行时，CPU必须将该进程执行完才处理队列中的下一个进程吗？
>   ~当然不是，当进程进入死循环，CPU就会一直被占用，导致其他的进程无法被执行。对于我们实际写的死循环，我们发现其他的进程可以正常运行，因此CPU一定不是将一个进程执行完后再执行另一个进程。
>   这是因为**现代OS采用多任务调度执行进程。**
>
>   [百度百科:](https://baike.baidu.com/item/%E8%BF%9B%E7%A8%8B%E8%B0%83%E5%BA%A6/10702294)
>   ![image-20231225145730054](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231225145730054.png)
>
>   进程调度是按照某种调度算法尽可能地让所有进程公平地享有计算机资源！

常见的调度算法有：

1.   时间片轮转
2.   先来先服务（FCFS）
3.   最短作业优先（SJF）
4.   优先级调度
5.   多级反馈队列调度

进程具有的属性：

-   竞争性：进程的优先级决定了进程之间会相互竞争资源
-   独立性：一个进程退出与否不影响另一个进程的执行
-   并行性：多个进程在多个CPU分别同时进行，这称之为并行 
-   并发性：多个进程在一个CPU下采用`进程切换`的方式，在一段时间内，让多个进程都得以推进，称为并发。

>   进程调度和进程切换之间的关系：
>
>   1.   进程切换通常是由进程调度引发的。当调度算法决定切换到另一个进程时，OS会执行进程切换来实现这一决策。
>   2.   进程调度和进程切换都是为了确保多个进程能够在系统中公平地共享CPU资源，实现多任务执行。
>   3.   进程调度决定了什么时候切换，切换到哪个进程。进程切换决定了具体地进程切换操作。

## 进程切换

>   准备概念：
>   进程在运行的过程中，会产生大量的临时数据存放在CPU的寄存器中。
>
>   -   进程中创建的变量、中间计算结果会存放在相应的寄存器`eax`、`ebx`、`ecx`、`edx`（x86架构）/ `r0`、`r1`、`r2`（ARM架构）
>   -   指向栈顶的指针存放在寄存器`esp`（X86架构）/ `sp`（ARM架构）中
>   -   存放当前正在执行指令的地址的寄存器为`eip`（X86架构）/`pc`（ARM架构）
>   -   段寄存器`ECS`、`EDS`、`EES`、`ESS`、`EFS`、`EGS`
>
>   进程在CPU内部产生的的临时数据称为进程的`硬件上下文`。

当CPU调度另一个进程B时，会将先前调度进程A的上下文数据从CPU中拿出来保存到进程A对应的私有栈中，若进程B没有被调度过，则用进程B的上下文数据初始化CPU中寄存器，若进程B是二次调度，则在进程B对应的私有栈中找到保存的上下文数据，填恢复到对应的寄存器中即可（恢复上下文）。

注意：在Linux中，进程对应的私有堆栈是`task_struct`中的`tss_struct（任务状态段）`属性<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231225204301870.png" alt="image-20231225204301870" style="zoom:67%;" /><img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231225204343282.png" alt="image-20231225204343282" style="zoom: 67%;" />

**总结：**

-   CPU中有很多寄存器
-   进程运行时会在CPU中产生大量的临时数据（进程的硬件上下文）
-   进程调度结束时会将硬件上下文保存到task_struct中——保护上下文，调度进程时，如果是首次调度，初始化上下文；二次调度，恢复上下文。
-   不同的进程的上下文放在同一个CPU中，但是所有的数据都是被进程私有！

## Linux中进程调度算法

PS：如下调度算法基于Linux2.6内核版本。

Linux调度算法特性：

-   Linux下的调度算法必须满足的条件

    1.   考虑进程优先级

    2.   考虑饥饿问题

    3.   考虑效率

-   Linux下调度算法的时间复杂度为$O(1)$
-   Linux调度算法是基于时间片轮转的

Linux中通过`CPU运行队列`实现调度算法。下面我们来看一下运行队列的具体结构。

### Linux下CPU的运行队列

![img](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhoua89a89afbd2a40288ed4bb2cb4434241.png)queue[0]-queue[99]为实时进程的队列，本文只考虑作为分时进程队列的queue[100]-queue[139]。

1.   考虑优先级![image-20231225220122933](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231225220122933.png)`runqueue`中的`queue`属性是真正用来存放进程的，其中queue[100]-queue[139]是分时进程的队列，每一个队列中可以存放多个相同优先级的进程，queue[100]存放优先级为60的进程，queue[139]存放优先级为99的进程。为了先调度优先级高的进程，OS调度进程时从queue[100]开始遍历，queue[100]对应的进程队列是分时进程中优先级最高的进程。

2.   考虑饥饿问题
     若只考虑优先级，当在优先级低的进程已经处于排队状态中不断地加入优先级高的进程，那么处于排队状态中的进程始终无法得到CPU资源，会造成进程饥饿。
     解决办法是`runqueue`中创建一个array数组

     ```c
     struct q
     {
     	int nr_active;//活跃进程个数
     	int bitmap[5];//快速遍历待调度进程
     	task_struct* queue[140];//100个实时进程队列+40个分时进程队列
     }array[2];//array[0]最初是活跃进程，array[1]最初是过期进程
     ```

     array[0]最开始是活跃进程的进程队列，array[1]最开始是过期进程的进程队列,`runqueue`中的`active`指针最开始指向array[0],后续始终指向活跃进程；`expried`指针最开始指向array[1]，后续始终指向过期进程。正在处于排队状态的进程连接到活跃进程对应的队列中，而后加入的进程以及时间片用完的进程连接到过期队列中，CPU每次只执行活跃进程的代码，这样就可以保证后加入的进程即使优先级高也是连接到过期进程中不会影响活跃进程的进行。当活跃进程全部执行完时（nr_active==0），此时过期进程中可能积累了很多进程，此时只需要交换`active`指针和`expried`指针的值，使之前过期的进程成为新一批的活跃进程，从而被CPU调度。![image-20231225233224739](https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231225233224739.png)

3.   考虑效率<img src="https://sy--study-picture-for-typora.oss-cn-hangzhou.aliyuncs.com/oss-cn-hangzhouimage-20231225230404830.png" alt="image-20231225230404830" style="zoom:150%;" />**为什么要提高效率：**
     在选择进程调度时，OS每次都要从queue[100]遍历到queue[139],每次都需要遍历40个数并且判断对应的数组元素是否为NULL（即判断对应的队列是否有进程)，为了提高遍历效率，OS在runqueue中引入了bitmap数组。

     **bitmap：**
     bitmap由5个int数据构成，即160个比特位，用每一个比特位的位置表示进程的优先级，比特位对应的值表示该优先级队列是否有进程。

     **更快的找出待调度进程：**
     a遍历bitmap中的5个数，若该数bitmap[i]为0，说明对应的32个bit位都为0，即32个优先级队列都没有进程，若该数不为0，找出该bitmap[i]中为1的比特位k，则queue[2*i+k-1]的队列中就会有进程。这样OS每次只需要先遍历5个数，并只需要对bit位进行操作，可以提高效率。



**总结：**
runqueue中有struct q array[2],active,expired。struct q的结构有int bitmap[5],task_struct* queue[140],nr_active。queue中[0-99]是实时进程，[100-139]是分时进程， 分时进程的task_struct包含存放硬件上下文数据的相关属性。actice指向的进程是正在或即将运行的进程，expired指向的进程是新增的进程或者active中时间片用完的进程，当active->nr_active==0时，即活跃进程执行完毕，交换active指针和expried指针的值即可让之前处于过期进程队列中的进程处于活跃进程中。

