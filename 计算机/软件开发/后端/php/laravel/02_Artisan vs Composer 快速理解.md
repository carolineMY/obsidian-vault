

### **Composer = npm**
```bash
# 包管理
composer install          # npm install
composer require package  # npm install package
composer update          # npm update
```

### **Artisan = npm scripts**
```bash
# 应用命令
php artisan migrate       # npm run migrate
php artisan cache:clear   # npm run clear-cache
php artisan make:controller # npm run create-controller
```

## 🔗 **关系**
1. **Composer** 安装 Laravel 框架
2. **Artisan** 是 Laravel 的命令行工具
3. 先有 Composer，后有 Artisan

## 📝 **常用命令对比**
| 功能 | Composer | Artisan | 前端对应 |
|------|----------|---------|----------|
| 安装依赖 | `composer install` | - | `npm install` |
| 创建文件 | - | `php artisan make:controller` | `npm run create` |
| 数据库 | - | `php artisan migrate` | `npm run db:migrate` |
| 清除缓存 | - | `php artisan cache:clear` | `npm run clear` |

# 前端开发流程
npm install          # 安装依赖
npm run dev          # 启动开发
npm run build        # 构建项目

# Laravel 开发流程
composer install     # 安装依赖
php artisan serve    # 启动开发
php artisan build    # 构建项目（如果有）

## 📝 前端开发理解要点

### 1. 工具层次
- Composer: 包管理器（像 npm）
- Artisan: 应用工具（像 npm scripts）

### 2. 使用场景
- Composer: 管理依赖、安装包
- Artisan: 执行应用命令、管理应用

**记住**: Composer 管包，Artisan 管应用！