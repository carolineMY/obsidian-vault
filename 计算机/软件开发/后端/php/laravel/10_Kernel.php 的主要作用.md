## 🎯 `app/Http/Kernel.php` 的主要作用

这是 Laravel 应用的**HTTP 内核配置文件**，用来定义全局和路由相关的中间件，以及启动流程。

---

## 1️⃣ **继承自 HttpKernel**

```php
class Kernel extends HttpKernel
```
- 继承自 Laravel 框架的 `HttpKernel`
- 是所有 HTTP 请求的“总管家”

---

## 2️⃣ **启动流程配置（$bootstrappers）**

```php
protected $bootstrappers = [ ... ];
```
- 定义应用启动时要执行的步骤（如加载环境变量、配置、异常处理、服务提供者等）

---

## 3️⃣ **全局中间件（$middleware）**

```php
protected $middleware = [ ... ];
```
- 所有请求都会经过这里定义的中间件
- 例如：代理信任、CORS、维护模式、请求体大小限制、字符串修剪等

---

## 4️⃣ **中间件分组（$middlewareGroups）**

```php
protected $middlewareGroups = [
    'web' => [ ... ],
    'api' => [ ... ],
];
```
- 按照路由类型分组
- `web` 组：会话、CSRF、视图错误等
- `api` 组：限流、路由绑定等

---

## 5️⃣ **路由中间件（$routeMiddleware）**

```php
protected $routeMiddleware = [
    'auth' => ...,
    'throttle' => ...,
    // 还有自定义的
    'backend.permission' => BackendPermissionCheckMiddleware::class,
    'api.login.status.check' => ...,
];
```
- 可以在路由里单独指定
- 例如：`Route::get(...)->middleware('auth')`

---

## 📝 **总结**

- **定义全局中间件**：所有请求都要经过
- **定义分组中间件**：按 web/api 分组
- **定义路由中间件**：可在路由单独指定
- **配置启动流程**：应用启动时的初始化步骤

---

## 💡 **前端类比**

- 就像 Express/Koa 的 `app.use()` 和中间件分组
- 统一管理所有请求的“拦截器”和“前置处理”

---

**记住**：  
`app/Http/Kernel.php` = “全局中间件和启动流程的总配置中心”