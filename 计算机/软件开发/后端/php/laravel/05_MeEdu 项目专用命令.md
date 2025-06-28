
### **安装命令**
```bash
php artisan install role      # 安装角色数据
php artisan install config    # 安装配置数据
php artisan install administrator  # 安装管理员
php artisan install:lock      # 生成安装锁
```

### **插件命令**
```bash
php artisan addons:install    # 安装插件
php artisan addons:uninstall  # 卸载插件
php artisan addons:list       # 查看插件列表
```

## �� **开发流程命令**

### **新功能开发**
```bash
# 1. 创建模型和迁移
php artisan make:model Course -m

# 2. 编辑迁移文件后执行
php artisan migrate

# 3. 创建控制器
php artisan make:controller CourseController

# 4. 创建服务类
php artisan make:service CourseService
```

### **部署前准备**
```bash
# 1. 清除所有缓存
php artisan cache:clear
php artisan config:clear
php artisan route:clear
php artisan view:clear

# 2. 重新生成缓存
php artisan config:cache
php artisan route:cache
php artisan view:cache

# 3. 优化应用
php artisan optimize
```
