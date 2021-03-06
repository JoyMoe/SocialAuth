百度登录
===

安装
===

```posh
Install-Package JoyMoe.AspNetCore.Authentication.Baidu
```

使用
===

### Startup.cs

```c#
public void ConfigureServices(IServiceCollection services)
{
    services.AddAuthentication()
            .AddBaidu(baiduOptions =>
            {
                baiduOptions.Appkey = Configuration["Authentication:Baidu:Appkey"];
                baiduOptions.SecretKey = Configuration["Authentication:Baidu:SecretKey"];
            })
}
```

| Claim Name                | Descript |
| ------------------------- | -------- |
| ClaimTypes.NameIdentifier | 用户UID    |
| ClaimTypes.Name           | 登录的用户名   |
| urn:baidu:portrait        | 用户头像     |
|                           |          |

### 用户头像

Claim头像值只是portrait，必须将它转换为绝对URL.

- small image: http://tb.himg.baidu.com/sys/portraitn/item/{$portrait} 

- large image: http://tb.himg.baidu.com/sys/portrait/item/{$portrait}
