<template>
  <div>
    <table
      border="1"
      width="200"
      align="center"
    >
    <tr>
      <th>ID</th>
      <th>Name</th>
      <th>Age</th>
      <th>Corse</th>
    </tr>
    <tr v-for="(item, index) of state.userList" :key="item.id" align="center">
      <td>{{ item.id }}</td>
      <td>{{ item.name }}</td>
      <td>{{ item.age }}</td>
      <td>{{ item.score }}</td>
    </tr>
  </table>
  </div>
</template>

<script setup>
import { io } from 'socket.io-client';
import { reactive } from 'vue';

const socket = io('http://127.0.0.1:3000');

socket.on('loadData', (data) => {
  state.userList = data;
});

const state = reactive({
  userList: []
});


</script>

<style>

</style>
