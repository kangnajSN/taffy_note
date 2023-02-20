#### 创建全局引用

> &max_size 定义引用名称

> *max_size 使用
```
max_size: &max_size 20MB


# 1000~10000
server:
  port: 9763
  tomcat:
    max-http-form-post-size: *max_size

spring:
  servlet:
    multipart:
      max-request-size: *max_size
      max-file-size: *max_size
```
