# Why Parallelism? Why Efficiency?

### Demo1

16 sum 1 person  vs 16 sum 2 person

### Speedup

Speedup(p processors) = Time(1) / Time(p)

从第一个demo可以看出，加速方法有加速计算，或者加速交流的速度

### Demo2

4个人加四个数字，但只能写在纸上，传给下一个人

这个例子当中笔和纸是独占的，而且写完了只能干瞪眼，所以要加速计算，可以通过合理的分配方法

### Demo3

全班把自己看到的数字全加起来(Massive parallel execution)

交流的时间比算的时间多很多很多，因此并行计算当中交流会限制speedup



- Thinkings

并行要根据不同的硬件设计

Fast is not Efficient! 用10个处理器只获得两倍加速，它真的效率高吗？

不能只从软件的角度来思考（充分利用机器的硬件），也要从硬件设计者的角度来考虑（能力/开销？时间开销，能耗开销，价格开销，硅开销？）



## Concurrency & Parallel

并发的不一定是并行计算的（2003年调用pthread和今天调用pthread的区别，前者需要的是异步，后者需要的是并行）

## Why parallel processing

早期摩尔定律生效的时候，想让代码并行没啥用，因为每18个月算力翻一倍

十年之前，处理器主要优化了以下两个部分：

- 时钟效率提高
- 开发指令层面的并行（Instruction Level Parallelism)

#### What does a processor do?

按照顺序执行指令，一种加速方法是让执行指令的速度变快，第二种方法是一堆指令并行跑(Superscalar execution)，只要指令是按照某种顺序执行的

- ILP Example

`a = x*x + y*y + z*z`

首先三个乘法是独立的，可以让三个乘法指令并行，之后加法是不独立的，只能串行执行

加速也取决于每个处理器可以并行执行多少指令，比如对于一个4指令并行和16指令并行，跑上面这个程序speedup是差不多的

因此ILP很容易遇到瓶颈（差不多在2005年之后就没有太大的提升了）

对于始终周期也是一样，在00年左右就没有提升了

#### Power wall

能耗在现代设计当中非常非常重要，晶体管在inactive的时候会有能耗，动态运动的时候也会有能耗，因此，能耗会决定效率的上限
