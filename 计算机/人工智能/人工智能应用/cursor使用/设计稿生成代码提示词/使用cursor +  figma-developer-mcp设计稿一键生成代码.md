#### 一、figma准备
##### 1、注册figma账号，获取figma的access;

  （1）头像=>settings=>security=>generate new token
  ![[Pasted image 20250612134043.png]]
 
 （2）生成key时需要开启read权限，否则mcp读取设计稿报错
 
  ==**"Error fetching file: Cannot read properties of undefined (reading 'children')"**==
  
  ![[Pasted image 20250612134243.png]]
  
  （3）生成的key需妥善保管，只有一次复制机会
  
##### 2、准备figma设计稿链接
- 选中一组需要绘制的页面（group selection 或 Frame selection）
- Copy/Paste as => Copy link to selection
- 获取到设计稿链接，如：
```
 https://www.figma.com/design/7vacr5ZSzAnRNrGYgFWMRG/Untitled?node-id=1-1413&t=TpjpNvtRyK1Z0coV-4
```

![[Pasted image 20250612140711.png]]

常见问题：
- 问：若Copy/Paste as 没有 Copy link to selection项
- 答：可先选中之后作为一组group selection，再Copy/Paste as

- 问：没有现成的设计稿，想测试下
- 答：随便创建一个设计稿 或者 从template中随便找一个模版，然后点击open in figma
-  open in figma 可能很慢，请耐心等待；
- 打开后复制页面到你自己的面板中，再Copy link to selection获取到设计稿链接
- ![[Pasted image 20250612141347.png]]
![[Pasted image 20250612141357.png]]


