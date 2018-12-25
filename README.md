# admin-demo

- Admin的[官方文档](https://codecentric.github.io/spring-boot-admin/current/)

# master分支
- Maven聚合项目，两个模块，一个server一个client，所有注册到server应用将被监控
- 访问方式：直接访问server：http://localhost:8811
- 最简单的模式，适用于单机架构

# T01分支
- 使用eureka负责发现，SBA server注册到eureka实现监控，不再依赖和使用SBA client
- 此时其他服务只需要注册到eureka即可，不用依赖SBA client，当然你也可以依赖SBA client并使用它，完全不使用eureka（这就比较逗比了别忘了你玩的是cloud）实现监控
- SBA服务端可以访问客户端的敏感端点，因此手册建议我们应该为它们添加安全配置
- 安全配置只需在server做，但是客户端要对应配置好用户名密码，否则客户端无法注册到SBA server（eureka发现不受影响）
- 加入密码后发现大家多了个配置metadataMap。Eureka 中的 metadataMap 是专门用来存放一些自定义的数据，当注册中心或者其他服务需要此服务的某些配置时可以在 metadataMap 里取。实际上，每个 instance 都有各自的 metadataMap，map 中存放着需要用到的属性。
- 另外，你会发现，eureka不带metadataMap（用户名密码）也能注册上去，脸白的一匹
- 还能玩的更花，通知：当已注册到SBA server的client发生某些事件的时候，可以收到通知，比如使用email实现