
### 一、什么是AI智能体 AI Agent 

定制化 Agent ，**自主调用系列工具**完成复杂任务。
能够分解任务、推理思考、调用工具的对话式智能助手；

![[Pasted image 20241101131327.png]]

![[Pasted image 20241101135503.png]]

![[Pasted image 20241101130428.png]]




### 二、工作流
编排 AI 工作流，**人为规划嵌入模型、工具**等，使其输出更稳定可控

#### 1、Dify（开源的 LLM 应用开发平台） - 反思翻译工作流

基于流程编排的方式定义更加灵活的 LLM 工作流；
工作流通过将复杂的任务分解成较小的步骤（节点）降低系统复杂度，减少了对提示词技术和模型推理能力的依赖，提高了 LLM 应用面向复杂任务的性能，提升了系统的可解释性、稳定性和容错性。

##### Chatflow 对话类工作流：给出指令 → 生成内容 → 就内容进行多次讨论 → 重新生成结果 → 结束

	Chatflow 内置聊天记忆（Memory），用于存储和传递多轮对话的历史消息，可在 LLM 、问题分类等节点内开启，Workflow 无 Memory 相关配置，无法开启。
	
Workflow 自动化工作流：给出指令 → 生成内容 → 结束

![[Pasted image 20241101114229.png]]

###### （1）开始节点
![[Pasted image 20241101114343.png]]
###### （2）设置默认值
![[Pasted image 20241101114352.png]]
system：为对话提供高层指导，定专家角色，要做的事
user: 向模型提供指令、查询或任何基于文本的输入

###### （3）初始翻译
![[Pasted image 20241101114551.png]]
###### （4）判断国家
![[Pasted image 20241101114516.png]]
###### （5）反思翻译
![[Pasted image 20241101115827.png]]
###### （6）变量聚合器
将多分支的变量聚合为一个变量，以实现下游节点的统一配置
![[Pasted image 20241101120115.png]]
###### （6）优化翻译- 针对反思给出优化
![[Pasted image 20241101120616.png]]
###### （7）结束-输出翻译结果
![[Pasted image 20241101120512.png]]

##### **迭代**

![[Pasted image 20241101132717.png]]

#### 2、漫画翻译工作流

![[Pasted image 20241101134816.png]]

#### 3、Agent 与工作流

![[Pasted image 20241101140011.png]]


### 三、结合
![[Pasted image 20241101130250.png]]