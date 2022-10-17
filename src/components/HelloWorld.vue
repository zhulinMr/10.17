
<template>
  <h1>{{ msg }}</h1>
  <h2>{{count}}</h2>
  <p>111</p>
  <button @click="handleAdd">点击</button>
  <el-button>Default</el-button>
    <el-button type="primary">Primary</el-button>
    <el-button type="success">Success</el-button>
    <el-button type="info">Info</el-button>
</template>

<script setup lang="ts">
import { computed, ref } from 'vue'
// 引入useStore
import {useStore} from "../store/index"
// 初始化store
const store = useStore()
// 获取vuex getters里面的count
const count = computed(()=>{
  return store.getters.getCount
})
defineProps<{ msg: string }>()
const num = ref(0)
// 点击触发
const handleAdd=()=>{
  num.value+=1
  store.commit("setCount",num.value)
}
</script>



<style scoped>
.read-the-docs {
  color: #888;
}
</style>
