## 基本类别
* 1XX：信息性状态码`（informational）`接受的请求正在处理
* 2XX：成功状态码`（success）`请求正常处理完毕
* 3XX：重定向状态码`（redirect）`需要进行附加操作以完成请求
* 4XX：客户端状态码`（Client error）`
* 5XX：服务器状态码`（server error）`

## 2XX成功


#### 204 No Content

服务器接受的请求已正常处理，但是没有资源可返回

#### 206 Partial Content

客户端进行范围请求，响应报文中包含由`Content-Range`指定范围的实体内容

## 3XX 重定向

#### 301 Moved permanently
 
永久性重定向：代表你访问资源的`URI`已经发生了改变，以后应该使用资源新的`URI`了，如果保存了书签，那么`URI`应该从新保存

`URI：`统一资源标识符

`URL：`统一资源定位符


#### 302 Found

临时性重定向：不是永久性的移动，已移动的资源下次还可能移动，`URI`还可能发生改变

#### 303 See other

与`302`类似，当使用`POST`访问资源时，其执行结果是希望客户端采用`GET`方法重定向到另一个`URI`

![](http://upload-images.jianshu.io/upload_images/852671-bba84a15729bb9bf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 304 Not Modified

表示客户端发送附带条件的请求时，服务器允许访问资源，但条件未满足时，`304`状态码返回时，不包含任何响应的主体部分。`304`虽然放在`3XX`中，但是和重定向没什么关系

## 4XX 客户端错误

#### 400 bad request

表示请求中可能存在语法错误，服务器无法理解

#### 401 unauthorized

表示此请求需要有通过`HTTP`认证的认证信息,当浏览器首次接收到`401`后，会弹出认证的对话窗口

#### 403 forbidden

访问没有权限的资源

#### not found

无法找到指定资源

## 5XX 服务器错误

#### 500 Internal Server Error

服务器在执行请求时发生了错误

#### 503 Service Unavilable

表示服务器超负载或者正在停机维修，暂时无法处理请求


