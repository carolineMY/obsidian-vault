
## 1. 为什么 `AddonsProvider` 不写在 `config/app.php` 的 `providers` 里？

- `config/app.php` 的 `providers` 主要用于注册**全局、常驻的服务提供者**，如 Auth、Route、Event 等，保证每次请求都自动加载。
- 插件（Addons）相关的服务提供者通常**不是全局常驻**，而是**按需动态注册**，比如只在插件启用、后台管理、或特定业务场景下才加载。
- 这样做的好处是**灵活、高效**，避免无用插件影响主应用性能。

---

## 2. `AddonsProvider` 的注册方式（详细分析）

- `App\Meedu\AddonsProvider` 不是标准的 Laravel ServiceProvider，而是一个自定义的插件服务注册器。
- 它的 `bootstrap(Application $app)` 方法会读取 `addons/addons_service_provider.json` 文件，批量注册所有已启用插件的 ServiceProvider。
- 插件的 ServiceProvider 是通过扫描 `addons` 目录下的 `*ServiceProvider.php` 文件，自动收集并写入 `addons_service_provider.json`。
- **注册时机**：AddonsProvider 并没有在 `config/app.php` 里自动注册，而是通过如下方式**动态注册**：
  ```php
  (new \App\Meedu\AddonsProvider())->bootstrap(app());
  ```
- 这个调用通常出现在**插件管理相关的控制器、命令行工具或特定业务流程**中，比如插件启用/禁用/安装/升级时。
- 这样设计可以让插件系统更加灵活高效，便于扩展和维护。

---

## 3. 总结

- **全局服务**写在 `config/app.php` 的 `providers` 里，**插件服务**通过 `AddonsProvider` 动态注册。
- `AddonsProvider` 的注册是**按需触发**，不是全局自动。
- 插件的 ServiceProvider 信息存储在 `addons/addons_service_provider.json`，由 AddonsProvider 统一注册。
- 这样做有助于提升性能、增强灵活性、方便插件扩展。

---
