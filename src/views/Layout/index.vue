<script setup>

import LayoutNav from './components/LayoutNav.vue'
import LayoutHeader from './components/LayoutHeader.vue'
import LayoutFooter from './components/LayoutFooter.vue'
import LayoutFixed from './components/LayoutFixed.vue'

// 触发获取导航列表的action

import { useCategoryStore } from '@/stores/categoryStore'
import { onMounted } from 'vue'

//使用状态库
const categoryStore = useCategoryStore()
// 获取数据，数据使用是在layout的子组件中使用
onMounted(() => categoryStore.getCategory())
</script>

<template>
  <LayoutFixed />
  <LayoutNav />
  <LayoutHeader />
  <!-- 添加key 破坏复用机制 强制销毁重建 -->
  <!-- <RouterView :key="$route.fullPath" /> -->
                                              <!-- 二级路由出口 默认加载home-->
  <RouterView />
  <LayoutFooter />
</template>