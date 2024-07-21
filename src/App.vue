<script setup>
import { ref } from 'vue';

const tasks = ref([]);
const newTask = ref("");

const addTask = () => {
  if(newTask.value.trim()) {
    tasks.value.push({
      id: `${Date.now()}-${Math.random()}`,
      text: newTask.value.trim(),
      completed: false
    });
  }
  newTask.value = "";
}

const toggleTaskCompletion = (task) => {
  task.completed = !task.completed;
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
        <input class="new-task" type="text" name="newTask" v-model="newTask" @change="toggleTaskCompletion">
      </label>
      <button class="add-button" type="submit">add</button>
    </form>
  </section>

  <section class="list-container">
    <h2>your tasks</h2>
    <ul class="list">
      <li class="list-item" v-for="task in tasks" :key="task.id">  
        <span class="task-text" :class="{ 'completed': task.completed }" @click="toggleTaskCompletion(task)">
          {{ task.text }}
        </span>
        <button @click="removeTask(task.id)">delete</button>
      </li>
    </ul>
  </section>

</template>




<style scoped>
</style>
