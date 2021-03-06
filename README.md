# wander
go on foot

## 知识储备
### 1. 二分查找和各种变种的二分查找
对应的代码文件为:`BinarySearch.go`
```go
package main
// IBinarySearch 二分法查找及其变种
type IBinarySearch interface {
	// 参数释义
	// arr 给定有序数组
	// start 初始序号
	// end 结尾序号
	// length 数组长度
	// searchValue 待查找的值

	// Recursion 二分查找 - 递归查找
	Recursion(arr []int, start, end, searchValue int) int
	// Normal 二分查找 - 常规非递归查找
	Normal(arr []int, searchValue int) int
	// EqualFirst 二分查找变种 - 查找与所查找的数相等的第一个数
	EqualFirst(arr []int, length, searchValue int) int
	// EqualLast 二分查找变种 - 查找与所查找的数相等的第一个数
	EqualLast(arr []int, length, searchValue int) int
	// MoreThanOfFirst 二分查找变种 - 查找第一个大于key的值，也就是说返回大于key的最左边元素的下标。
	MoreThanOfFirst(arr []int, length, searchValue int) int
	// LessThanOfLast 二分查找变种 - 查找最后一个小于key的元素，也就是说返回小于key的最右边的元素下标。
	LessThanOfLast(arr []int, length, searchValue int) int
}
```

### 2. 各类排序算法以及复杂度分析（快排、归并、堆）
参考: `Sort.go` 文件
```bash
https://blog.csdn.net/hellozhxy/article/details/79911867 (10大算法)
https://blog.csdn.net/liang_gu/article/details/80627548  (7大算法)
```
```go
package main
// 排序
type ISort interface{
	// BubbleSort 冒泡排序 - 先从数组中找到最大值(或最小值)并放到数组最左端(或最右端)，
	// 然后在剩下的数字中找到次大值(或次小值)，以此类推，直到数组有序排列。算法的时间复杂度为O(n^2)。
	// 最佳情况：T(n) = O(n)   最差情况：T(n) = O(n2)   平均情况：T(n) = O(n2)
	BubbleSort(arr []int) []int

	// SelectionSort 选择排序 - 首先在未排序序列中找到最小（大）元素，存放到排序序列的起始位置，然后，
	// 再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。以此类推，直到所有元素均排序完毕
	// 最佳情况：T(n) = O(n2)  最差情况：T(n) = O(n2)  平均情况：T(n) = O(n2)
	SelectionSort(arr []int) []int

	// InsertSort插入排序 - 通过构建有序序列，对于未排序数据，在已排序序列中从后向前扫描，找到相应位置并插入。
	// 插入排序在实现上，通常采用in-place排序（即只需用到O(1)的额外空间的排序），因而在从后向前扫描过程中，
	// 需要反复把已排序元素逐步向后挪位，为最新元素提供插入空间。
	// 最佳情况：T(n) = O(n)   最坏情况：T(n) = O(n2)   平均情况：T(n) = O(n2)
	InsertSort(arr []int) []int

	// QuickSort 快速排序 - 通过一趟排序将待排记录分隔成独立的两部分，其中一部分记录的关键字
	// 均比另一部分的关键字小，则可分别对这两部分记录继续进行排序，以达到整个序列有序。
	// 最佳情况：T(n) = O(nlogn)   最差情况：T(n) = O(n2)   平均情况：T(n) = O(nlogn)　
	QuickSort(arr []int,start,end int) []int
}
```

### 3. 各类算法题（手写）
更多算法, 未实现代码......
```go
	// 归并排序
	MergeSort(arr []int)
	// 堆排序
	HeapSort(arr []int) []int
	// 希尔排序 - 希尔排序(Shell's Sort)在插入排序算法的基础上进行了改进，算法的时间复杂度与前面几种算法相比有较大的改进。其算法的
	// 基本思想是：先将待排记录序列分割成为若干子序列分别进行插入排序，待整个序列中的记录"基本有序"时，再对全体记录进行一次直接插入排序。
	ShellSort(arr []int) []int
	// 计数排序
	CountingSort(arr []int) []int
	// 桶排序
	BucketSort(arr []int) []int
	// 基数排序
	RadixSort(arr []int) []int
```

