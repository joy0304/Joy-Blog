### 介绍

`QYPerformanceMonitor `可以实时监测卡顿，当卡顿发生时，收集各个线程实时的堆栈信息。对于堆栈信息，对外界提供了两种数据

第一种是解析完成的函数信息，如下所示


	Thread 0:
	0     libsystem_kernel.dylib          0x10c84810a __semwait_signal + 94474
	1     libsystem_c.dylib               0x10c5cab0b sleep + 518923
	2     CrashTests                      0x109bbd1cf -[ViewController tableView:cellForRowAtIndexPath:] + 4559
	3     UIKit                           0x10abee4f4 -[UITableView _createPreparedCellForGlobalRow:withIndexPath:willDisplay:] + 1586420
	4     UIKit                           0x10abee62c -[UITableView _createPreparedCellForGlobalRow:willDisplay:] + 1586732
	5     UIKit                           0x10abc2d4f -[UITableView _updateVisibleCellsNow:isRecursive:] + 1408335
	6     UIKit                           0x10abf7686 -[UITableView _performWithCachedTraitCollection:] + 1623686
	7     UIKit                           0x10abde344 -[UITableView layoutSubviews] + 1520452
	
第二种是一些相关的地址信息，方便日后结合 dsym 进行脚本解析

	Thread 0:
	0     libsystem_kernel.dylib          0x10f18d10a 0x10f176000 + 94474
	1     libsystem_c.dylib               0x10ef0fb0b 0x10ee91000 + 518923
	2     CrashTests                      0x10c5021cf 0x10c501000 + 4559
	3     UIKit                           0x10d5334f4 0x10d3b0000 + 1586420
	4     UIKit                           0x10d53362c 0x10d3b0000 + 1586732
	5     UIKit                           0x10d507d4f 0x10d3b0000 + 1408335
	6     UIKit                           0x10d53c686 0x10d3b0000 + 1623686
	7     UIKit                           0x10d523344 0x10d3b0000 + 1520452
	8     UIKit                           0x10d490980 0x10d3b0000 + 919936
	
### 	使用方法

导入头文件`QYPerformanceMonitor.h`，通过`[QYPerformanceMonitor shareInstance]`可以创建一个单例对象

对外提供了这几个接口
	
	- (void)beginMonitor;   // 开始监测
	- (void)endMonitor;     // 停止监测
	- (void)setTheObserverTime:(int64_t)timeValue;           // 传入卡顿的时间间隔， 单位是 ms
	- (void)setEnableSymbolValue:(bool)enableSymbol;         //  总开关，设置是否进行符号解析
	- (NSString *)getBacktraceWithSymbol:(bool)enableSymbol;  // false 的时候获取地址信息， true 获取函数符号信息

* 对于`setEnableSymbolValue`是用于设置是否开启符号解析，一般情况下，不需要开启，后期会通过脚本解析，所以这里为了性能更好，可以设为 `false`，默认即为`false`

* 对于`setTheObserverTime`是用于设置卡顿检测的时间间隔，默认是`100 * 3`，单位是`ms`，可以进行自由设置(您设置数字后，我们会对数值 * 3 来作为卡顿检测的时间，例如设置为100之后，卡顿检测的时间间隔就是300ms)

* 对于`getBacktraceWithSymbol`是用于用户主动投递时，获取最新的一次卡顿信息。`false` 的时候获取地址信息， `true `获取函数符号信息，如果没有开启符号解析，`true`可能获取到 空


如果每次卡顿的时候，都要进行投递，需要使用库中的回调，使用方法如下：

* 首先实现`QYPerformanceMonitorDelegate`中的可选`@optional`方法。实现`handleTheMonitorDataWithSymbol`方法的话获取的就是符号解析后的函数信息，实现`handleTheMonitorData`就是用来获取地址信息
	
		- (void)handleTheMonitorDataWithSymbol:(NSString *)stringData;  // 获取函数符号信息
		- (void)handleTheMonitorData:(NSString *)stringData;            // 获取地址信息

* 提示，记得设置 `delegate` 哦

	    [QYPerformanceMonitor shareInstance].delegate = self;
	    
### 	   使用范例

记得先设置好参数，再开始检测哦

    QYPerformanceMonitor *QYMonitor = [QYPerformanceMonitor shareInstance];
    
    [QYMonitor setTimeObserver:300];
    [QYMonitor setEnableSymbol:false];
    [QYMonitor beginMonitor];
    
= = 
	 
	@interface ViewController ()<QYPerformanceMonitorDelegate>
	
	@end
	
	@implementation ViewController
	
	- (void)viewDidLoad {
	    [super viewDidLoad];
	    
	    [QYPerformanceMonitor shareInstance].delegate = self;
	}
	- (void)handleTheMonitorData:(NSString *)stringData {
	    NSLog(@"%@",stringData);
	}
	- (void)handleTheMonitorDataWithSymbol:(NSString *)stringData {
	    NSLog(@"%@",stringData);
	}



	