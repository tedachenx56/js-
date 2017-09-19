浏览器 三次握手 域名解析 后台 数据库 返回 判断 解压缩 处理数据

## HttpXMLRequest

|属性|参数|描述|
|---|---|---|
|readyState|0 1 2 3 4 |0 代表未初始化 1 代表准备发送 2 已发送但还没收到响应 3 正在接收 4 接收完成|
|responseText|string|包含客户端接收到的HTTP响应的文本内容。当readyState=4时，responseText才包含完整的响应信息。当readyState=3时，responseText包含未完整的响应信息。当readyState<3时，responseText为空字符串。|
|responseXML|DOM|当readyState=4,并且响应头部的Content-Type的MIME类型为XML(text/xml或application/xml)时,该属性有值并且被解析成一个XML文档。其它情况为null,包括回传的XML文档不良或未完成响应回传。|
|status|http status|当readyState>2,才能访问，否则出现异常。服务器返回的http状态码。200表示“成功”，404表示“未找到”，500表示“服务器内部错误”等。|
|statusText|describe status|服务器返回状态的文本信息。|

|方法|参数|描述|
|---|---|---|
|onreadystatechange|/|当readyState属性发生变化时触发此事件，用于触发回调函数。|
|open|method(*), uri, async, username, password|用来进行初始化工作 返回值：得到一个包含send()方法的对象 method：必须。用于指定HTTP方法如GET,POST,PUT....。按规定必须大写。 uri：请求发送到服务器相应的URI.自动解析成绝对地址。 async：请求是否异步，默认为true. 调用open后，readystate状态为1。|
|send|null/buffer/dom|向服务器发出请求，如果采用异步方式，该方法会立即返回。content可以指定为null表示不发送数据，其内容可以是DOM对象，输入流或字符串。|
|abort|/|该方法可以暂停一个HttpRequest请求或者HttpResponse的接收，并且将XMLHttpRequest的状态设置为初始化。|
|setRequestHeader|string:header,string:value|该方法用来设置请求的头部信息。在调用open()后调用这个方法。否则将得到一个异常。|
|getResponseHeader|string:header|当readystate>2时，该方法用来检索响应的头部信息。否则返回一个空字符串。 返回值是一个字符串，包含所有头信息，其中每个键名和键值用冒号分开，每一组键之间用CR和LF（回车加换行符）来分隔！| 
|getAllResponseHeader|/|当readystate>2时，该方法用来返回所有的HttpResponse头部信息,否则返回一个空字符串。 返回值是一个字符串，包含所有头信息，其中每个键名和键值用冒号分开，每一组键之间用CR和LF（回车加换行符）来分隔！| 


## ajax

同步ajax会被警告，所以能不用就不用吧, 对于一些有同步需求(比如先后顺序执行)的, 可以用promise来实现。

