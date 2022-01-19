# EasyRedis

## 一、使用默认 IOC 注入

### 1. 方式一  系统 IOC 注入：Startup 类 ConfigureServices 方法中添加以下代码
````
services.AddTransient<RedisStringService>();
services.AddTransient<RedisListService>();
services.AddTransient<RedisHashService>();
services.AddTransient<RedisSetService>();
services.AddTransient<RedisZSetService>();

RedisConfigInfo.ReadServerList = "192.168.220.132:6379";
RedisConfigInfo.WriteServerList = "192.168.220.132:6379";
````

### 2. 方式二  Autofac 注入 Startup 类 ConfigureContainer 方法中添加以下代码

```
/// <summary>
/// Autofac
/// </summary>
/// <param name="builder"></param>
public void ConfigureContainer(ContainerBuilder builder)
{
    builder.RegisterType<RedisStringService>();
    builder.RegisterType<RedisListService>();
    builder.RegisterType<RedisHashService>();
    builder.RegisterType<RedisSetService>();
    builder.RegisterType<RedisZSetService>();
}

RedisConfigInfo.ReadServerList = "192.168.220.132:6379";
RedisConfigInfo.WriteServerList = "192.168.220.132:6379";
```

