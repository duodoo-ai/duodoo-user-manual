#### 匠石之齐，至于曲辕，见栎社树。其大蔽数千牛，絜之百围，其高临山十仞而后有枝，其可以为舟者旁十数。观者如市，匠伯不顾，遂行不辍。  
-- 《庄子・人间世》
---
配置文件：
[options]
; 强制使用数据库会话存储
; 使用文件会话存储（因为我们现在自定义了数据库存储）
session_store = file
session_type = file
session_storage = db

; 确保基础模块正确加载
init = base,web

; 会话超时设置（秒）
session_timeout = 86400  ; 24小时

admin_passwd = 1234qwer
addons_path = /home/jason/app/odoo18/src/addons, /home/jason/app/odoo18/src/odoo/addons, duodoo-tekr-flexo

db_host = 127.0.0.1
db_name = false
db_password = 1234qwer    ; 1234qwer
db_port = 5432
db_user = odoo
data_dir = /home/jason/app/runtime/odoo18_cert
dbfilter=flexo_pipeline ; 重点的重点，只加载指定的数据库，其他的数据库加载会导致接口报错

; 启用调试模式
debug_mode = True

xmlrpc_port = 3000
cors_origins = *  # 明确指定允许的源
csrf_origin_check = False   ; 禁用 CSRF 保护（仅对 API 路由）

limit_memory_hard = 12000000000
limit_memory_soft = 12000000000
limit_request = 8192
limit_time_real = 99999

;创建新数据库时使⽤的数据库模板
db_template = template0

temp_path = /home/jason/app/runtime/temp_path
attachment_path = /home/jason/app/runtime/attachment_path
wkhtmltopdf_path = /usr/bin/wkhtmltopdf

auth_admin_passkey_password = admin@098iop

; 日志配置 - 合并所有 log_handler 到一行
log_level = debug
log_handler = :DEBUG,oak_project:DEBUG,oak_core:DEBUG
; logfile = /home/jason/app/odoo18/log/odoo-server.log
; logrotate = True



geoip_city_db = False
geoip_country_db = False
geoip_proxy_db = False
geoip_database_path = /usr/share/GeoIP


