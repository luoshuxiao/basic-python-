# 一 .socket套接字：实现通信过程的两个端，等待请求的一个端是服务器套接字，发送请求的一端是客户端套接字，python中有一个socket模块来支持编程
## a:服务器套接字（最小系统）：
### 1.创建套接字对象： 对象= socket.socket（family,type）

family : 设置ip地址（默认值AF_INEF,AF_INEF6:IPV6）

type  ：设置传输协议类型（默认值SOCK_STREAM--TCP类型，SOCK_DGRAM--UDP类型）

		import socket
		server= socket.socket()
### 2.绑定ip地址和端口： 对象.bind（ip,端口）
ip --  服务器对应的计算机的ip地址，字符串类型

端口号 --  用来区分计算机上不同的服务；

端口号要求：是一个范围在【0-65535】的数字，其中1024以下的是著名端口，用来表示特殊服务（一般不用），同一时间一个端口只能对应一个服务

		server.bind(('10.7.187.61',8080))

### 3.开始监听：对象.listen（最大监听数) --用来设置当前服务器一次可以处理多少个请求 

		server.listen(100)

### 4.让服务器一直处于开启状态：while死循环

		while Ture:
### 5.接受客户端发送的请求，返回请求地址和建立会话
注意：这段代码会阻塞线程（程序运行到这会停下，知道有哭护短给当前服务器发送请求为止）

    		conersation,address = server.accept()
### 6.接收客户端发送的消息：conversation.recv(缓存大小)
  recv(缓存大小) -- 获取客户端发送的数据（二进制）

  阻塞线程，知道客户端发送了消息才会接着往后执行

    		re_data = conversation.recv(1024)
### 7.向客户端数据发送： send(数据) -- 将指定的数据发送给客户端（二进制）

字符串转二进制： bytes(字符串，'utf-8') 或者 字符串.encode('utf-8')

二进制转字符串： str(二进制，'utf-8') 或者 二进制.decode（'utf-8'） 

		    massage = input('向客户端发送数据：')
		    conversation.send(massage.encode(encoding='utf-8')) 
### 8.关闭连接  close()   
            conversation.close() 
## b.客户端套接字（最小系统）

### 1.创建套接字对象：  socket.socket()
    client = socket.socket()
### 2.连接服务器：  对象.connect((ip,端口))
    client.connect(('10.7.187.61',8080))
### 3.发送消息
	while True:
	   n = input('请说：')
	   client.send(n.encode('utf-8'))
### 4.接收消息
  	   re_data = client.recv(1024)
# 二.远程数据网络请求：python中做http请求，需要使用一个叫requests的第三方库
## 1.请求数据： requests.get（url）返回数据对象
### a.手动拼接url
			# 拼接地址
		url = 'https://www.apiopen.top/satinApi?type=1&page=1'
            # 获取数据：字符串
		respones = requests.get(url)
		print(respones)    #  <Response [200]>
### b.函数调用自动拼接（推荐使用）
       	    # 地址
		url = 'https://www.apiopen.top/satinApi'
            # 获取数据：字符串
		respones = requests.get(url，{'type':1,'page':1})
		print(respones)    #  <Response [200]>
## 2.获取响应头：对象.headers，返回值为响应头对象
        header = respones.headers
        print(header)      # 对服务器的描述、对返回数据的描述（没有数据）
## 3.获取响应体：对象.content，返回值为响应体数据对象
#### a.  cont = respones.content  获取二进制格式的响应体
#### b.  cont = respones.json()  获取json格式的响应体(自动将数据转换成python格式)   
#### c.  cont = respones.text  获取字符串格式的响应体     

####  练习：下载一个网络图片
		url = 'http://wimg.spriteapp.cn/picture/2018/0922/1e7656b4be8011e8923d842b2b4c75ab_wpd.jpg'
		res = requests.get(url)
		image_data = res.content
		with open('龙哥是董事长.jpg','wb') as f:
		    f.write(image_data)

#### 练习：接收图片，不断接收数据，直到接收完为止
		# 创建一个空的二进制数据
		data = bytes()
		while True:
		    re_data = client.recv(1024)
		    data += re_data
		    print('接收到数据!')
		    if not re_data:
		        break