GET /Servlet/servlet/Servlet_03 HTTP/1.1
Accept: application/x-ms-application, image/jpeg, application/xaml+xml, image/gif, image/pjpeg, application/x-ms-xbap, application/x-shockwave-flash, */*
Accept-Language: zh-CN
User-Agent: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.1; WOW64; Trident/5.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; .NET4.0C; .NET4.0E)
Accept-Encoding: gzip, deflate
Host: localhost:8080
Connection: Keep-Alive

getRequestURL方法返回客户端发出请求时的完整URL。
getRequestURI方法返回请求行中的资源名部分。
getQueryString 方法返回请求行中的参数部分。
getRemoteAddr方法返回发出请求的客户机的IP地址
getRemoteHost方法返回发出请求的客户机的完整主机名
getRemotePort方法返回客户机所使用的网络端口号
getLocalAddr方法返回WEB服务器的IP地址。
getLocalName方法返回WEB服务器的主机名



##
hasownpropertyof

##
 href是Hypertext Reference的缩写，表示超文本引用。用来建立当前元素和文档之间的链接。常用的有：link、a。


## HTTP 协议 

目前我们使用的是HTTP/1.1 版本
### 网页访问过程
当我们打开浏览器，在地址栏中输入URL，然后我们就看到了网页。 原理是怎样的呢？

实际上我们输入URL后，我们的浏览器给Web服务器发送了一个Request, Web服务器接到Request后进行处理，生成相应的Response，然后发送给浏览器， 浏览器解析Response中的HTML,这样我们就看到了网页。

### url解析过程

URL详解
URL(Uniform Resource Locator) 地址用于描述一个网络上的资源,  基本格式如下

schema://host[:port#]/path/.../[?query-string][#anchor]
scheme               指定低层使用的协议(例如：http, https, ftp)
host                 HTTP服务器的IP地址或者域名
port#                HTTP服务器的默认端口是80，这种情况下端口号可以省略。如果使用了别的端口，必须指明，例如 http://www.cnblogs.com:8080/
path                访问资源的路径
query-string        发送给http服务器的数据(get请求)
anchor-             锚

#### hash`#`

`#`代表网页中的一个位置。其右面的字符，就是该位置的标识符。比如，http://www.example.com/index.html#print就代表网页index.html的print位置。浏览器读取这个URL后，会自动将print位置滚动至可视区域。
为网页位置指定标识符，有两个方法。一是使用锚点，比如`<a name="print"></a>`，二是使用id属性，比如`<div id="print">`。

是用来指导浏览器动作的，对服务器端完全无用。所以，HTTP请求中不包括#。在第一个#后面出现的任何字符，都会被浏览器解读为位置标识符。这意味着，这些字符都不会被发送到服务器端。

单单改变#后的部分，浏览器只会滚动到相应位置，不会重新加载网页。每一次改变#后的部分，都会在浏览器的访问历史中增加一个记录，使用"后退"按钮，就可以回到上一个位置。这对于ajax应用程序特别有用，可以用不同的#值，表示不同的访问状态，然后向用户给出可以访问某个状态的链接。值得注意的是，上述规则对IE 6和IE 7不成立，它们不会因为#的改变而增加历史记录。

SEO Google抓取#的机制
默认情况下，Google的网络蜘蛛忽视URL的#部分。
但是，Google还规定，如果你希望Ajax生成的内容被浏览引擎读取，那么URL中可以使用"#!"，Google会自动将其后面的内容转成查询字符串_escaped_fragment_的值。
比如，Google发现新版twitter的URL：http://twitter.com/#!/username
就会自动抓取另一个URL：http://twitter.com/?_escaped_fragment_=/username
通过这种机制，Google就可以索引动态的Ajax内容。

window.location.hash 可读可写；读取时，可以用来判断网页状态是否改变。写入时，则会在**不重载**网页的前提下，创造一条访问历史记录。
事件 onhashchange ie8+

#### ?
1.连接作用
2.视为新页面不触发缓存
#### &
不同参数的间隔符

### HTTP状态
1.http协议是无状态的，同一个客户端的这次请求和上次请求是没有对应关系，对http服务器来说，它并不知道这两个请求来自同一个客户端。 为了解决这个问题， Web程序引入了Cookie机制来维护状态。

point:无状态是指协议对于事务处理没有记忆能力，服务器不知道客户端是什么状态。从另一方面讲，打开一个服务器上的网页和你之前打开这个服务器上的网页之间没有任何联系。HTTP是一个无状态的面向连接的协议，无状态不代表HTTP不能保持TCP连接，更不能代表HTTP使用的是UDP协议（无连接）。

从HTTP/1.1起，默认都开启了Keep-Alive，保持连接特性，简单地说，当一个网页打开完成后，客户端和服务器之间用于传输HTTP数据的TCP连接不会关闭，如果客户端再次访问这个服务器上的网页，会继续使用这一条已经建立的连接。
Keep-Alive不会永久保持连接，它有一个保持时间，可以在不同的服务器软件（如Apache）中设定这个时间
### Request 结构
先看Request 消息的结构,   Request 消息分为3部分，第一部分叫Request line, 第二部分叫Request header, 第三部分是body. header和body之间有个空行， 

Method /Path-to-resource HTTP/version-num
Header-Name-1:Value1
Header-Name-2:Value2
Header-Name-3:Value3

Optional request body
___
GET /Servlet/servlet/Servlet_03 HTTP/1.1
Accept: application/x-ms-application, image/jpeg, application/xaml+xml, image/gif, image/pjpeg, application/x-ms-xbap, application/x-shockwave-flash, */*
Accept-Language: zh-CN
User-Agent: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.1; WOW64; Trident/5.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; .NET4.0C; .NET4.0E)
Accept-Encoding: gzip, deflate
Host: localhost:8080
Connection: Keep-Alive
___
Method表示请求方法,比如"POST","GET",  Path-to-resoure表示请求的资源， Http/version-number
当使用的是"GET" 方法的时候， body是为空的

