> HTTP（Hypertext Transfer Protocol）超文本传输协议

http是一个基于“==请求与响应模式==的“，无状态的应用层协议



http采用URL作为定位网络资源的标识，URL格式如下：

```http
http://host[:post][path]
```

 		host：合法的internet主机域名或IP地址

​		port：端口号，缺省80

​		path：请求资源的路径



HTTP URL示例：

```http
http://www.baidu.com
```

URL是通过http协议存取资源的internet路径，一个url对应一个数据资源



http协议对资源的操作：

| 方法   | 说明                                                |
| ------ | --------------------------------------------------- |
| GET    | 请求获取URL位置的资源                               |
| HEAD   | 请求获取url位置资源的响应报告，即头部信息           |
| POST   | 请求向url位置的资源后附加新的数据                   |
| PUT    | 请求向url位置存储一个新的资源，覆盖原url位置的资源  |
| PATCH  | 请求局部更新url位置的资源，即改变该处资源的部分内容 |
| DELETE | 请求删除url位置存储的资源                           |

