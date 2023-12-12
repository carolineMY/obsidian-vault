
// 对通用弹层组件的封装，用于业务弹层，或最终使用的父组件
如：父组件F1：列表页面，使用子组件C1：新增一条数据的新增dialog, 该子组件使用项目中封装的基础dialog组件D11

1、在父组件F1中：
const { isVisible,onConfirm} = useFeedBack()
<C1  v-model="isVisible" @onConfirm="onConfirm"/>

2、在子组件C1中：
const { isVisible,onClose,onConfirm} = useFeedBack(emits) // emits
<D11  v-model="isVisible" @onClose="onClose" @onConfirm="onConfirm">


import { ref, computed, getCurrentInstance, Ref } from 'vue'

export default function useFeedBack(emits?: any) {
  const { proxy } = getCurrentInstance() as any
  let isVisible: Ref<boolean>
  const isLoading = ref(false)
  const openFeedBack = () => (isVisible.value = true)
  const closeFeedBack = () => (isVisible.value = false)
  const openLoading = () => (isLoading.value = true)
  const closeLoading = () => (isLoading.value = false)

  if (emits) {
    // 双向绑定值
    isVisible = computed({
      get: () => {
        return proxy.modelValue
      },
      set: (val: boolean) => {
        emits('update:modelValue', val)
      }
    })

	// 点击关闭
    const onClose = () => {
      isVisible.value = false
      emits('close')
    }
    
    // 点击确认按钮
    const onConfirm = () => {
      onClose()
      emits('confirm')
    }
    
    return { 
	    isVisible, 
	    isLoading,
	     openFeedBack, 
	     closeFeedBack, 
	     openLoading, 
	     closeLoading, 
	     onClose, 
	     onConfirm
	   }
  } else {
    isVisible = ref(false)
    return { isVisible, isLoading, openFeedBack, closeFeedBack, openLoading, closeLoading }
  }
}