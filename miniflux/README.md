# miniflux
## 简介
Miniflux is a minimalist and opinionated feed reader.

[官网](https://miniflux.app/)
[GitHub](https://github.com/miniflux/v2.git)

### 配置环境
[docker-compose配置](../docker-compose/readme.md)

## 使用教程
    [services][ports]:
        - 897:8080
    宿主机将897端口对接到docker的8080端口，一般来说，docker的端口不可随意更改。

    [services][miniflux][environment]内条目是环境变量
    格式为 
     - $环境变量名称=$环境变量内容

    [postgres][environment]
    环境变量配置的是数据库用户名密码，务必自行生成高强度密码。
    并在[services][miniflux][environment][DATABASE_URL] 中修改

官方环境变量列表：[链接](https://miniflux.app/miniflux.1.html)

## 推荐的环境变量配置
|变量名|说明|
|-----|-----|
|POLLING_FREQUENCY|刷新feed的间隔时间，（分钟）|
|CLEANUP_ARCHIVE_UNREAD_DAYS|清除未阅读的文章，-1不清除，（天）|
|CLEANUP_ARCHIVE_READ_DAYS=-1|清除已阅读的文章，-1不清除，（天）|
|BASE_URL|用于生成HTML链接的基本URL和cookie的基本路径。（但在这里并不是就这样添加域名，仅有展示效果）|

## 添加自定义域名
### nginx
```
server {
    server_name     $YOUR_DOMAIN_WITHOUT_HTTP(S);
    listen          80;

    location / {
        proxy_pass http://127.0.0.1:897;#这里的897可设置为环境变量中自定义的宿主机端口。
        proxy_redirect off;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

### 宝塔
1. 创建一个静态网站
2. 设置->反向代理->添加如下图所示
![image.png](https://s2.loli.net/2022/01/13/KV7AP6FtlLvOMfj.png)
3. 重启nginx