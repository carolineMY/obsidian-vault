1、使用淘宝镜像源
```
npm config set registry http://registry.npm.taobao.org
```
2、当前安装使用淘宝镜像源下载
```text
npm install --registry=http://registry.npmmirror.com
```
3、查看当前镜像源
```text
npm config get registry
```
4、查看某个包的版本
```
npm view uview-plus versions 查看所有版本 ['3.4.12', '3.4.13',...]
npm view uview-plus version 查看最新版本 3.4.12
```
5、查询包间的依赖关系（当出现依赖冲突时查询）
```
npm view pinia peerDependencies 
%% 查询pinia的依赖关系，比如pinia的xx版本需要兼容xx版本的vue %%
```
6、[npm与npx ](https://juejin.cn/post/7501975683548823579)

7、npx清除缓存 
npx clear-npx-cache

8、安装补丁（使用 patch-package 进行补丁修改node_modules的某个文件的某个方法）
```
npm install patch-package --save-dev
```
9、检查 npm 的全局安装路径
```
npm config get prefix
```
10、检查全局安装的某个包的路径，如pnpm

```
npm install -g pnpm
```