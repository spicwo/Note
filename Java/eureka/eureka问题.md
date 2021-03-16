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

