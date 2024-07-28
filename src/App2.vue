<script setup>
import {onMounted, ref} from 'vue';

const name = ref('Joe Doe')
const status = ref('active')
const tasks = ref(['task1', 'task2', 'task3'])
const newTask = ref('')

const toggleStatus = () => {
  if (status.value === "active") {
    status.value = "inactive";
  } else {
    status.value = "active";
  }
}

const addTask = () => {
  if (newTask.value.trim() !== '') {
    tasks.value.push(newTask.value)
    newTask.value = ''
  }
}

const deleteTask = (index) => {
  tasks.value.splice(index, 1)
}

onMounted(async () => {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/todos")
    const data = await response.json()
    tasks.value = data.map((task) => task.title)
  } catch (error) {
    console.log("error", error)
  }
});
</script>

<template>
  <p v-if="status === 'active'">{{ name }}, {{ status }}</p>
  <p v-else-if="status === 'inactive'">{{ status }}</p>
  <p v-else>internalservererror, {{ status }}</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" v-model="newTask"/>
    <button type="submit">Add</button>
  </form>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)">Delete</button>
    </li>
  </ul>
  <!--  <a v-bind:href="link">google</a>-->
  <!--  <button v-on:click="toggleStatus">Change Status</button>-->
  <button @click="toggleStatus">Change Status</button>
</template>
