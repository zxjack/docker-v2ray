# docker-v2ray-aria2-nextcloud  

利用docker-compose一键搭建v2ray-ws-tls,增加了aria2和nextcloud，这样就可以一键搞定所有的事情了。  

- 注意修改：

v2ray中  

```bash
    environment:
          - VIRTUAL_HOST=域名
          - VIRTUAL_PORT=端口
```

nextcloud中  

```bash
    container_name: 域名
    expose:
          - "80"
    environment:
          - VIRTUAL_HOST=域名
          - VIRTUAL_PORT=80
          - LETSENCRYPT_HOST=域名
          - LETSENCRYPT_EMAIL=邮箱地址

```  

- v2ray设置  

v2ray 设置文件config.json在 dockec-compose.yml 下创建 v2ray 文件件，
新建文件 config.json
port 注意与 v2ray 设置一致
id 改为你的id，可以使用 uuidgenerator 生成一个。
json 写完之后，注意校对格式哦

- TLS转发设置  
  
转发在 dockec-compose.yml 下创建 vhost.d 文件件，
新建文件 You_Domain_Name_location
使用你的域名替换 You_Domain_Name，要与 web1 设置的一致。
注意 proxy_pass 后的端口与 v2ray 设置的一致。  

```bash
proxy_redirect off;
proxy_http_version 1.1;
proxy_set_header Upgrade $http_upgrade;
proxy_set_header Connection "upgrade";
proxy_set_header Host $http_host;
if ($http_upgrade = "websocket" ) {
proxy_pass http://v2ray:****;
}
```
