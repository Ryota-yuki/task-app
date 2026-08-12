<template>
  <div class="app">
    <h1>タスク管理</h1>
    <input v-model="newTask" type="text" placeholder="タスク名を入力" />
    <button @click="addTask">追加</button>

    <ul>
      <li v-for="task in tasks" :key="task.id">
        {{ task.title }}
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const newTask = ref('')
const tasks = ref([
  { id: 1, title: 'サンプルタスク1', done: false },
  { id: 2, title: 'サンプルタスク2', done: false },
])

function addTask() {
  if (!newTask.value.trim()) return

  tasks.value.push({
    id: Date.now(),
    title: newTask.value.trim(),
    done: false,
  })

  newTask.value = ''
}
</script>
