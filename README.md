最近找实习投简历（2025-2-25），一个面试机会都没有。欠缺的东西太多了，打算记录一下此后的学习历程。以周为单位，个人博客会更新一些笔记：[Q1ng's Blog](https://loboq1ng.github.io/)

# Week 1（2025.3.2 ~ 2025.3.8）

这周主要使用`Hexo`和`github pages`搭建个人博客，记录一下二进制的学习之路。

刷Pwn.college的Reverse，以及一些之前板块中更新的题目（虽然那些题目难度不大，但是我看着前面那些模块不是100%有点难受...）。大概包括**Talking Web**模块（36个Challenges）、**Dealing with Data**模块（19个Challenges）、**SQL Playground**模块（10个Challenges）、**Reverse**模块（完成了20Challenges）

看了篇论文`FUZZILLI: Fuzzing for JavaScript JIT Compiler Vulnerabilities`，以及把fuzzilli项目跑了跑。

其实，我之前所学也就是二进制的入门，Fuzz所接触到的，也就是看完AFL源码，调试AFL++的源码，跑了个FuzzBench而已。因此，在初接触到JIT的Fuzzer时，确实有点不知所措。这篇论文就看了三天没看完。得改一改看论文的效率了...丢给AI就好了。哪里不理解就直接问AI。



# Week 2 (2025.3.9 ~ 2025.3.15)

这周阅读了两篇JIT优化漏洞的博客：[JITSpoitation I](https://googleprojectzero.blogspot.com/2020/09/jitsploitation-one.html)和[JITSpoitation II](https://googleprojectzero.blogspot.com/2020/09/jitsploitation-two.html)，这个系列还有第三章，但是那一章纯是缓解机制的绕过，而我主要是想了解Fuzz这块儿在JIT中的利用，因此就不浪费时间去看了。以及漏洞`CVE-2020-9802`的复现，也就是博客中所说的漏洞。

然后，看了1/10左右的Fuzzilli官方项目文档。关于fuzzilli的介绍挺详细的，因此要细看，下周争取看完它。然后搭建了swift的debug环境，vscode的lldb调式swift项目。踩踩坑后，现在也是成功能够debug了。

这周也终于是把pwn.college的Reverse Engineering刷完了。从`level 19.0`开始，到`level 22.1`共8关。刷了挺久的。



# Week 3 (2025.3.16 ~ 2025.3.22)

这周一直在刷题，想尽快把pwn.college刷到堆部分。下周再看一下fuzzilli的源码吧，因为要开组会了。

pwn.college的Intermediate Memory Errors模块刷完了。（写了18个challenges）

Return Oriented Programming模块还差爆破部分。（写了24个challenges，还差最后的6个challenges就过了）

这周有点小摆，不过刷题还是有意思的。不过这周同研三师兄们聚餐时，发现安全的岗位是少的多，也卷得多。大家就算已经签约了，也依然在担忧裁员，担忧未来。



# Week 4 (2025.3.23 ~ 2025.3.29)

这周好像状态挺好的，可能是因为fuzzilli的源码写得很好，让人看起来非常身心愉悦。

首先把fuzzilli的项目文档看完了，然后源码部分是把fuzzilli的整体框架看完了，然后重点细看了它的插桩（以V8引擎编译脚本为对象），然后还看了看JSC的编译脚本。它和AFL不一样，AFL自己写了个编译`afl-clang/gcc/g++`的插桩编译工具，封装好了的。而对于fuzzilli来说，我看到的是V8和JSC的源码中是包含了`fuzzilli`的编译脚本的。也就是这些引擎本身就支持了fuzzilli，然后因为之前对llvm的插桩不是很理解，也就是编译过程中有关`sanitizer`的参数，这周细细看了一下: [SanitizerCoverage — Clang 21.0.0git documentation](https://clang.llvm.org/docs/SanitizerCoverage.html#inline-bool-flag)

然后，pwn.college也是成功入heap了，看了下ASU的课。总结：

- pwn.college的ROP module（完成最后6个challenges）
- 阅读fuzzilli项目文档
- 阅读fuzzilli源码（框架流程，插桩等）
  - 进一步需看多线程以及Reprl模式



# Week 5 (2025.3.30 ~ 2025.4.6)

将fuzzilli的Reprl模式看完，它给每个target源码编译时都加上回调函数，拿v8为例，v8支持fuzzilli编译。它会改变v8的源码，以接收父进程的`exec`信号以及`read`系统调用循环读取父进程的输入（这里父进程使用`memcpy`进行内存映射，而子进程进行`read`读取）

看了篇论文`fuzzJIT`，有点没太理解作者的意思。所以打算进一步看看源码，想做一个对fuzzilli的改进research，没有idea，先看看别人对fuzzilli的改进。`ProgramTemplate`是一个很规律的结构，看看能不能好好利用一下。



# Week 6 (2025.4.7 ~ 2025.4.13)

pwn.college的**Dynamic allocator misuse**模块写了30个challenges，剩10个challenges。

堆是一个很大的内容，目前这里只涉及到了`Tcache bin`和一些保护措施。



# Week 7 (2025.4.14 ~ 2025.4.20)

做PPT，算法课要汇报了。以及下周和zgc lab的大佬Zhiyi Zhang进行讨论，所以PPT准备得充分些。但是看完FuzzJIT的源码发现这个研究是结果好，在fuzzilli的基础上写了一个Profile，拿到了四个浏览器引擎的很多漏洞。



# Week 8 (2025.4.21 ~ 2025.4.27)

完成pwn.college的**Dynamic allocator misuse**模块（最后10个challenges），然后看了project zero关于LLM 辅助OSS-Fuzz的三篇博客，其中将Target拆解，并使用*fuzz-introspector*进行分析，对于低hits的函数将其源码发送给LLM，并给予相应的Prompt使其生成harness，随后使用libfuzzer+harness来突破这个函数的低覆盖率情形，也就是说LLM会生成harness + 一些初始test case + 可编译Target。这个workflow确实牛逼，但是目前`oss-fuzz-gen`是否能生成非oss-fuzz项目的yaml文件以及harness还未可知，可以做个Observation试试水。

把这一个多月以来关于浏览器引擎Fuzz的部分总结了一下，下周汇报听听前辈们的意见。~~做点科研还真难哇.O.o.~~



# Week 9 (2025.4.28 ~ 2025.5.4)

同Zhiyi Zhang讨论结束后，我调研的浏览器引擎Fuzz没啥大的意义，因为没有发现问题，没有发现问题直接改进Fuzz那是无厘头的，改进Fuzz一定是朝着解决某类/个问题的方向去改进的，因此我需要花费很长的时间去找找最近一年浏览器引擎中某一类漏洞的所有攻击面，总结并尝试找到问题。

好吧，这大概是我第一次发现科研和实际贴合得这么近的时刻。恰逢五一，还挺颓废的.O.o.



# Week 10 (2025.5.5 ~ 2025.5.11)

本周完成pwn.college的`Program Exploitation`，共18道题。`Program Security`整个大的模块已经全部over了，接下来就去`system security`里遨游吧。在做pwn.college的时候，真的可以沉溺在其中，*一个恍惚就一天过去了。*



# Week 11 (2025.5.12 ~ 2025.5.18)

主要在搭建`oss-fuzz-gen`，因为项目文档有点粗糙，搭了很久，一直跑不通。解决“墙”的问题就解决了几次。顺带其中的`libfuzzer`也简单看了下。想跑`oss-fuzz-gen`的成本有点高，既要API又要大量proxy的代理流量。现在我想知道为什么它一直在创建docker？这么多个images和container，我现在认为它在创建实例的过程中，创建一批后才开始运行。（不然没理由运行容器几十秒，然后容器内的指令只有`exit`）

最前沿的东西，果然难搞。(T__T)



# Week 12 (2025.5.19 ~ 2025.5.25)

把oss-fuzz-gen调试了一遍，以xpdf为目标。解答了我之前一直跑，一直创建镜像和容器但没结果的疑惑，因为AI生成的harness编译错误，但是报错信息并不会回传给LLM，`oss-fuzz-gen`里只会将`no member`类型的报错信息作为`context`发回给LLM，而它生成的harness报错最多的是`no type name`，这就有意思了。oss-fuzz-gen尝试不把报错信息返还给LLM，而是加了个IMPORTANT提示，说要注意引入一些头文件来解决`no type name`的问题，结果就是它一直在解决这个问题，从而导致100轮迭代都没能解决成功。

此外，做了个PPT汇报Fuzz，顺带理解了`AddressSanitizer`的原理，或许有些洞不仅需要给target额外插桩，还需要自定义sanitizer才能检测。



# Week 13(2025.5.26 ~ 2025.6.1)

了解完整个`oss-fuzz-gen`的流程，以及**端午小摆一下**

`oss-fuzz-gen`中发现的漏洞使用的模型是经过训练的，它的训练数据是当前所有手工编写的harness，所以此前我所做的实验都无法将其成功复现。而`oss-fuzz-gen`是将API的源码以及签名给了LLM，随后直接让它生成harness。思路值得借鉴，但是步子有点太大了。可能google能够通过大量的算力资源来对模型进行微调训练，提高生成harness的可用性。因此，想想其他的办法，我首先用`Xpdf`为例，和`gpt-4o`交互后生成了一个可用的，低覆盖率API的harness。其实际也没有提高多少覆盖率，触发大量的错误处理。

该如何让LLM生成大量可用的harness呢？或许利用静态分析拿到一些tree？或许...-.-



# Week 14 (2025.6.2 ~ 2025.6.8)

完成pwn.college的**Sanboxing**模块（共18个challenge）。其余时间在上课，以及申请CSC。吐槽一下：材料盖章真的很麻烦，因为本人情况还真special：身处杭州，要本部的章，导师既不在杭州，也不在本部。跑来跑去，真是麻烦！

下周应该主要研究一下`CVE-2025-37899`和`CVE-2025-37778`，只能说祝我好运~
