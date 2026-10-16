【开发笔记】Ubuntu 24.04+Odoo18+Vue配置前后端分离访问，测试通过！！
---

#### 技术支持：zou.jason@qq.com · 微信 duodoo2018 · https://www.duodoo.tech

---
Vue前端文件权限配置：--用户和组都要配置 用户权限：www-data  用户组权限：www-data
```bash
root@odoo:/var/www/html/dist# ls -l
total 64
drwxr-xr-x 3 www-data www-data  4096 Jul  4 03:22 css
-rw-r--r-- 1 www-data www-data  4286 Jul  4 03:22 favicon.ico
drwxr-xr-x 2 www-data www-data  4096 Jul  4 03:22 fonts
drwxr-xr-x 2 www-data www-data  4096 Jul  4 03:22 img
-rw-r--r-- 1 www-data www-data  3964 Jul  4 03:22 index.html
drwxr-xr-x 2 www-data www-data  4096 Jul  4 03:22 js
-rw-r--r-- 1 www-data www-data 34523 Jul  4 03:22 LICENSE
```
Nginx配置文件功能：--按以下文件顺序配置，确保配置生效。
**文件路径：/etc/nginx/sites-available/default** 
```bash
server {
    listen 3000;
    server_name 60.172.152.100;  #todo 替换为你的服务器 IP 或域名
    
    # Vue 应用构建文件的根目录
    root /var/www/html/dist;  #todo 确保这是你的 Vue 应用的实际路径
    index index.html;
    
    # ====================== 后端服务代理 - 优先处理 ======================
    # 修复根目录访问问题
    location = / {
        try_files /index.html =404;
    }
    
    # 1. 长轮询服务专用代理 (8072端口) - 最高优先级
    location /longpolling {
        proxy_pass http://127.0.0.1:8072;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_read_timeout 3600s;
        proxy_send_timeout 3600s;
        proxy_connect_timeout 3600s;
    }
    
    # 2. Odoo 后端核心代理 (8069端口) - 包含所有可能的后端路径
    location ~ ^/(api|auth|login|odoo|web|mail|im|websocket|session|jsonrpc|web/image|logo\.png) {
        proxy_pass http://127.0.0.1:8069;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        
        # 会话保持关键配置 (解决登录状态丢失问题)
        proxy_cookie_path / /;
        proxy_cookie_domain ~^(?<domain>.+)$ $domain;
        
        # 修复 WebSocket 超时问题
        proxy_connect_timeout 7d;
        proxy_send_timeout 7d;
        proxy_read_timeout 7d;
    }

    # 3. Odoo 静态资源代理 - 单独处理
    location /web/static/ {
        proxy_pass http://127.0.0.1:8069;
        proxy_cache_valid 200 302 12h;
        proxy_cache_valid 404 1m;
        expires 1y;
        add_header Cache-Control "public";
    }

    # ====================== 前端资源优化 ======================
    # 静态图片目录专用处理 (使用 ^~ 提升优先级)
    location ^~ /img/ {
        alias /var/www/html/dist/img/;
        expires 1y;
        add_header Cache-Control "public, immutable";
        access_log off;
        
        # 详细调试信息
        add_header X-Img-Path "Alias: $request_filename";
    }

    # Vue 静态资源缓存优化 (图片等资源已经被上面的 /img/ 处理，这里主要处理其他静态资源)
    location ~* \.(js|css|gif|ico|svg|woff2)$ {
        root /var/www/html/dist;
        expires 1y;
        add_header Cache-Control "public, immutable";
        try_files $uri =404;
        
        # 详细调试信息
        add_header X-Static-Path "Root: $request_filename";
    }
    
    # ====================== 前端路由处理 - 兜底 ======================
    location / {
        try_files $uri $uri/ /index.html;
    }
    
    # ====================== 错误处理 ======================
    error_page 404 /404.html;
    location = /404.html {
        internal;
        root /var/www/html/dist;
    }
    
    location ~ /\. {
        deny all;
    }
    
    # ====================== 调试配置 ======================
    # 启用详细日志
    access_log /var/log/nginx/debug_access.log;
    error_log /var/log/nginx/debug_error.log debug;
}
```


