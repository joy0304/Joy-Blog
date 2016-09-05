## Tips

### 复杂表达式

当你有一个复杂的 `if `子句的时候，你应该把它们提取出来赋给一个 `BOOL` 变量，这样可以让逻辑更清楚，而且让每个子句的意义体现出来

	BOOL nameContainsSwift  = [sessionName containsString:@"Swift"];
	BOOL isCurrentYear      = [sessionDateCompontents year] == 2014;
	BOOL isSwiftSession     = nameContainsSwift && isCurrentYear;
	
	if (isSwiftSession) {
	    // Do something very cool
	}
### 命名

**类名:**

类名应该以三个大写字母作为前缀（双字母前缀为 `Apple` 的类预留）。尽管这个规范看起来有些古怪，但是这样做可以减少 `Objective-c` 没有命名空间所带来的问题。

另一个好的类的命名规范：当你创建一个子类的时候，你应该把说明性的部分放在前缀和父类名的在中间。

举个例子：如果你有一个 `ZOCNetworkClient` 类，子类的名字会是`ZOCTwitterNetworkClient` (注意 "`Twitter`" 在 "`ZOC`" 和 "`NetworkClient`" 之间); 按照这个约定， 一个`UIViewController` 的子类会是 `ZOCTimelineViewController`.

**推荐使用长的、描述性的方法和变量名**

	// 推荐:
	UIButton *settingsButton;
	
	// 不推荐:
	UIButton *setBut;

**常量**

应该以驼峰法命名，并以相关类名作为前缀。

	static const NSTimeInterval ZOCSignInViewControllerFadeOutAnimationDuration = 0.4;
	
推荐使用常量来代替字符串字面值和数字，这样能够方便复用，而且可以快速修改而不需要查找和替换。常量应该用 `static` 声明为静态常量，而不要用 `#define`，除非它明确的作为一个宏来使用。

	推荐：
	static const CGFloat ZOCImageThumbnailHeight = 50.0f;
	
	不推荐:
	#define CompanyName @"Apple Inc."
	#define magicNumber 42
	
### Property

默认情况下一个可读写属性，会获得实例变量的支持，这个是由编译器生成的。默认情况下，实例变量的名字是属性名字前面加上下划线

	
	@property(readonly) NSString *name;
	
	// 那么实例变量的名字是 _name
	
同时自己可以自定义生成的实例变量的名字

	@synthesize name = firstName;

那么现在就可以通过 `firstName` 来进行访问

如果使用`@synthesize` 关键字的时候，不去指明实例变量的名字
 
 	@synthesize name;
 那么实例变量的命名就会和属性一致，没有下滑线，也就是`name`
 
 可以不通过属性来定义实例变量，可以将实例变量声明在类接口和实现的大括号内
 
	@interface ViewController : UIViewController{
	    NSString *martinAge;
	}	
	@end


 	@implementation ViewController{
   		 NSString *martinName;
	}
 	@end
 	
 
###  KVC	 	

对于` “setValue:属性值 forKey@"name”`代码，底层逻辑是怎样的？

1. 程序首先考虑调用`"setName:属性值"`代码通过`setter`方法完成设置
2. 如果该类没有`setter`方法，那么`KVC`机制就会去寻找该类中名为`_name`的成员变量，对`_name`实例变量赋值
3. 如果没有`setter`方法、`_name`实例变量，那么`KVC`机制会搜索该类中名为`name`的成员属性，对`name`成员变量赋值
4. 如果都没有找到，则会执行该对象的`setValue:forUnDefinedKey：`方法

对于`“valueforKey@”name“;”`代码，底层执行机制是怎么样的？

1. 程序首先调用`name`来获取该`getter`方法的返回值
2. 如果该类没有`name`方法，那么`KVC`机制会搜索该类中名为`_name`的成员变量
3. 如果以上都没有，那么`KVC`开始搜索名为`name`的成员变量
4. 如果上面都没有找到，则系统将会执行该对象的`valueForUndefinedKey:`方法


### 属性特性
属性特性的顺序应该是`storage`、`atomicity`，与在`Interface Builder`连接`UI`元素时自动生成代码一致

	@property (weak, nonatomic) IBOutlet UIView *containerView;  
	@property (copy, nonatomic) NSString *tutorialName;

### 常量
常量是容易重复被使用和无需通过查找和代替就能快速修改值。常量应该使用`static`来声明而不是使用`#define`，除非显式地使用宏。

### 布尔值
`Objective-C`使用`YES`和`NO`。因为`true`和`false`应该只在`CoreFoundation`，`C`或`C++`代码使用。既然`nil`解析成`NO`，所以没有必要在条件语句比较。不要拿某样东西直接与`YES`比较，因为`YES`被定义为`1`和一个`BOOL`能被设置为`8`位。

这是为了在不同文件保持一致性和在视觉上更加简洁而考虑。

应该：

	if (someObject) {}  
	if (![anotherObject boolValue]) {}  
不应该：
	
	if (someObject == nil) {}  
	if ([anotherObject boolValue] == NO) {}  
	if (isAwesome == YES) {} // Never do this.  
	if (isAwesome == true) {} // Never do this.  
	
### instancetype 与 id
可以简单理解：`intancetype`就是本类，`id`是指向任意对象的指针

`instancetype`只能用来表示方法的返回值，但是`id`还可以表示变量和方法参数，如果一个程序运行时无法确定一个对象的类型，就可以将该对象声明为`id`

###  初始化方法

初始化方法的命名模式：以英文`init`开头

	- (instancetype)initWithItemName:(NSString *)name;
	- (instancetype)initWithItemoName:(NSString *)name
						   valueInDollars:(int)value;
						   
指定初始化方法

其他初始化方法，不需要再把指定初始化方法的代码搬过来了，只需要调用指定初始化方法即可

初始化方法的若干规则：

* 类会继承父类所有的初始化方法，也可以为类加入任意数量的初始化方法
* 每个类都要选定一个指定初始化方法
* 在执行其他初始化工作之前，必须先用指定初始化方法调用父类的指定初始化方法
* 其他初始化方法要调用指定初始化方法

### NSArray 与 NSMutableArray

数组对象只能保存指向 oc 对象的指针，所以不能将基本类型的变量加入数组对象，可以将其包装成 oc 对象后， 再放入数组

不能将`nil`放入数组，可以使用`NSull`对象代替`nil`

	[array addobject:[NSNull null]];

### 属性的内存管理特性

	@property (nonatomic, copy) NSString *itemName;

改用`copy`特性后，`itemName`属性的存方法可能类似于以下代码：
	
	- (void)setItemName:(NSString *)itemName{
		_itemName = [itemName copy];
	}
这么做的原因是：如果属性指向的对象的类有可修改的子类，那么该属性可能会指向可修改的子类对象，同时，该对象可能会被其他拥有者修改，因此，最好先复制该对象，然后再将属性指向复制后的对象

