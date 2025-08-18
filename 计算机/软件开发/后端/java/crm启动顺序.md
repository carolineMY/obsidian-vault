1、启动nacos
- 双击nacos/bin/new_statup.bat启动
- 复制路径192.168.108:8848
- 登录 nacos wisevirtue.Com

2、修改bootstrap.yml nacos 服务注册地址
  - server-addr: ${NACOS_HOST:127.0.0.1}:${NACOS_PORT:8848}
  - 涉及模块：crm-auth、crm-gateway、crm-modules-system、crm-modules-flowable、crm-modules-crm

3、依次启动crm-gateway、crm-auth、其他模块