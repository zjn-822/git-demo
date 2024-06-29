<!--
 * @Description: 
 * @Version: 1.0
 * @Autor: Li Cheng
 * @Date: 2024-06-24 09:52:27
 * @LastEditors: Li Cheng
 * @LastEditTime: 2024-06-24 16:28:11
-->
<script setup>
import { ref } from 'vue';
import list from './components/list.vue';
import Computed from './components/computeds.vue';
import baseVue from './components/base.vue';
import HelloWorld from './components/HelloWorld.vue';
import formModel from './components/formModel.vue';
import life from './components/life.vue';

const type = ref('base');
const message = ref('你好👋');

function warn(message, event) {
  console.log('event', event);
  // 这里可以访问原生事件
  if (event) {
    event.preventDefault();
  }
  alert(message);
}
</script>

<template>
  <button :class="{ active: type === 'base' }" @click="type = 'base'">base</button>
  <button :class="{ active: type === 'computed' }" @click="type = 'computed'">computed</button>
  <button :class="{ active: type === 'list' }" @click="type = 'list'">list</button>
  <button :class="{ active: type === 'hello' }" @click="type = 'hello'">hello</button>
  <button :class="{ active: type === 'form' }" @click="type = 'form'">form</button>
  <button :class="{ active: type === 'life' }" @click="type = 'life'">life</button>

  <div class="border pd-20">
    <baseVue v-if="type === 'base'" />
    <Computed v-if="type === 'computed'" />
    <list v-if="type === 'list'" />
    <HelloWorld v-if="type === 'hello'" msg="Hello Vue 3 + Vite" :message="message" />
    <formModel v-if="type === 'form'" />
    <life v-if="type === 'life'" />
  </div>

  <button @click="message = '同学们好'">切换 message</button>
  <button @click="event => warn('event事件', event)">获取事件</button>
</template>

<style scoped>
.active {
  color: #ff99cc;
}

.border-black {
  border: #000001 solid px;
}

.pd-20 {
  padding: 20px;
}
</style>
