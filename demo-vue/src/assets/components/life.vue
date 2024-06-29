<!--
 * @Description: 
 * @Version: 1.0
 * @Autor: Li Cheng
 * @Date: 2024-06-24 16:25:54
 * @LastEditors: Li Cheng
 * @LastEditTime: 2024-06-24 16:34:42
-->
<template>
  <div id="content">{{ context }}</div>
  <button @click="context = 'Hello World'">change</button>
</template>

<script setup>
import {
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
  ref
} from 'vue';

const context = ref('Hello Vue 3');

onBeforeMount(() => {
  console.log('1.组件即将挂载，此时组件的模板已经被编译，但是还没有挂载到 DOM 上。');
  const content = document.getElementById('content');
  console.log(content); // 输出：null
});

onMounted(() => {
  console.log('2.组件已经挂载，此时可以执行 DOM 相关的操作，比如直接访问 DOM 元素。');
  const content = document.getElementById('content');
  console.log(content); // 输出：null
});

onBeforeUpdate(() => {
  console.log('3.组件即将更新，此时组件的状态已经更新，但是 DOM 还未重新渲染。');
});

onUpdated(() => {
  console.log('4.组件已经更新，此时 DOM 已经更新，可以执行依赖于更新后 DOM 的操作。');
});

onBeforeUnmount(() => {
  console.log('5.组件即将卸载，此时组件实例仍然存在。');
  const content = document.getElementById('content');
  console.log(content); // 输出：null
});

onUnmounted(() => {
  console.log('6.组件已经卸载，此时组件实例已经被销毁。');
});
</script>
