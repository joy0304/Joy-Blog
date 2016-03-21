## 多线程：A、B完成之后去做D，B、C完成之后去做E


### 第一种思路：利用`GCD`的`group`来完成。把`ABC`放进一个队列里面，然后`group1`来监听`AB`任务，`group2`监听`BC`任务，最后执行`notify`任务

	dispatch_queue_t queue = dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0);
    
    dispatch_group_t group1  = dispatch_group_create();
    dispatch_group_t group2  = dispatch_group_create();
    
    dispatch_group_enter(group1);
    dispatch_async(queue, ^{
        NSLog(@"A开始");
        sleep(arc4random_uniform(10));
        NSLog(@"A结束");
        dispatch_group_leave(group1);
    });
    
    dispatch_group_enter(group1);
    dispatch_group_enter(group2);
    dispatch_async(queue, ^{
        NSLog(@"B开始");
        sleep(arc4random_uniform(3));
        NSLog(@"B结束");
        dispatch_group_leave(group2);
        dispatch_group_leave(group1);
    });
    
    dispatch_group_enter(group2);
    dispatch_async(queue, ^{
        NSLog(@"C开始");
        sleep(arc4random_uniform(10));
        NSLog(@"C结束");
        dispatch_group_leave(group2);
    });
    
    dispatch_group_notify(group1, queue, ^{
        NSLog(@"D开始");
        NSLog(@"D结束");
    });
    
    dispatch_group_notify(group2, queue, ^{
        NSLog(@"E开始");
        NSLog(@"E结束");
    });
    
###  第二种思路：利用信号量来完成

	    
    dispatch_semaphore_t a = dispatch_semaphore_create(0);
    dispatch_semaphore_t b = dispatch_semaphore_create(0);
    dispatch_semaphore_t c = dispatch_semaphore_create(0);
    
    dispatch_queue_t queue = dispatch_queue_create("queue", DISPATCH_QUEUE_CONCURRENT);
    
    dispatch_async(queue, ^{
        NSLog(@"A开始");
        sleep(arc4random_uniform(10));
        NSLog(@"A结束");
        dispatch_semaphore_signal(a);
    });
    dispatch_async(queue, ^{
        NSLog(@"B开始");
        sleep(arc4random_uniform(10));
        NSLog(@"B结束");
        dispatch_semaphore_signal(b);
        dispatch_semaphore_signal(b);
    });
    dispatch_async(queue, ^{
        NSLog(@"C开始");
        sleep(arc4random_uniform(10));
        NSLog(@"C结束");
        dispatch_semaphore_signal(c);
    });
    
    
    dispatch_async(queue, ^{
        
        dispatch_semaphore_wait(a, DISPATCH_TIME_FOREVER);
        dispatch_semaphore_wait(b, DISPATCH_TIME_FOREVER);
        NSLog(@"D开始");
        NSLog(@"D结束");
    });
    dispatch_async(queue, ^{
        dispatch_semaphore_wait(b, DISPATCH_TIME_FOREVER);
        dispatch_semaphore_wait(c, DISPATCH_TIME_FOREVER);
        NSLog(@"E开始");
        NSLog(@"E结束");
    });
    
    
  