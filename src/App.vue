<!-- App.vue -->
<template>
  <div class="todo-app">
    <h1>Minhas Tasks</h1>
    <input v-model="newTask" @keyup.enter="addTask" placeholder="Nova task" />
    <button @click="addTask">Adicionar</button>
    <ul>
      <li v-for="task in tasks" :key="task.id">
        {{ task.text }}
        <button @click="deleteTask(task.id)">X</button>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const tasks = ref([])
const newTask = ref('')

function addTask() {
  if (!newTask.value.trim()) return
  tasks.value.push({ id: Date.now(), text: newTask.value.trim() })
  newTask.value = ''
}

function deleteTask(id) {
  tasks.value = tasks.value.filter(t => t.id !== id)
}
</script>
