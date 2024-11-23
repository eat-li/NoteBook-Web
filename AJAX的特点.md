## AJAX的特点

### AJAX的优点

1. 可以无需刷新页面于服务端进行通行



### AJAX的缺点

1. 没有浏览历史
2. 存在跨域问题
3. SEO不友好

## HTTP协议

HTTP协议——超文本传输协议，详细规定了浏览器和万维网服务器之间的互相通信的规则

###  请求报文

重点是格式和参数

```js
行	1 请求类型 POST GET 2 路径 /	3 HTTP/1.1 
头	HOST:at guigu.com
	Cookie: name = guigu
	Content-type: application/x-www-from-urlencoded
	User-Agent: chrom 83
空行 
体	username=admin&password=admin
```

### 响应报文

~~~html
行	HTTP/1.1 200（表示ok） OK
头	Content-Type: text/html;charset=utf-8
	 Content-lenght: 2048
	 Content-encoding:gzip

空行
体	<html>
    	<head>
            <body>
                <h1>
                    你好
                </h1>
            </body>
    	</head>
    </html>
~~~

* 404
* 403
* 401
* 500
* 200


## URL地址

- 通信协议
- 服务器名称
- 资源具体存放位置



## 客户端和服务器的通信过程

1. 客户端请求服务器
2. 服务器处理请求
3. 服务器相应客户端






