启动eureka server时出现错误

```
com.sun.jersey.api.client.ClientHandlerException: java.net.ConnectException: Connection refused: connect

com.netflix.discovery.shared.transport.TransportException: Cannot execute request on any known server
```

原因：默认设置下，eureka服务注册中心服务端也是客户端，也需要找到注册中心将自己注册上去，但是作为服务端，我们不需要它注册上去，所以我们需要禁用它的客户端注册行为，在配置文件中设置register-with-eureka: false

启动eureka client时出现错误

```
***************************
APPLICATION FAILED TO START
***************************

Description:

Field optionalArgs in org.springframework.cloud.netflix.eureka.EurekaClientAutoConfiguration$RefreshableEurekaClientConfiguration required a bean of type 'com.netflix.discovery.AbstractDiscoveryClientOptionalArgs' that could not be found.

The injection point has the following annotations:
	- @org.springframework.beans.factory.annotation.Autowired(required=true)

```

原因：是因为没有导入web

解决Feign调用出现URISyntaxException: Illegal character in hostname at index
```
eureka:
  client:
    service-url:
      defaultZone: http://localhost:8080/eureka/
  instance:
    instance-id: ${spring.application.name}:${server.port}
  # 优先使用IP地址方式进行注册服务
    prefer-ip-address: true
  # 配置使用指定IP
    ip-address: 127.0.0.1
```
原因是因为我的主机名中存在下划线，而它是不支持下划线的。

Eureka服务注册是采用主机名还是IP地址？，
