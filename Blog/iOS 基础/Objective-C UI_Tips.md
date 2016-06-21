## Objective-C UI Tips


### Frame 单位

	CGRect firstFrame = CGRectMake(100, 200, 100, 200);
	
请注意这些数值的单位是点（`points`）,不是像素（`pixels`）。如果单位是像素，那么视图在`Retina`与非`Retina`显示屏的大小无法保持一致。点的大小与设备的分辨率无关系，取决于以多少像素显示一个点：在`Retina`显示屏上，一个点是两个像素高度，两个像素宽度，非`Retina`显示屏则是一个像素宽度，一个像素高度。为了在不同分辨率的屏幕上看起来一致，都是使用点来作为单位

### 重绘

`UIView`的`setNeedsDisplay`和`setNeedsLayout`方法。首先两个方法都是异步执行的。而`setNeedsDisplay`会调 用自动调用`drawRect`方法，这样可以拿到`UIGraphicsGetCurrentContext`，就可以画画了。而`setNeedsLayout` 会默认调用`layoutSubViews`，就可以处理子视图中的一些数据。

宗上所诉，`setNeedsDisplay`方便绘图，而`layoutSubViews`方便出来数据

### 关于类扩展的属性

在类扩展中声明类的内部属性和方法是良好的编程习惯，这样可以保持头文件的精简，避免过多细节的暴露，保证头文件中全部是其他类确定需要使用的属性和方法，从而让其他开发者更容易理解如何使用该类

	@interface UIViewController()
	
	@property (strong, nonatomic) UIColor *circleColor;
	
	@end

子类同样无法访问在类扩展中声明的属性和方法

### 协议

发送方在发送可选方法之前，会向其委托方发送另一个名为 `respondsToSelector：`的消息。所有` Objective－C `对象都从 `NSObject `继承了 `respondsToSelector：`方法，该方法能在运行时检查对象是否实现了指定方法

	if([self.delegate respondsToSelector:clearSelector]){
	
	}

如果协议方法是必需的，就不需要检查委托对象是否实现了该方法

### How to Use updateConstraints

简单来说.不要将`updateConstraints()`用于视图的初始化设置。当你需要在单个布局流程`（single layout pass）`中添加、修改或删除大量约束的时候，用它来获得最佳性能。如果没有性能问题，直接更新约束更简单。
	
>So when would you need to use updateConstraints? Well, it boils down to performance. If you find that just changing your constraints in place is too slow, then update constraints might be able to help you out. It turns out that changing a constraint inside updateConstraints is actually faster than changing a constraint at other times. The reason for that is because the engine is able to treat all the constraint changes that happen in this pass as a batch.

[How to Use updateConstraints](http://oleb.net/blog/2015/08/how-to-use-updateconstraints/)、[在哪里写Autolayout布局最合适？](http://reviewcode.cn/article.html?reviewId=14)
