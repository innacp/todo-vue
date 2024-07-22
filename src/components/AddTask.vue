<script setup>
import { ref } from 'vue';
import TaskList from './TaskList.vue';

const tasks = ref([]);
const newTask = ref("");

const addTask = () => {
  if(newTask.value.trim()) {
    tasks.value = [
    ...tasks.value,  
    {
      id: `${Date.now()}-${Math.random()}`,
      text: newTask.value,
      completed: false
    }];
  newTask.value = "";
  }
}

const removeTask = (id) => {
  tasks.value = tasks.value.filter((task) => task.id !== id);
}
</script>

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
  <TaskList :elements="tasks" @delete-task="removeTask" />
</template>