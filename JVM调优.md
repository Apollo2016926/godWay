-XX:AutoBoxCacheMax=20000   调整永久代中Integer缓存的大小 -128~20000  

CMSInitiatingOccupancyFraction=75 当老年代堆空间的使用率达到75%的时候就开始执行垃圾回收,CMSInitiatingOccupancyFraction默认值是92%,这个就太大了。参数必须跟下面两个参数一起使用才能生效的。 

-XX:+UseConcMarkSweepGC 

-XX:+UseCMSInitiatingOccupancyOnly  

-XX:MaxTenuringThreshold=6   改变新生代晋升到老年代需要经历的GC次数 

-XX:NewRatio=1   GC最多的还是发生在新生代的young gc,所以可以提高一下新生代在整个堆的占用比例,建议设置为对半分,尽量避免young gc

-XX:+ DisableExplicitGC来禁止RMI调用System.gc 

-XX:+UseCMSCompactAtFullCollection开关参数，用于在“享受”完Full GC服务之后额外免费赠送一个碎片整理的过程，内存整理的过程无法并发的，空间碎片问题没有了，但提顿时间不得不变长了，JVM设计者们还提供了另外一个参数 -XX:CMSFullGCsBeforeCompaction,这个参数用于设置在执行多少次不压缩的Full GC后,跟着来一次带压缩的。

