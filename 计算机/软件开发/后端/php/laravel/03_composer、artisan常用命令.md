
## **1、Composer常用命令**
### **基础命令**
```bash
composer install          # 安装依赖
composer update          # 更新依赖
composer require package  # 安装新包
composer remove package   # 删除包
composer dump-autoload   # 重新生成自动加载
```

### **开发命令**
```bash
composer install --dev    # 安装开发依赖
composer update --no-dev  # 更新生产依赖
composer show package     # 查看包信息
composer outdated         # 检查过期包
```

## **2、Artisan常用命令**
### **开发命令**
```bash
php artisan serve         # 启动开发服务器
php artisan make:controller NameController  # 创建控制器
php artisan make:model ModelName            # 创建模型
php artisan make:migration create_table_name # 创建迁移
php artisan make:middleware MiddlewareName  # 创建中间件
```
### **数据库命令**
```bash
php artisan migrate       # 执行迁移
php artisan migrate:rollback  # 回滚迁移
php artisan migrate:refresh   # 重置数据库
php artisan db:seed       # 执行数据填充
php artisan migrate:fresh --seed  # 重置并填充数据
```

### **缓存命令**
```bash
php artisan cache:clear   # 清除缓存
php artisan config:clear  # 清除配置缓存
php artisan route:clear   # 清除路由缓存
php artisan view:clear    # 清除视图缓存
php artisan optimize      # 优化应用
```

### **应用命令**
```bash
php artisan key:generate  # 生成应用密钥
php artisan jwt:secret    # 生成JWT密钥
php artisan storage:link  # 创建存储链接
php artisan list          # 查看所有命令
php artisan help command  # 查看命令帮助
```

## **3、常用组合命令**

### **重置开发环境**
```bash
composer install
php artisan migrate:fresh --seed
php artisan cache:clear
php artisan serve
```

### **快速调试**
```bash
php artisan cache:clear
php artisan config:clear
php artisan route:clear
```

### **新项目初始化**
```bash
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate
php artisan storage:link
```

## 💡 **记忆技巧**

### **Composer 命令**
- `install` = 安装
- `update` = 更新
- `require` = 需要
- `dump-autoload` = 重新加载

### **Artisan 命令**
- `make:` = 创建
- `migrate` = 数据库
- `clear` = 清除
- `serve` = 服务

**记住**: Composer 管包，Artisan 管应用！