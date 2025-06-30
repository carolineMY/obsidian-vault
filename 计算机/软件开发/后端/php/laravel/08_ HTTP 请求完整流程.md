
中间件-路由-控制器-响应
---

## 🚦 1. 浏览器/前端发起请求

比如你访问：
```
GET https://api.xxx.com/api/v3/member/courses
```

---

## 🏁 2. 入口文件（public/index.php）

- 类似前端的 `main.js` 或 `server.js`
- 作用：一切请求都先到这里

```php
require __DIR__ . '/../vendor/autoload.php'; // 加载依赖
$app = require_once __DIR__ . '/../bootstrap/app.php'; // 创建应用实例
$kernel = $app->make(Illuminate\Contracts\Http\Kernel::class); // 获取 HTTP 内核
$response = $kernel->handle($request = Illuminate\Http\Request::capture()); // 处理请求
$response->send(); // 发送响应
$kernel->terminate($request, $response); // 收尾
```

---

## 🏗️ 3. 应用实例和内核（bootstrap/app.php）

- 创建 `$app` 实例，相当于前端的 `createApp()`
- 绑定核心服务（HTTP 内核、异常处理等）

---

## 🧩 4. HTTP 内核（App\Http\Kernel）

- 类似前端的“中间件栈”
- 负责全局中间件（如 CORS、日志、认证等）处理
- 依次执行中间件，像 Express/Koa 的 `app.use()`

---

## 🗺️ 5. 路由分发（RouteServiceProvider）

- 根据 URL 匹配到对应的路由文件（如 routes/frontend-v3.php）
- 路由文件里定义了 URL 和控制器的映射
  ```php
  Route::get('/member/courses', 'MemberController@courses');
  ```

---

## 🧑‍💻 6. 控制器（Controller）

- 路由找到控制器方法（如 `MemberController@courses`）
- 控制器方法里处理业务逻辑，调用 Service 层、Model 层
- 获取数据后，返回响应（通常是 JSON）

---

## 🗃️ 7. 服务层/模型层（Service/Model）

- 控制器调用 Service 层（如 `UserService`），Service 再调 Model（数据库）
- Model 查询数据库，返回数据

---

## 🛡️ 8. 响应处理

- 控制器返回数据（如 `return response()->json([...])`）
- Laravel 自动把数据转成 HTTP 响应

---

## 🚚 9. 响应返回

- `$response->send()` 把响应内容发回前端
- 浏览器/前端收到 JSON 数据

---

## 📝 **流程图（类比前端）**

```
[浏览器请求]
      ↓
[public/index.php]   // (main.js/server.js)
      ↓
[bootstrap/app.php]  // (createApp/init)
      ↓
[App\Http\Kernel]    // (中间件栈)
      ↓
[RouteServiceProvider] // (路由分发)
      ↓
[Controller]         // (控制器/路由处理函数)
      ↓
[Service/Model]      // (业务逻辑/数据库)
      ↓
[返回响应]           // (res.json()/res.send())
      ↓
[前端收到数据]
```

---

## 💡 **前端类比总结**

| Laravel 步骤           | 前端类比                | 作用                      |
|------------------------|-------------------------|---------------------------|
| public/index.php       | main.js/server.js       | 应用入口                  |
| bootstrap/app.php      | createApp/init          | 创建应用实例              |
| App\Http\Kernel        | app.use() 中间件栈      | 全局中间件处理            |
| RouteServiceProvider   | 路由分发                | URL 匹配到处理函数        |
| Controller            | 路由处理函数/Controller | 业务逻辑                  |
| Service/Model         | Service/Model/DB        | 数据处理/数据库           |
| response()->json()    | res.json()/res.send()   | 返回响应                  |

---

## 🚀 **一句话总结**

> Laravel service-api 的请求流程就像前端的 Koa/Express 服务端：入口 → 中间件 → 路由 → 控制器 → 服务/数据库 → 返回响应！

这样你就能用前端思维快速理解 Laravel 的请求全流程啦！