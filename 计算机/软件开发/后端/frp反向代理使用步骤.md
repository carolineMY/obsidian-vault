
"D:\frp_0.43.0_windows_amd64\frpc.ini"

1、更改frpc.ini文件

[common]
server_addr = 139.224.115.132
server_port = 7000
privilege_token = wisevirtue.com

[mall]
type = http
local_port = 7575  // 更改成前端本地要代理的启动项目端口
custom_domains = mall.deyanflow.com // 最终使用的访问地址

2、启动
frpc -c frpc.ini