我们再看Response消息的结构, 和Request消息的结构基本一样。 同样也分为三部分,第一部分叫Response line, 第二部分叫Response header，第三部分是body. header和body之间也有个空行

HTTP/version-num status code message
Header-Name-1:Value1
Header-Name-2:Value2
Header-Name-3:Value3

Optional request body
___
HTTP/version-number表示HTTP协议的版本号，  status-code 和message 状态码和描述。

### GET POST 区别
GET, POST, PUT, DELETE就对应着对这个资源的查，改，增，删4个操作。
GET一般用于获取/查询资源信息，而POST一般用于更新资源信息。

数据存放位置 大小 加密（安全性）获取方式
1. GET提交的数据会放在URL之后，以?分割URL和传输数据，参数之间以&相连，如EditPosts.aspx?name=test1&id=123456。  POST方法是把提交的数据放在HTTP包的Body中。
2. GET提交的数据大小有限制（因为浏览器对URL的长度有限制），而POST方法提交的数据没有限制.
3. GET方式需要使用Request.QueryString来取得变量的值，而POST方式通过Request.Form来获取变量的值。
4. GET方式提交数据，会带来安全问题，比如一个登录页面，通过GET方式提交数据时，用户名和密码将出现在URL上，如果页面可以被缓存或者其他人可以访问这台机器，就可以从历史记录获得该用户的账号和密码.

### 常见状态码

HTTP/1.1中定义了5类状态码， 状态码由三位数字组成，第一个数字定义了响应的类别

|方法|描述|
|---|--|
|1XX|提示信息 - 表示请求已被成功接收，继续处理|
|2XX|成功 - 表示请求已被成功接收，理解，接受|
|3XX|重定向 - 要完成请求必须进行更进一步的处理|
|4XX|客户端错误 -  请求有语法错误或请求无法实现|
|5XX|服务器端错误 -   服务器未能实现合法的请求|

|方法|描述|
|---|--|
|200 OK 成功|这表明该请求被成功地完成，所请求的资源发送回客户端|
|302 Found 重定向|新的URL会在response 中的Location中返回，浏览器将会自动使用新的URL发出新的Request|
|304 Not Modified 已有缓存|代表上次的文档已经被缓存了， 还可以继续使用，|
|400 Bad Request 错误的请求|客户端请求与语法错误，不能被服务器所理解|
|403 Forbidden 禁止|服务器收到请求，但是拒绝提供服务|
|404 Not Found 未找到服务器|请求资源不存在（输错了URL）|
|500 Internal Server Error 服务器错误|服务器发生了不可预期的错误|
|503 Server Unavailable 服务器不能访问|服务器当前不能处理客户端的请求，一段时间后可能恢复正常|

point:如果你不想使用本地缓存可以用Ctrl+F5 强制刷新页面