### 4. 理解并可以分析时间和空间复杂度。
```bash
https://www.cnblogs.com/zknublx/p/5885840.html
```
### 5. 算法和数据结构数组、链表、二叉树、队列、栈的各种操作（性能，场景）
1. 数组  
    数组存储的数据在地址空间上是连续的。
    方便数据的查找，查找数据的时间复杂度为O(1）。
2. 链表  
    链表存储的数据在地址空间上可连续，可不连续。
    链表中的每一个节点都包括数据和指向下一个地址的指针。
    查找数据的时间复杂度为O(n)，方便数据的增删。
3. 栈  
    栈是一种先入后出的逻辑结构，每次加入新的元素和拿走元素都在顶部操作。
4. 队列  
    队列是一种先入先出的逻辑结构，对元素的操作分别在对头和队尾，元素的插入在对尾，元素的删除在对头。
5. 二叉树  
    每个节点至多只有两个子树的结构，在父节点中有指向左右子树的指针
    先序遍历：根–左–右
    中序遍历：左–根–右
    后序遍历：左–右–根
    查找二叉树：左子树的值小于根节点的值，右子树的值大于根节点的值，在插入数据时，从根节点开始往下比较，小于比较值则放在左边，大于比较值放在右边。插入一个值的时间复杂度是O(logn)
    平衡二叉树：左右子树的高度差的绝对值不超过1 

### 6. 红黑树、AVL树、Hash树、Tire树、B树、B+树、跳跃树。
概念: https://blog.csdn.net/daaikuaichuan/article/details/80778955

### 7. 图算法（比较少，也就两个最短路径算法理解吧）
### 8. 动态规划（笔试回回有。。）、贪心。
入门示例: 
```
三角形最大和: https://blog.csdn.net/baidu_28312631/article/details/47418773
几个Demo: https://blog.csdn.net/u013309870/article/details/75193592
```
### 9. 计算机网络OSI7层模型（TCP4层）每层的协议
### 10. TCP/IP三次握手、四次挥手
### 11. 拥塞控制（过程、阈值）
### 12. 流量控制与滑动窗口
### 13. TCP与UDP比较

### 14. http/https 1.0、1.1、2.0
### 15. url到页面的过程
### 16. get/post 以及幂等性
### 17. http 协议头相关
### 18. 网络攻击（CSRF、XSS）
### 19. DDos攻击

### 20. 数据库（最多的还是mysql，Nosql有redis）索引（包括分类及优化方式，失效条件，底层结构）
### 21. sql语法（join，union，子查询，having，group by）
### 22. 引擎对比（InnoDB，MyISAM）
### 23. 数据库的锁（行锁，表锁，页级锁，意向锁，读锁，写锁，悲观锁，乐观锁，以及加锁的select sql方式）
### 24. 隔离级别，依次解决的问题（脏读、不可重复读、幻读）
### 25. 事务的ACID
### 26. B树、B+树
### 27. 优化（explain，慢查询，show profile）
### 28. 数据库的范式。
### 29. 分库分表，主从复制，读写分离。
### 30. Nosql相关（redis和memcached区别之类的，如果你熟悉redis，redis还有一堆要问的）
### 31. 操作系统：进程通信IPC（几种方式），与线程区别
### 32. OS的几种策略（页面置换，进程调度等，每个里面有几种算法）
### 33. 互斥与死锁相关的

### 34. 子网划分（一般只有笔试有）
### 35. (B)IO/NIO/AIO三者原理，各个语言是怎么实现的
### 36. Linux内核select poll epoll
### 37. linux常用命令（问的时候都会给具体某一个场景）
### 38. Linux内核相关（select、poll、epoll）

### 39. 其他扩展技能（这个方方面面太多了，全部掌握基本上不可能，只是作为大家其他时间扩充技能的参考）
### 40. 分布式架构：（了解原理就行，如果真的有实践经验更好）CAP原理和BASE理论。
### 41. Nosql与KV存储（redis，hbase，mongodb，memcached等）
### 42. 服务化理论（包括服务发现、治理等，zookeeper、etcd、springcloud微服务、）
### 43. 负载均衡（原理、cdn、一致性hash）
### 44. RPC框架（包括整体的一些框架理论，通信的netty，序列化协议thrift，protobuff
### 45. 消息队列（原理、kafka，activeMQ，rocketMQ）
### 46. 分布式存储系统（GFS、HDFS、fastDFS）、存储模型（skipList、LSM等）
### 57. 分布式事务、分布式锁等
### 58. 搜索引擎与技术
