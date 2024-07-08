

<template>
  <section class="add-task-container">
    <h2>add task</h2>
    <form class="todo-form" @submit.prevent="addTask">
      <label>
        <input class="new-task" type="text" name="newTask" v-model="newTask">
      </label>
      <button class="add-button" type="submit">add</button>
    </form>
  </section>

  <section class="list-container">
    <h2>your tasks</h2>
    <ul class="list">
      <li class="list-item" v-for="(task, index) in tasks" :key="index" @click="markComplete">
        <span class="task-text">
          {{ task }}
        </span>
        <button @click="deleteTask">delete</button>
      </li>
    </ul>
  </section>

</template>

<script setup>
import { ref } from 'vue';

const newTask = ref("");
const tasks = ref([]);

const addTask = () => {
  tasks.value.push(newTask.value)
  newTask.value = "";
}

const deleteTask = (index) => {
  tasks.value.splice(index, 1)
}

const markComplete = () => {
  newTask.value
}

  
</script>

<style scoped>
</style>