### Request Header
Accept:text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
Accept-Encoding:gzip, deflate, br
Accept-Language:zh-CN,zh;q=0.8,zh-TW;q=0.6
Connection:keep-alive
Cookie:BAIDUID=3014269A446AB284235DC6E6EBE15A96:FG=1; BIDUPSID=3014269A446AB284235DC6E6EBE15A96; PSTM=1489813118; BDUSS=zlpbEJJMUlRZ1BiaDhDb1hOSUV4Qn5KSUgzUlJEZVE5UERTQXpJY0Z-V1VoNEZaSVFBQUFBJCQAAAAAAAAAAAEAAADEFDAD9~a1rcPOyOe56QAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAJT6WVmU-llZd; BDSFRCVID=QEPsJeCCxG39su7Z6GFMaWtt-0fxDnb-2-It3J; H_BDCLCKID_SF=JJkO_D_atKvjDbTnMITHh-F-5fIX5-RLf23LB-OF5lOTJh0ReqnYXpIWK-6wKtQ9WjFLM56F5ncUOqojDTbke6JQjN8qq6Ds2jLX0JjV-bOoKROvhjRj2xAyyxomtjjxbI_eKnOubMTAqC5M3h34M60NKMT2LUkqKCOzhDt52JIM_pOGjMQJb-AkQttjQUThfIkja-KE3nOfJR7TyU42hf47yboqQTIqtb4q_KL2fb5Sejrzbjnqh-Lm5qOLybJyb6r20C6tKRTfftJnK-r_24k0-fIsWM5J-2Q-5hOy3K8BqPK6Wxb0M5JbhUJzJPnhMgnX3jC-HlTMhpFuj6-2j6bBjaR-2PLXaCIS0RRHX-5MDf7RhnoK-PQK-xQ0KnQjK5R0WtcSbRj_bUjH0bbkbftd2-teqRJtJaLqKhQzKx3Mf5CxbR7Uh4jDDmcA-TJZfD7H3KCbJIKaMx5; pgv_pvi=7761719296; pgv_si=s8421696512; PSINO=1; H_PS_PSSID=1469_22533_21094_22073; BDORZ=B490B5EBF6F3CD402E515D22BCDA1598; Hm_lvt_55b574651fcae74b0a9f1cf9c8d7c93a=1504075890,1504150439,1504163046,1504165164; Hm_lpvt_55b574651fcae74b0a9f1cf9c8d7c93a=1504165164
Host:baike.baidu.com
Referer:https://baike.baidu.com/item/URI/2901761?fr=aladdin
Upgrade-Insecure-Requests:1
User-Agent:Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36
___
####简略版：
常见mime信息
##### application/x-www-form-urlencoded
原生表单post形式请求 常用ajax post请求（jquery ajax post）

	POST http://www.example.com HTTP/1.1
	Content-Type: application/x-www-form-urlencoded;charset=utf-8
	 
	title=test&sub%5B%5D=1&sub%5B%5D=2&sub%5B%5D=3
___
##### application/json
序列化后的json 数据传输(AngularJS Ajax) 层次可以很深

	POST http://www.example.com HTTP/1.1
	Content-Type: application/json;charset=utf-8
	 
	{"title":"test","sub":[1,2,3]}
___
##### text/xml 
XML-RPC（XML Remote Procedure Call） 简单易用的数据传输

	POST http://www.example.com HTTP/1.1
	Content-Type: text/xml
 
	<?xml version="1.0"?>
	<methodCall>
	    <methodName>examples.getStateName</methodName>
	    <params>
	        <param>
	            <value><i4>41</i4></value>
	        </param>
	    </params>
	</methodCall>
___
##### multipart/form-data
POST 数据提交的方式。我们使用表单上传文件的请求 上传文件

	POST http://www.example.com HTTP/1.1
	Content-Type:multipart/form-data; boundary=----WebKitFormBoundaryrGKCBY7qhFd3TrwA
	 
	------WebKitFormBoundaryrGKCBY7qhFd3TrwA
	Content-Disposition: form-data; name="text"
	 
	title
	------WebKitFormBoundaryrGKCBY7qhFd3TrwA
	Content-Disposition: form-data; name="file"; filename="chrome.png"
	Content-Type: image/png
	 
	PNG ... content of chrome.png ...
	------WebKitFormBoundaryrGKCBY7qhFd3TrwA--
