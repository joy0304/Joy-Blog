
## 页置换相关算法：
### FIFO

先进先出，置换先进来的页

### LRU

`Least Recently Used`：最近最少使用算法

置换在过去时间内最长时间没有使用的页


### OPT 或 MIN

`Optimal page-replacement algorithm`： 最优页置换算法

置换在未来时间内最长时间不会使用的页


## CPU 调度相关算法

### FCFS

`first-come,first-served scheduling algorithm`：先到先服务调度算法

* 非抢占

### SJF

`shortest-job-first scheduling algorithm`：最短作业优先调度算法

* 可能是非抢占的
* 也可能是抢占的：这时候就会变成最短剩余时间优先调度(`shortest-remaining-time-first scheduling`)

### 优先级调度

`priority scheduling algorithm`：谁的优先级高谁就先执行

### 轮转法调度（`round-robin,RR`）

类似于先到先服务，但是增加了抢占以切换进程，定义一个较小时间单元，称为时间片






