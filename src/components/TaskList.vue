<script setup>
const props = defineProps({
  elements: {
    type: Array,
  },
});

const emit = defineEmits(['delete-task']);

const toggleTaskCompletion = (task) => {
  task.completed = !task.completed;
}

const deleteTask = (id) => {
  emit('delete-task', id);
}
</script>

<template>
  <section class="list-container">
    <h2>your tasks</h2>
    <ul class="list">
      <li class="list-item" v-for="task in props.elements" :key="task.id">  
        <span class="task-text" :class="{ 'completed': task.completed }" @click="toggleTaskCompletion(task)">
          {{ task.text }}
        </span>
        <button @click="deleteTask(task.id)">delete</button>
      </li>
    </ul>
  </section>
</template>