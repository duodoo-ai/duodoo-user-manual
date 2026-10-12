【开发笔记】Ubuntu 24.04 + Odoo 18 + Vue 前后端分离访问（结构示例）

> 以下为**脱敏示例**：密码、本机路径、生产库名请按部署环境替换，**勿将真实凭据提交公开仓库**。

---

#### 技术支持：zou.jason@qq.com · 微信 duodoo2018 · https://www.duodoo.tech

---

配置文件片段 `[options]`：

```ini
session_store = file
session_type = file
session_timeout = 86400

admin_passwd = <管理员主密码，部署时设置>
addons_path = <odoo_addons路径>, <自定义模块路径>

db_host = 127.0.0.1
db_name = false
db_password = <数据库密码>
db_port = 5432
db_user = odoo
data_dir = <filestore目录>
dbfilter = <仅加载的目标库名>

xmlrpc_port = 3000
cors_origins = *
csrf_origin_check = False

limit_memory_hard = 12000000000
limit_memory_soft = 12000000000
limit_request = 8192
limit_time_real = 99999

db_template = template0
temp_path = <临时目录>
attachment_path = <附件目录>
wkhtmltopdf_path = /usr/bin/wkhtmltopdf

log_level = info
```

说明：`dbfilter` 仅加载指定库，避免多库环境下接口路由异常。调试项（如 `debug_mode`）生产环境请关闭。
