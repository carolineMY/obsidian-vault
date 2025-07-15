---
cssclasses: []
aliases: 
tags:
---
```js
<script >
	export default {
		data(){
			return {
				count:0,
				firstName:"soda",
				lastName:'buffy'
			}
		},
		computed:{
			fullName(){
				return firstName+' ' + lastName
			}
		}
	}
</script>
<style lang="less" scoped>
</style>
```