首先生成了一个 boundary 用于分割不同的字段，为了避免与正文内容重复，boundary 很长很复杂。然后 Content-Type 里指明了数据是以 mutipart/form-data 来编码，本次请求的 boundary 是什么内容。消息主体里按照字段个数又分为多个结构类似的部分，每部分都是以 –boundary 开始，紧接着内容描述信息，然后是回车，最后是字段具体内容（文本或二进制）。如果传输的是文件，还要包含文件名和文件类型信息。消息主体最后以 –boundary– 标示结束。关于 mutipart/form-data 的详细定义，请前往 rfc1867 查看。

这种方式一般用来上传文件，各大服务端语言对它也有着良好的支持。
___
|方法|描述|
|--|--|
|If-Modified-Since|缓存页面的最后修改时间|
|If-None-Match|（浏览器）可接收的压缩方式|
|Pragma|防止页面被缓存|
|Cache-Control|这个用来指定Response-Request遵循的缓存机制。|
|Accept|（浏览器）可接收的数据类型|
|Accept-Encoding|（浏览器）可接收的压缩方式|
|Accept-Language|（浏览器）可接收的语言|
|Accept-Charset |（浏览器）可接收的字符集|
|User-Agent|使用者代理 使用者告诉HTTP服务器， 客户端使用的操作系统和浏览器的名称和版本。|
|Cookie|将cookie的值发送给HTTP 服务器|
|Content-Length|发送给HTTP服务器数据的长度。|
|Content-Type|发送给HTTP服务器数据的类型。（mime Multipurpose Internet Mail Extensions）|
|Referer|提供了Request的上下文信息的服务器，告诉服务器我是从哪个链接过来的，比如从我主页上链接到一个朋友那里，他的服务器就能够从HTTP Referer中统计出每天有多少用户点击我主页上的链接访问他的网站。|
|Connection|客户端和服务器之间用于传输HTTP数据的TCP连接状态，一般是Connection: keep-alive|
|Host|被请求资源的Internet主机和端口号，它通常从HTTP URL中提取出来的。|
___
#### Cache 头域 缓存
##### If-Modified-Since
作用： 把浏览器端缓存页面的最后修改时间发送到服务器去，服务器会把这个时间与服务器上实际文件的最后修改时间进行对比。如果时间一致，那么返回304，客户端就直接使用本地缓存文件。如果时间不一致，就会返回200和新的文件内容。客户端接到之后，会丢弃旧文件，把新文件缓存起来，并显示在浏览器中.
例如：If-Modified-Since: Thu, 09 Feb 2012 09:07:57 GMT
实例如下图
##### If-None-Match
作用: If-None-Match和ETag一起工作，工作原理是在HTTP Response中添加ETag信息。 当用户再次请求该资源时，将在HTTP Request 中加入If-None-Match信息(ETag的值)。如果服务器验证资源的ETag没有改变（该资源没有更新），将返回一个304状态告诉客户端使用本地缓存文件。否则将返回200状态和新的资源和Etag.  使用这样的机制将提高网站的性能
例如: If-None-Match: "03f2b33c0bfcc1:0"
##### Pragma
作用： 防止页面被缓存， 在HTTP/1.1版本中，它和Cache-Control:no-cache作用一模一样
Pargma只有一个用法， 例如： Pragma: no-cache
注意: 在HTTP/1.0版本中，只实现了Pragema:no-cache, 没有实现Cache-Control
##### Cache-Control
作用: 这个是非常重要的规则。 这个用来指定Response-Request遵循的缓存机制。各个指令含义如下
Cache-Control:Public   可以被任何缓存所缓存（）
Cache-Control:Private     内容只缓存到私有缓存中
Cache-Control:no-cache  所有内容都不会被缓存
还有其他的一些用法， 我没搞懂其中的意思， 请大家参考其他的资料
####Client 头域 客户端
##### Accept
作用： 浏览器端可以接受的媒体类型,
例如：  Accept: text/html  代表浏览器可以接受服务器回发的类型为 text/html  也就是我们常说的html文档,
如果服务器无法返回text/html类型的数据,服务器应该返回一个406错误(non acceptable)
通配符 * 代表任意类型
例如  Accept: */*  代表浏览器可以处理所有类型,(一般浏览器发给服务器都是发这个)
##### Accept-Encoding：
作用： 浏览器申明自己接收的编码方法，通常指定压缩方法，是否支持压缩，支持什么压缩方法（gzip，deflate），（注意：这不是只字符编码）;
例如： Accept-Encoding: gzip, deflate
##### Accept-Language
作用： 浏览器申明自己接收的语言。 
语言跟字符集的区别：中文是语言，中文有多种字符集，比如big5，gb2312，gbk等等；
例如： Accept-Language: en-us
##### User-Agent
作用：告诉HTTP服务器， 客户端使用的操作系统和浏览器的名称和版本.
我们上网登陆论坛的时候，往往会看到一些欢迎信息，其中列出了你的操作系统的名称和版本，你所使用的浏览器的名称和版本，这往往让很多人感到很神奇，实际上，服务器应用程序就是从User-Agent这个请求报头域中获取到这些信息User-Agent请求报头域允许客户端将它的操作系统、浏览器和其它属性告诉服务器。
例如： User-Agent: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 5.1; Trident/4.0; CIBA; .NET CLR 2.0.50727; .NET CLR 3.0.4506.2152; .NET CLR 3.5.30729; .NET4.0C; InfoPath.2; .NET4.0E)
##### Accept-Charset
作用：浏览器申明自己接收的字符集，这就是本文前面介绍的各种字符集和字符编码，如gb2312，utf-8（通常我们说Charset包括了相应的字符编码方案）；
#### Cookie/Login 头域 cookie/login
The term "cookie" was coined by web browser programmer Lou Montulli. It was derived from the term "magic cookie", which is a packet of data a program receives and sends back unchanged, used by Unix programmers. Magic cookie in turn derives from "fortune cookie", a cookie with an embedded message.[citation needed]
##### Cookie:
作用： 最重要的header, 将cookie的值发送给HTTP 服务器
#### Entity头域 实体
##### Content-Length
作用：发送给HTTP服务器数据的长度。
例如： Content-Length: 38
##### Content-Type
作用：为了支持多媒体数据类型，HTTP协议中就使用了附加在文档之前的MIME数据类型信息来标识数据类型。
例如：Content-Type: application/x-www-form-urlencoded

|主类型|常见属性|参数含义|
|--|--|--|
|text|charset|文本信息所使用的字符集|
|image|name|图像的名称|
|application|name|应用程序的名称|
|multipart|boundary|邮件分段边界标识|

#### Miscellaneous 头域 多种多样的
##### Referer:
作用： 提供了Request的上下文信息的服务器，告诉服务器我是从哪个链接过来的，比如从我主页上链接到一个朋友那里，他的服务器就能够从HTTP Referer中统计出每天有多少用户点击我主页上的链接访问他的网站。
例如: Referer:http://translate.google.cn/?hl=zh-cn&tab=wT
#### Transport 头域 传输
##### Connection
例如：　Connection: keep-alive   当一个网页打开完成后，客户端和服务器之间用于传输HTTP数据的TCP连接不会关闭，如果客户端再次访问这个服务器上的网页，会继续使用这一条已经建立的连接
例如：  Connection: close  代表一个Request完成后，客户端和服务器之间用于传输HTTP数据的TCP连接会关闭， 当客户端再次发送Request，需要重新建立TCP连接。
##### Host（发送请求时，该报头域是必需的）
作用: 请求报头域主要用于指定被请求资源的Internet主机和端口号，它通常从HTTP URL中提取出来的
例如: 我们在浏览器中输入：http://www.guet.edu.cn/index.html
浏览器发送的请求消息中，就会包含Host请求报头域，如下：
Host：http://www.guet.edu.cn
此处使用缺省端口号80，若指定了端口号，则变成：Host：指定端口号
### Response Header
Bdpagetype:3
Bdqid:0xc78274740000513a
Bduserid:53482692
Connection:Keep-Alive
Content-Encoding:gzip
Content-Length:78
Content-Type:text/html; charset=utf-8
Date:Fri, 01 Sep 2017 02:25:21 GMT
Is_status:1
Server:BWS/1.1
Set-Cookie:PSINO=1; domain=.baidu.com; path=/
Set-Cookie:BDSVRTM=185; path=/
Set-Cookie:H_PS_PSSID=1469_22533_21094_22073; path=/; domain=.baidu.com
Set-Cookie:BD_CK_SAM=1;path=/
Strict-Transport-Security:max-age=172800
Vary:Accept-Encoding
X-Powered-By:HPHP
X-Ua-Compatible:IE=Edge,chrome=1
___
#### 
#### Cache头域
##### Date
作用:  生成消息的具体时间和日期
例如：　Date: Sat, 11 Feb 2012 11:35:14 GMT 
##### Expires
作用: 浏览器会在指定过期时间内使用本地缓存
例如: Expires: Tue, 08 Feb 2022 11:35:14 GMT
##### Vary
作用：
例如: Vary: Accept-Encoding
#### Cookie/Login 头域
##### P3P
作用: 用于跨域设置Cookie, 这样可以解决iframe跨域访问cookie的问题
例如: P3P: CP=CURa ADMa DEVa PSAo PSDo OUR BUS UNI PUR INT DEM STA PRE COM NAV OTC NOI DSP COR
##### Set-Cookie
作用： 非常重要的header, 用于把cookie 发送到客户端浏览器， 每一个写入cookie都会生成一个Set-Cookie.
例如: Set-Cookie: sc=4c31523a; path=/; domain=.acookie.taobao.com
#### Entity头域
##### ETag
作用:  和If-None-Match 配合使用。 （实例请看上节中If-None-Match的实例）
例如: ETag: "03f2b33c0bfcc1:0"
##### Last-Modified:
作用： 用于指示资源的最后修改日期和时间。（实例请看上节的If-Modified-Since的实例）
例如: Last-Modified: Wed, 21 Dec 2011 09:09:10 GMT
##### Content-Type
作用：WEB服务器告诉浏览器自己响应的对象的类型和字符集,
例如:
Content-Type: text/html; charset=utf-8
Content-Type:text/html;charset=GB2312
Content-Type: image/jpeg
##### Content-Length
指明实体正文的长度，以字节方式存储的十进制数字来表示。在数据下行的过程中，Content-Length的方式要预先在服务器中缓存所有数据，然后所有数据再一股脑儿地发给客户端。
例如: Content-Length: 19847
##### Content-Encoding
WEB服务器表明自己使用了什么压缩方法（gzip，deflate）压缩响应中的对象。
例如：Content-Encoding：gzip
##### Content-Language
作用： WEB服务器告诉浏览器自己响应的对象的语言者
例如： Content-Language:da
#### Miscellaneous 头域
##### Server:
作用：指明HTTP服务器的软件信息
例如:Server: Microsoft-IIS/7.5
##### X-AspNet-Version:
作用：如果网站是用ASP.NET开发的，这个header用来表示ASP.NET的版本
例如: X-AspNet-Version: 4.0.30319
X-Powered-By:
作用：表示网站是用什么技术开发的
例如： X-Powered-By: ASP.NET
##### Transport头域
#### Connection
例如：　Connection: keep-alive   当一个网页打开完成后，客户端和服务器之间用于传输HTTP数据的TCP连接不会关闭，如果客户端再次访问这个服务器上的网页，会继续使用这一条已经建立的连接
例如：  Connection: close  代表一个Request完成后，客户端和服务器之间用于传输HTTP数据的TCP连接会关闭， 当客户端再次发送Request，需要重新建立TCP连接。
#### Location头域
##### Location
作用： 用于重定向一个新的位置, 包含新的URL地址
 实例请看304状态实例

### CORs 简单请求
app.all('*', function(req, res, next) {  
    res.header("Access-Control-Allow-Origin", "*"); //请求时Origin字段的值(域名)
    res.header("Access-Control-Allow-Headers", "X-Requested-With");  
    res.header("Access-Control-Allow-Methods","PUT,POST,GET,DELETE,OPTIONS");  //允许方法
    res.header("X-Powered-By",' 3.2.1')  
    res.header("Content-Type", "application/json;charset=utf-8");  //mime
    next();  
});  

### 页面间传值
cookie\sessionstorage get请求对URL进行字符串拼接

## js执行机制
js是单线程 == 同步 
为了避免阻塞 引入异步 另一个线程 管理异步任务
主线程完成任务 查询异步任务 异步任务符合条件 加入主线程
主线程完成任务 插队

setTimeout	在异步队列里创建一个函数，时间到了，符合条件。可以在时间后输入参数
setInterval	在异步队列里创建一个函数，每当时间到了，符合条件。

try{} catch(error){} error{}



ES6诞生以前，异步编程的方法，大概有如下四种：回调函数、事件监听、发布/订阅、Promise对象；ES6中，引入了Generator函数；ES7中，async更是将异步编程带入了一个全新的阶段。

异步任务必须指定回调函数，当主线程开始执行异步任务，就是执行对应的回调函数。


建立主线程 判断引入异步 符合条件 主线程完成 异步的回调函数进入主线线程。
Prpromiseomise > setImmediate > setTimeout(0)

### promise

    var promise = new Promise(function(resolve, reject) {
    		// ... some code
    		if( /* 异步操作成功 */ ) {
    			resolve(value);
    		} else {
    			reject(error);
    		}
    });

