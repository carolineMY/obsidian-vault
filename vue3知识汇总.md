一、template
1、slot中传参数出去
```
子组件：
let data = ref({name:'ssdd'})
<slot name="content" :data="data"></slot>

父组件中使用：
<template #name="{data}">
	<div>{{data.name}}</div>
</template>
```
二、script

0、定义组件名称
（1）安装插件
```
npm i vite-plugin-vue-setup-extend -D
```
（2）在vite.config.js中调用
```
export default defineConfig(({ mode }) => {
	return {
		plugins:[
			VueSetupExtend(),
		]
	}
})
```
（3）定义组件名
```
<script setup lang="ts" name="myComponent"></script>
```
1、const props = defineProps({
	id:{
		type:string,
		default:''
	},
	modelValue:false
})
const  props = defineProps<{
	id:string,
	modelValue:boolean
}>()
2、const emits = defineEmits<{
	(e:'update:modelValue',value):void,
	(e:'onConfrim'):void
}>()

3、const {proxy} = getCurrentInstance()

4、const count = ref(0)

5、const fullName = computed(() => {
	return firstName.value+' ' + lastName.value
})
	computed使用实例[[vue封装el-dialog等反馈组件hook]]

6、watch(count,(val) => {
	// do something
},{
	immediate:true,
	deep:true
})

7、 watchEffect(() => {
	console.log(count)
})

8、watchSyncEffect(() => {

})

9、watchPostEffect

10、注入
父组件：provide('count',count)
后代组件：const  myCount = inject('count',0)  // 0为默认值
	
11、路由
	const router = userRouter() // 路由器
	const route = useRoute() // 当前路由
	路由跳转
	（1）直接跳转地址
		router.push(‘/login’) 
	（2）query拼接在地址栏上
			传参：
			router.push({ 
				path: '/about', 
				query: {id:1 }
			 })
			 使用：
			const route = useRoute()
			const id = route.query.id
	（3）params 传参 -- 必须在路由配置的路径后拼上动态路由‘
		如：{
					path: 'pages/about/:id'',
					component: '@/pages/about/index.vue'
				} 
		传参：
		router.push({
			name:'about',
			params:{
				id:1
			}
		})
		使用参数：
		const route = useRoute()
		const id = route.params.id

	


