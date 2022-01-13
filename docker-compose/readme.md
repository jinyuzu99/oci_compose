## Install docker environment
```bash
curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
```

## Installing the docker-compose environment
[official documentation](https://docs.docker.com/compose/install/)


## Easy to use tutorial
[Official Documentation](https://docs.docker.com/compose/)
|Commands|Instructions|
|docker-compose up
|docker-compose up| based on the current docker-compose in the same level directory. yaml or yml file foreground start|
|docker-compose up -d|Based on the docker-compose. yaml or yml file in the current sibling directory to start in the background|
|docker-compose down|deletes existing dockers and docker networks based on the docker-compose. yaml or yml file in the current sibling directory|

## Caution
1. docker service does not start automatically after reboot by default.
```bash
systemctl enable docker
```
![image.png](https://s2.loli.net/2022/01/13/ORdB1P6IkXaliUp.png)

If that doesn't work, then you'll need to write the startup script by hand

Translated with www.DeepL.com/Translator (free version)
