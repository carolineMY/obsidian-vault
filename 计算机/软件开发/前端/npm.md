1、使用淘宝镜像源
```text
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
npm view uview-plus versions
```
5、查询包间的依赖关系（当出现依赖冲突时查询）
```
npm view pinia peerDependencies 
%% 查询pinia的依赖关系，比如pinia的xx版本需要兼容xx版本的vue %%
```
