# 第2节：HTTP概述
## http协议
HyperText Transfer Protocol, 超文本传输协议
## https
Hypertext Transfer Protocol over Secure Socket Layer
HTTP下加入SSL层，HTTPS的安全基础是SSL，HTTPS的安全基础是SSL，因此加密的详细内容就需要SSL。
## 区别
* HTTPS存在不同于HTTP的默认端口及一个加密/身份验证层（在HTTP与TCP之间）
* HTTPS广泛用于万维网上安全敏感的通讯，例如交易支付方面
* HTTP端口号：80；HTTPS端口号：443
## 客户端HTTP请求（带上请求头，证明）
先请求DNS服务器，把ip地址请求到，才能知道请求的是哪台电脑
还要带上一些请求头
1. 请求报头(客户端带一些信息给服务器)
* Host（主机和端口号）
	http://118.190.150.35:9000/login
* Connect（链接类型）：keep alive 长连接，不需要每次都去请求
* User-Agent（浏览器名称）
	使用fake_useragent包
		from fake_useragent import UserAgent
        
        ua = UserAgent()      # 实例化出来
        headers={
        "User-Agent" :ua.random
        }
        
* Accept（接收传输文件类型）
    ```
	*/* 什么都可以接收
    image/gif 希望接收GIF图像格式的资源
    text/html 表明客户端希望接收html
    text/html,application/xhtml+xml;q=9,image/*;q=0.8
    支持html文本、xhtml和xml文档、所有的图像格式资源，q为权重(0<=q<=1)默认为1（规定分号前面的内容），越靠近1表示越希望";"之前的内容，为0 不希望的类型
    ```
* Referer（页面跳转处）
	表明产生请求的网页来自于哪个URL
* Accept-Encoding（浏览器接受文件编码格式）
* Accept-Language（浏览器接受语言种类）
* Accept-Charset（浏览器可接受字符编码）
* Cookie（浏览器本地Application中）
* Content-Type（POST请求中数据的数据类型）
2. 响应报头
* Cache-Control：must-revalidate，no-cache，private
	服务器不希望客户端缓存资源，下次必须重新请求
    Cache-Control：max-age=86400
    在86400秒的时间内，客户端可以从缓存中读取资源
* Connection：keep-alive
	告诉客户端服务器的tcp连接也是一个长连接，客户端可以继续使用这个tcp链接发送http请求
* Content-Encodeing：gzip
	告诉客户端服务端发送的资源时采用gzip编码的
* Content-Type：text/html;charset=UTF-8
	告诉客户端资源文件类型还有字符编码
* Date：Sun，21 Sep
	服务器发送资源时间
* Expires:Sun...
	告诉客户端在这个时间内，可以直接访问缓存副本
* Pragma：no-cache与Cache-Control
* Server 服务器信息
* Transfer-Encoding:chunked
	告诉客户端，服务器发送的资源的方式是分块发送的
* Vary：Accept--Encoding
	告诉缓存服务器，缓存压缩文件还是非压缩文件
* 响应状态码
	* 100~199  服务器成功接收部分请求，需要客户端继续提交其余请求
	* 200~299  服务器成功接收请求并已完成整个处理过程
    * 200  请求成功
	* 300~399  为完成请求，客户需要进一步细化请求
    * 307  304   使用缓存资源
	* 400~499 客户端请求有错误
    * 404  无法找到页面
    * 403  服务器拒绝访问
	* 500~599  服务器端出现错误
    * 500  请求未完成