|方法|参数|描述|
|---|---|---|
|then|/|原型方法|
|catch|/|原型方法|
|all|flex-start flex-end center space-between space-around|父极 副轴 行距|
|race|row row-reverse column column-reverse|父极 主轴方向|
|resolve|nowrap wrap wrap-reverse|父极 换行 不换行 换行 向副轴反方向换行|
|reject|/|父极主轴方向 换行|
|try|flex-start flex-end center space-between space-around|提案|
|done|number 默认0|附加方法|
|finally|number 默认0|附加方法|

### callback
callback 函数是一种以参数形式传递给另一个函数的函数。
如果您的网站上存在多个 AJAX 任务，那么您应该为创建 XMLHttpRequest 对象编写一个标准的函数，并为每个 AJAX 任务调用该函数。
该函数调用应该包含 URL 以及发生 onreadystatechange 事件时执行的任务（每次调用可能不尽相同）：
	


## 对象

### 工厂模式

	function createPerson(name){
		var o=new Object;
		o.name=name
		o.getname=function(){
			return this.name
		}
	}
### 构造函数
	function Person(name){
		this.name=name;
		this.getname=function(){
			return this.name
		}
	}
### 原型
	function Person(){;}
	person.prototype={
		this.name="name";
		this.getname=function(){
			return this.name
		}
	}
