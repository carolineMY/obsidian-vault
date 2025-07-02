`config/app.php` 是 Laravel 框架的**核心配置文件**，它的加载时机和机制如下：

---

## 1. **加载时机**

- **Laravel 应用启动的最早阶段**就会加载 `config/app.php`。
- 具体是在**服务容器初始化**和**配置仓库（ConfigRepository）注册**时，由 `Illuminate\Foundation\Application` 类自动加载。

---

## 2. **加载流程**

1. **入口文件**：`public/index.php`
   - 创建应用实例：`$app = require_once __DIR__.'/../bootstrap/app.php';`

2. **bootstrap/app.php**
   - 实例化 `Illuminate\Foundation\Application`。
   - 注册基础绑定（包括配置仓库）。

3. **配置仓库注册**
   - Laravel 会自动加载 `config` 目录下的所有配置文件（包括 `app.php`），并将其内容注册到全局配置仓库中。
   - 这一步发生在 `Illuminate\Foundation\Bootstrap\LoadConfiguration` 这个引导类中。

4. **服务提供者注册**
   - `config/app.php` 中的 `providers` 数组会被读取，自动注册所有服务提供者。

5. **别名注册**
   - `config/app.php` 中的 `aliases` 数组会被读取，自动注册所有类别名。

---

## 3. **作用**

- 提供应用名称、环境、调试、URL、时区、语言、密钥等全局配置。
- 注册所有服务提供者（providers）。
- 注册所有 Facade 别名（aliases）。

---

## 4. **总结**

- `config/app.php` 在**Laravel 应用启动的最初阶段**就会被自动加载。
- 你无需手动引入，Laravel 框架会自动处理。
- 其配置内容会影响整个应用的服务注册、全局参数、别名等。

---

**一句话总结**：  
`config/app.php` 是 Laravel 启动时最早加载的配置文件之一，决定了应用的基础配置和服务注册。