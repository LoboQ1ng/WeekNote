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



