## HTTPS 请求

### 在一个HTTPS连接的网站里，输入账号密码点击登录后，到服务器返回这个请求前，中间经历了什么



![](http://upload-images.jianshu.io/upload_images/852671-93a593fc347c4035.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


服务器 用`RSA`生成公钥和私钥
把公钥放在证书里发送给客户端，私钥自己保存
客户端首先向一个权威的服务器检查证书的合法性，如果证书合法，客户端产生一段随机数，这个随机数就作为通信的密钥，我们称之为对称密钥，用公钥加密这段随机数，然后发送到服务器

服务器用密钥解密获取对称密钥，然后，双方就已对称密钥进行加密解密通信了


### 参考

[啦啦啦](http://blog.csdn.net/clh604/article/details/22179907)

