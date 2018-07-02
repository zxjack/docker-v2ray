# docker-v2ray
利用docker-compose一键搭建v2ray-ws-tls
- 注意修改：
v2ray中
```
    environment:
          - VIRTUAL_HOST=域名
          - VIRTUAL_PORT=端口
```          
web1中
```
    container_name: 域名
    expose:
          - "80"
    environment:
          - VIRTUAL_HOST=域名
          - VIRTUAL_PORT=80
          - LETSENCRYPT_HOST=域名
          - LETSENCRYPT_EMAIL=邮箱地址
```

