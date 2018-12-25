# admin-demo

- Admin的[官方文档](https://codecentric.github.io/spring-boot-admin/current/)

# master分支
- Maven聚合项目，两个模块，一个server一个client，所有注册到server应用将被监控
- 访问方式：直接访问server：http://localhost:8811
- 最简单的模式，适用于单机架构

# T01分支
- 使用eureka负责发现，SBA server注册到eureka实现监控，不再依赖和使用SBA client

