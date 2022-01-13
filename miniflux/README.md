# miniflux
## Introduction
Miniflux is a minimalist and opinionated feed reader.

[Website](https://miniflux.app/)
[GitHub](https://github.com/miniflux/v2.git)

### Configuring the environment
[docker-compose configuration](. /docker-compose/readme.md)

## Using the tutorial
    [services][ports]:
        - 897:8080
    The host will pair port 897 to docker's port 8080. In general, docker's port cannot be changed arbitrarily.

    The entry in [services][miniflux][environment] is an environment variable
    The format is 
     - $environment variable name=$environment variable content

    [postgres][environment]
    The environment variable is configured with the database username password, be sure to generate your own high strength password.
    And change it in [services][miniflux][environment][DATABASE_URL]

Official environment variables list: [link](https://miniflux.app/miniflux.1.html)

## Recommended environment variable configuration
|variable name|description|
|-----|-----|
|POLLING_FREQUENCY|Refresh feed interval, (minutes)|
|CLEANUP_ARCHIVE_UNREAD_DAYS|Clear unread articles, -1 not clear, (days)|
|CLEANUP_ARCHIVE_READ_DAYS=-1|clears read articles, -1 does not clear, (days)|
|BASE_URL|The base URL used to generate the HTML link and the base path to the cookie. (but not just add the domain name here, only the display effect) |

## Add a custom domain name
### nginx
```
server {
    server_name $YOUR_DOMAIN_WITHOUT_HTTP(S);
    listen 80;

    location / {
        proxy_pass http://127.0.0.1:897; # 897 here can be set to a custom host port in the environment variable.
        proxy_redirect off;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

### Pagoda
1. create a static website
2. Set up -> reverse proxy -> add the following image
![image.png](https://s2.loli.net/2022/01/13/KV7AP6FtlLvOMfj.png)
3. restart nginx

Translated with www.DeepL.com/Translator (free version)
