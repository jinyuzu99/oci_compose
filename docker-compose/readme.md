## 安装docker环境
```bash
curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
```

## 安装docker-compose 环境
[官方文档](https://docs.docker.com/compose/install/)


## 简易使用教程
[官方文档](https://docs.docker.com/compose/)
|命令|说明|
|---|---|
|docker-compose up|根据当前同级目录下的docker-compose。yaml或者yml文件前台启动|
|docker-compose up -d|根据当前同级目录下的docker-compose。yaml或者yml文件后台启动|
|docker-compose down|根据当前同级目录下的docker-compose。yaml或者yml文件删除已有的docker与docker网络|

## 注意事项
1. docker服务默认不在重启后自动启动，
```bash
systemctl enable docker
```
![image.png](https://s2.loli.net/2022/01/13/ORdB1P6IkXaliUp.png)

如果无法使用，那就需要手写启动脚本了