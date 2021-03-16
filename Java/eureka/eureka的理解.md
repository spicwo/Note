eureka分为注册中心和服务发现，其中注册中心在创建的时候服务端也会将自己注册到注册中心上去，所以需要在配置文件中添加`register-with-eureka：false`,这样就不会

##### 为什么需要服务发现

Nginx 作为反向代理服务器，负载均衡服务器，服务端发现

客户端发现：eureka

服务端发现：nginx、zookeeper、kubernetes
