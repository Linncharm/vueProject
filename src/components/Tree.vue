<!--
一个可以递归渲染自己的嵌套树组件。
你可以双击一个项目将其转变为一个文件夹。
-->

<script setup>
import { ref } from 'vue'
import TreeItem from './TreeItem.vue'

const treeData = ref({
  name: 'My Tree',
  children: [
    { name: 'hello' },
    { name: 'world' },
    {
      name: 'child folder',
      children: [
        {
          name: 'child folder',
          children: [{ name: 'hello' }, { name: 'world' }]
        },
        { name: 'hello' },
        { name: 'world' },
        {
          name: 'child folder',
          children: [{ name: 'hello' }, { name: 'world' }]
        }
      ]
    }
  ]
})
</script>

<template>
  <el-card shadow="always" style="max-width: 500px; font-weight: bold">
    <template #header>
      <slot name="title"></slot>
    </template>
    <span>This is a tree</span>
  </el-card>
  <br>
  <ul>
    <TreeItem class="item" :model="treeData"></TreeItem>
  </ul>
</template>

<style>
.item {
  cursor: pointer;
  line-height: 1.5;
}
.bold {
  font-weight: bold;
}
</style>