### 构造函数 和 原型的结合
	function Person(){
		this.name=name;
	}
	person.prototype={
		this.getname=function(){
			return this.name;
		}
	}

## this
### 箭头函数 ()=>{}
箭头函数中的 this 确实和调用时的上下文无关 
怎么理解
实际上箭头函数中并不只是 this 和普通函数有所不同，箭头函数中没有任何像 this 这样自动绑定的局部变量，包括：this，arguments，super(ES6)，new.target(ES6)……
优点 适合函数式编程

point: 需要使用arguments 可使用展开运算符 ...
### call&&applay
1、方法定义
call方法: 
语法：call([thisObj[,arg1[, arg2[,   [,.argN]]]]]) 
定义：调用一个对象的一个方法，以另一个对象替换当前对象。 
说明： 
call 方法可以用来代替另一个对象调用一个方法。call 方法可将一个函数的对象上下文从初始的上下文改变为由 thisObj 指定的新对象。 
如果没有提供 thisObj 参数，那么 Global 对象被用作 thisObj。 

apply方法： 
语法：apply([thisObj[,argArray]]) 
定义：应用某一对象的一个方法，用另一个对象替换当前对象。 
说明： 
如果 argArray 不是一个有效的数组或者不是 arguments 对象，那么将导致一个 TypeError。 
如果没有提供 argArray 和 thisObj 任何一个参数，那么 Global 对象将被用作 thisObj， 并且无法被传递任何参数。