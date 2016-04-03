##  啥是HTTP？
* 超文本传输协议（`HTTP，HyperText Transfer Protocol`)是互联网上应用最为广泛的一种网络协议。所有的`WWW`文件都必须遵守这个标准
* 规定了客户端和服务器之间的数据传输格式

## HTTP缺点：
* **通信使用明文（未加密的报文），内容可能会被窃听：**即使是加密处理的通信，也会被窥视到通信内容，这点和未加密的通信是一样的。只是说如果通信经过加密，就有可能让人无法破解报文信息的含义，但加密处理后的报文信息本身还是会被看到的。（例如抓包工具）
	![窃听](http://upload-images.jianshu.io/upload_images/852671-3122fcb882f1bbbc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* **不验证通信方的身份就可能遭遇伪装：**HTTP协议的实现本身非常简单，不论是谁发来的请求都会返回响应。但是通过SSL可以查明对手的证书。（伪造证书是一件异常困难的事情）
![来者不拒](http://upload-images.jianshu.io/upload_images/852671-bd4f047f6b0816bc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* **无法证明报文的完整性，可能已被篡改：**虽然HTTP有MD5等校验算法，但是MD5本身也可能被修改，这样的话，用户完全察觉不到。为了防止弊端，有必要使用HTTPS。

![无法判断](http://upload-images.jianshu.io/upload_images/852671-3b8608b3c08c4059.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* **HTTP＋加密＋认证＋完整性保护＝HTTPS**

## 为什么不一直使用HTTPS

* 加密通信会消耗更多的CPU和内存资源
* 加密证书购买的成本。

现在大多非敏感信息使用HTTP通信，包含个人信息的敏感数据，才会利用HTTPS加密通信。

## HTTP的优点
* 速度快，效率高：如果使用加密，必然密集使用CPU，那么就会拖慢处理速度

## [GET与POST的区别](http://www.w3school.com.cn/tags/html_ref_httpmethods.asp)
* GET - 从指定的资源请求数据。
* POST - 向指定的资源提交要被处理的数据

------------------------------------------
* GET使用URL传参数，而POST将数据都放在BODY中
* 基于服务器安全性和稳定性考虑，会对URL的长度进行限制。所以就有了以下说法：GET请求因为URL长度的限制，所以对URL的大小进行了限制，而POST请求，数据都在BODY中，可以随意选择数据的大小。
* POST比GET更安全一点点：GET的URL带有参数，并且会被放在浏览器历史和服务器日志中，只要被偷窥了信息应该就会被他人获取，而POST，日志没有记录，只要数据库服务器不被入侵，基本还是安全的。（当然被抓了包，二者都不行）
* 幂等的说法，对于GET，同一个URL我们多次请求的数据是一样的，也方便大家进行转发和书签；而POST多用于敏感数据表单的提交，刷新之后就需要重新输入。
