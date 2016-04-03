## 面试所学到的

### 面试经历

从三月份到四月份这段时间，一共面试了阿里、蘑菇街、猿题库、百度、豆瓣以及搜狗，应聘的岗位都是 `iOS` 开发实习生，写一个面试的总结吧，一是为秋招做一下经验铺垫，二是梳理一下三月份踩过的坑。当然如果对其他朋友有帮助，那再好不过。


## 面试题

### 计算机基础

* `TCP` 与 `UDP` 的区别，以及各自的用途－[参考链接](http://www.jianshu.com/notebooks/3194766/latest)
* `TCP` 为什么三次握手，四次挥手？－[参考链接](http://www.jianshu.com/notebooks/3194766/latest)
* `TCP` 流量控制与拥塞控制－[参考链接](http://www.jianshu.com/notebooks/3194766/latest)
* 计算机网络分为几层，这样做的好处是什么？你还可以举出其他分层的例子吗？
* 进程与线程的区别，共用的是堆内存还是栈内存－[参考链接](https://github.com/Wl201314/MartinBlog/blob/master/Blog/%E8%AE%A1%E7%AE%97%E6%9C%BA%E5%9F%BA%E7%A1%80/%E5%86%85%E5%AD%98%E4%B8%AD%E7%9A%84%E5%A0%86%E4%B8%8E%E6%A0%88%E5%88%B0%E5%BA%95%E6%98%AF%E6%80%8E%E4%B9%88%E5%9B%9E%E4%BA%8B%EF%BC%9F.md)
* 数据库中的数据表设计需要注意什么问题？
* `facade` 设计模式－[参考链接](http://www.jianshu.com/p/aa74fd5f2b9a)
* 工厂模式和抽象工厂模式的区别
* **推荐书籍：图解 HTTP、图解 TCP／IP、TCP/IP 协议簇、操作系统概念**
* **推荐博客：[TCP 与 UDP 详解](http://www.jianshu.com/notebooks/3194766/latest)、[网络面试基础](http://www.jianshu.com/notebooks/3276500/latest)**


### 算法基础

* 数组与链表区别
* 两个长链表求交点（考虑环）
* 堆排序，以及建堆的过程
* 反转单链表，反转单链表的部分区间－[参考链接](https://github.com/Wl201314/MartinBlog/blob/master/Blog/%E7%AE%97%E6%B3%95/%E4%BB%8E%E5%A4%B4%E5%AD%A6%E7%AE%97%E6%B3%95%EF%BC%9A%E5%8D%95%E9%93%BE%E8%A1%A8%E7%9A%84%E4%B8%80%E4%BA%9B%E6%93%8D%E4%BD%9C.md)
* 删除原排序数组内重复次数超过三次的数字（不开辅助空间）
* 百万数据寻找最大的十个数
* 连续子数组的最大和
* 快排的理解、时间复杂度，什么情况下时间复杂度最高
* 如何判断一个链表有环，以及入口点在那里
* 反转字符串`“I LOVE YOU”` 为 `“YOU LOVE I”`
* 找第一个不重复的字符
* 哈希的原理，以及处理冲突的方式
* **推荐书籍：剑指 Offer、LeetCode、编程之美**

### iOS 基础

* `MVC `的理解，以及各个模块间的通信是怎么样子的
* `Delegate` 与 `Block` 的区别
* 消息通知的种类，以及`KVO`、`Notification`、`delegate`的区别，效率比较
* 手动触发`KVO`，以及`KVO`的底层原理－[参考链接](https://github.com/ChenYilong/iOSInterviewQuestions/blob/master/01%E3%80%8A%E6%8B%9B%E8%81%98%E4%B8%80%E4%B8%AA%E9%9D%A0%E8%B0%B1%E7%9A%84iOS%E3%80%8B%E9%9D%A2%E8%AF%95%E9%A2%98%E5%8F%82%E8%80%83%E7%AD%94%E6%A1%88/%E3%80%8A%E6%8B%9B%E8%81%98%E4%B8%80%E4%B8%AA%E9%9D%A0%E8%B0%B1%E7%9A%84iOS%E3%80%8B%E9%9D%A2%E8%AF%95%E9%A2%98%E5%8F%82%E8%80%83%E7%AD%94%E6%A1%88%EF%BC%88%E4%B8%8B%EF%BC%89.md#50-%E5%A6%82%E4%BD%95%E5%85%B3%E9%97%AD%E9%BB%98%E8%AE%A4%E7%9A%84kvo%E7%9A%84%E9%BB%98%E8%AE%A4%E5%AE%9E%E7%8E%B0%E5%B9%B6%E8%BF%9B%E5%85%A5%E8%87%AA%E5%AE%9A%E4%B9%89%E7%9A%84kvo%E5%AE%9E%E7%8E%B0)
* `Objective-C` 的`Copy`在那些场景下使用－[参考链接](https://github.com/ChenYilong/iOSInterviewQuestions/blob/master/01%E3%80%8A%E6%8B%9B%E8%81%98%E4%B8%80%E4%B8%AA%E9%9D%A0%E8%B0%B1%E7%9A%84iOS%E3%80%8B%E9%9D%A2%E8%AF%95%E9%A2%98%E5%8F%82%E8%80%83%E7%AD%94%E6%A1%88/%E3%80%8A%E6%8B%9B%E8%81%98%E4%B8%80%E4%B8%AA%E9%9D%A0%E8%B0%B1%E7%9A%84iOS%E3%80%8B%E9%9D%A2%E8%AF%95%E9%A2%98%E5%8F%82%E8%80%83%E7%AD%94%E6%A1%88%EF%BC%88%E4%B8%8A%EF%BC%89.md#3-%E6%80%8E%E4%B9%88%E7%94%A8-copy-%E5%85%B3%E9%94%AE%E5%AD%97)
* `Runtime` 的消息传递和消息转发－[参考链接](http://www.ianisme.com/ios/2019.html)
* `load` 与 `initialize` 的区别 －[参考](http://www.jianshu.com/p/d25f691f0b07) 
* `method swizzle`原理－[参考链接](http://southpeak.github.io/blog/2014/11/06/objective-c-runtime-yun-xing-shi-zhi-si-:method-swizzling/)
* `runtime`：字典转模型 － [参考](http://www.jianshu.com/p/cecfe78e9cd8)
* `isMemberOfClass` 和 `isKindOfClass` 的区别（从源码角度分析）
* 多线程你了解几种？有什么区别呢？-[参考链接](https://bestswifter.com/multithreadconclusion/)
* `operation`相比`GCD`的优势？-[参考链接](https://bestswifter.com/multithreadconclusion/)
* 数据持久化方案有哪些？`CoreData`了解吗？`CoreData`版本迁移注意什么？－[参考链接](http://www.chun.tips/blog/2014/11/28/core-data-ban-ben-qian-yi-jing-yan-zong-jie/)
* `ViewController` 生命周期，详细介绍一下`loadView`－[参考链接](https://bestswifter.com/uiviewlifetime/)
* `Runloop` 基本概念，猜想一下内部是怎么实现的－[参考链接](http://blog.ibireme.com/2015/05/18/runloop/)
* `Runloop` 的休眠和唤醒是怎么回事？是怎么完成的（底层原理）－[参考链接](http://blog.ibireme.com/2015/05/18/runloop/)
* `Runloop`的实际运用有哪些？－[参考链接](http://blog.ibireme.com/2015/05/18/runloop/)
* `Objective-C`  中对象等同性怎么做？
* `Autorealsepool` 的使用场景，`Autorealsepool`什么时候释放？－[参考](http://www.jianshu.com/p/f95b9bfda4a0)
* 讲一下浅拷贝和深拷贝吧 - [参考](https://www.zybuluo.com/MicroCai/note/50592)
* `Objective-C`字典中`Key`、`Value`有什么特别的要求
* `block` 的概念、本质、分类以及所带来的问题－(建议看多线程和内存管理一书)
* `MRC` 与 `ARC` 下 `blcok` 的区别
* 聊一下`block` 的 `strong weak dance` - [参考](http://www.jianshu.com/p/4ec18161d790)
* 读过那些开源代码？请介绍其中一个
* 以下两种方式的区别： - [参考](http://www.jianshu.com/p/f95b9bfda4a0)
	
		imageView?.image = UIImage(named: name)
		imageView?.image = UIImage(contentsOfFile: path)
		
* **推荐书籍：多线程和内存管理、Effective Objective-C 2.0、**

### 经验型题目 

* 对于`A`、`B`、`C`、`D`四个任务，完成`ABC`之后才可以去做`D`，你会怎么设计？
* 对于`ABCDE`五个任务，完成`AB`之后可以执行`D`，完成`BC`后可以去做`E`，你会怎么设计？ － [参考链接](https://github.com/Wl201314/MartinBlog/blob/master/Blog/%E9%9D%A2%E8%AF%95%E9%A2%98/%E5%A4%9A%E7%BA%BF%E7%A8%8B%EF%BC%9AA%E3%80%81B%E5%AE%8C%E6%88%90%E4%B9%8B%E5%90%8E%E5%8E%BB%E5%81%9AD%EF%BC%8CB%E3%80%81C%E5%AE%8C%E6%88%90%E4%B9%8B%E5%90%8E%E5%8E%BB%E5%81%9AE.md)
* 数据缓存怎么做？没做过的话猜想一下嘛！
* 怎么判断`Cell`是否在屏幕中？
* 解决多次点击按钮导致重复网络请求的方法 － [参考链接](http://blog.csdn.net/uxyheaven/article/details/48009197)
* 一个`View`，放了单击和双击的手势，如果我点击两次什么效果
* 你使用过那些设计模式？讲一下细节
* 你使用 `ARC`的时候，一般`ARC`会带来什么问题
* 你会怎么样进行软件测试－ （ `iOS` 测试指南（羋峮））
* 网络有没有遇到不稳定的情况？怎么处理
* `Git` 分支命令
* 做过哪些性能优化？谈一下详细的实践 － [参考](http://www.jianshu.com/notebooks/3050330/latest)
* `TableView` 优化 －[参考](http://longxdragon.github.io/2015/05/26/UITableView%E4%BC%98%E5%8C%96%E6%8A%80%E5%B7%A7/)
* 你的开源项目是使用了`AutoLayout`布局，说一下`layoutSubView`,重写过`sizeToFit`吗？－ [参考](https://github.com/Wl201314/MJianshu)
* 你的项目是用`MVC`，是怎么解决臃肿的`ViewController`问题的？－ [参考](http://oncenote.com/2015/12/08/How-to-build-UI/)

### 综合问题
* 在项目中遇到那些难点？最后怎么解决的？
* 你最近接触过什么新技术呢？
* 使用过哪些工具，都是用来做什么？
* 平时怎么学习的？读过哪些书？经常关注哪些国内外博客
* 为什么选择 `iOS `开发呢？
* 为什么最初选择 `Swift`，而现在往` Objective-C` 转呢？
* `Swift` 与 `Objective-C` 的区别是什么？
* 说一下你的职业规划
* 你还有什么要问的吗？

## 所踩的坑
### 关于简历
* **最好只写自己熟练的知识:** 一面往往围绕简历来问，不熟悉的技术千万不要往上写，我当时自己写的App，就写了一个独立完成开发、测试，结果就被问到了测试，答得很差
* **建议使用STAR模型：**对于项目过程和个人贡献尽量写的详细，都说简历作假严重，这样更容易突出简历的真实性和表现个人能力
* **然后就是简洁呀，我和小伙伴都是直接使用的`MarkDown`,感觉效果还不错－[参考](https://github.com/geekcompany/ResumeSample)**
* **电话最好隔开写，比如（155-6615-9700）,更便于`HR`联系你**

### 关于说话

* 我也没有太多去看面经，就感觉最初犯了一个禁忌：面试表达观点的时候不要说**好像**、**大概**、**或许**这些词语。。。。。。。。。

### 关于准备

* 纵使基础再好，面试前还是要看看学长们的面试题的，这样你可以更好的组织语言，表达的更好清晰和完善
* 一定要认真刷算法题目，本人就是吃了算法的亏，所面几个厂都有算法题目，而且有的让你现场写代码－[可以参考这个大神的经历](http://www.jianshu.com/p/1a60a3f159a7)
* 目前阶段准备面试语言方面更多是准备`Objective-C`，我有同学说只做`Swift`，我就想他什么时候可以找到实习呢！！所面的几个厂只有豆瓣有一些项目开始采用`Swift`,但是面试题也都是问`Objective-C`
* 刷几道题总是不够的，感觉要提前几个月准备，完善知识体系，主要包括iOS、算法、计算机网络、操作系统
