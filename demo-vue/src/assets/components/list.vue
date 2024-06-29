<!--
 * @Description: 
 * @Version: 1.0
 * @Autor: Li Cheng
 * @Date: 2024-06-24 14:34:13
 * @LastEditors: Li Cheng
 * @LastEditTime: 2024-06-24 15:01:55
-->
<template>
  <div>
    <h1>User List</h1>
    <ul>
      <li v-for="(item, index) in list" :key="item.id">
        <span>{{ index + 1 }}.</span><span>学号：{{ item.id }}</span> -
        <span>姓名：{{ item.userName }}</span> -
        <span>年龄：{{ item.age }}</span>
        <button @click="deleteUser(index)">删除</button>
        <button @click="editUser(index)">编辑</button>
        <button @click="getYourName(item.id)">问名字</button>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { reactive } from 'vue';
const list = reactive([
  {
    id: 220812022,
    userName: '刘淑文',
    age: 18
  },
  {
    id: 220812008,
    userName: '蔡欣怡',
    age: 18
  },
  {
    id: 220812030,
    userName: '龙依',
    age: 18
  }
]);

const deleteUser = index => {
  list.splice(index, 1);
};

const editUser = index => {
  const item = list[index];
  item.age = 22;
};

const getYourName = id => {
  const student = list.find(item => item.id === id);
  alert(student.userName);
};
</script>

<style scoped></style>