#### 二、figma mcp准备
##### 1、安装figma-developer-mcp
进入mcp.so或者到 **[Figma-Context-MCP github仓库](https://github.com/GLips/Figma-Context-MCP)** 复制mcp的配置
其中**YOUR-KEY**是第一步生成的token，复制token替换为你自己的key即可

```
{
  "mcpServers": {
    "Framelink Figma MCP": {
      "command": "cmd",
      "args": ["/c", "npx", "-y", "figma-developer-mcp", "--figma-api-key=YOUR-KEY", "--stdio"]
    }
  }
}
```

使用上述配置，等待mcp设置变成绿的点，说明安装完成；
![[Pasted image 20250612091653.png]]

常见问题：
- 问：加载mcp过程中出现 **==0 enabled tools==** 红点报错，说明mcp安装存在问题
- 答：
- **检查node版本**是否大于18，node > 18
- 若node版本>18,重新开启仍然存在问题，请**清除npx缓存**重试
```
npx清除缓存：npx clear-npx-cache
```

#### 三、开始生成代码

##### 1、生成html+tailwind提示词
```
你是一个大厂资深前端研发工程师，根据我提供的Figma UI设计稿，生成前端页面 
1、Figma UI设计稿：@https://www.figma.com/design/7vacr5ZSzAnRNrGYgFWMRG/Untitled?node-id=4-72&t=g4zFQFEWQtvZVxDD-4 
2、 使用HTML、Tailwind CSS实现前端页面 
3、限制：为了演示效果将全部生成的页面都放到一个HTML中展示
- 每个界面应作为独立的 HTML 文件存放，例如 home.html、profile.html、settings.html 等。
- index.html 作为主入口，不直接写入所有界面的 HTML 代码，而是使用 iframe 的方式嵌入这些 HTML 片段，并将所有页面直接平铺展示在 index 页面中，而不是跳转链接，
- index.html不需要副标题和需求介绍，iframe所在的div，尺寸375x812。

```
**生成结果如下**

![[Pasted image 20250612142950.png]]

##### 2、生成taro项目提示词
```
你是一个大厂资深前端研发工程师，根据我提供的Figma UI设计稿，生成前端页面 
1、Figma UI设计稿：@https://www.figma.com/design/7vacr5ZSzAnRNrGYgFWMRG/Untitled?node-id=4-72&t=g4zFQFEWQtvZVxDD-4 
2、生成前端代码
- 前端语言使用当前项目所用框架taro
- 按页面构建代码放入pages中，无对应页面则创建
- 图片放入当前项目/src/assets/images文件夹下
- 图片文件按页面存放，没有对应页面的图片文件夹则创建再存放
- 样式严格按照提供的设计稿1:1绘制
- 数据可先采用假数据
- 一切开发规范参照当前项目

3、按页面创建，创建完一个页面等我确认后继续

```
##### 3、生成uniapp项目提示词
```
你是一个大厂资深前端研发工程师，根据我提供的Figma UI设计稿，生成前端页面 
1、Figma UI设计稿：@https://www.figma.com/design/7vacr5ZSzAnRNrGYgFWMRG/Untitled?node-id=4-72&t=g4zFQFEWQtvZVxDD-4 
2、生成前端代码 
 - 前端语言使用当前项目所用框架uniapp 
 - 按页面构建代码放入pages中，无对应页面则创建,index 页面使用设计稿中的welcom页面代替 
 - 图片放入当前项目/src/static/images文件夹下 
 - 图片文件按页面存放，没有对应页面的图片文件夹则创建再存放 
 - 样式严格按照提供的设计稿1:1绘制 
 - 数据可先采用假数据 
 - 一切开发规范参照当前项目 
3、按页面创建，创建完一个页面等我确认后继续
```
**taro、uniapp项目生成结果**

![[Pasted image 20250612144820.png]]
##### 4、生成的代码

**相对比较规整**

- taro代码
![[Pasted image 20250612150719.png]]
- uniapp代码
![[Pasted image 20250612150751.png]]

#### 四、figma mcp 工作流程

- （1）在**cursor**的**chat**里输出提示词，需粘贴设计稿链接，chat/Agent 模型使用claude-3.7-sonnet 或claude-4-sonnet 
- （2）调用figma-developer-mcp
-  调用get_figma_data获取设计稿原数据，包含元素、字体、颜色、文本等，如
![[Pasted image 20250612150217.png]]
- 调用download_figma_images 下载文件中使用的 SVG 和 PNG 图像
- 最后，根据设计稿分析结果 及 提示词要求生成页面代码
![[Pasted image 20250612153755.png]]
#### 五、使用感受

##### 优点

（1）还原度较高，稍微二次开发即可投入使用
（2）生成代码较规整
（3）代码注释齐全
（4）样式类名、函数名等命名语义化

##### 缺点

（1）细节完成度不高
（2）对设计稿依赖稿，若设计稿不是很通用的设计，可能存在还原错误
- 如下图：无论是html 还是taro\uniapp 最终生成的页面,和设计稿都相差甚远；主要原因是设计稿中该元素的背景色没有使用fill填充，颜色读取错误。
 ![[Pasted image 20250612151519.png]]
（3）依赖提示词，需要一些前置条件，比如：
- 在taro项目中使用时，由于取到的设计稿尺寸是375x812，而项目中的尺寸设计尺寸是750，所以导致渲染的页面整体缩小了一半
- 故而，在使用的时候应先让cursor充分了解当前项目
  针对以上问题，修改项目配置或设计稿尺寸，此处修改项目配置
![[Pasted image 20250612153052.png]]
（4）有些细节需要反复调试，由于cursor 生成代码与自己本身编码习惯可能有所差异，所以可能存在意向不到的bug,需要反复调试，即使让cursor修改，仍然需要时间
（5）一次选择多多设计稿可能会生成报错，建议分批生成

##### 总结

总的来说，**非常不错！**
如果熟练使用，可以**快速开发静态页面！**
如果用的**越多**，cursor也会越来越熟悉你当前项目的编码习惯及设计习惯，会越用**越顺手！**

**Use more, code more, joy galore!**