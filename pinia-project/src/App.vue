<template>
  <div>
    <main>
      <header>
        <img src="./assets/pinia-logo.svg" alt="pinia logo" class="pinia-logo">
        <h1>Pinia Tasks</h1>
      </header>
      <TaskForm></TaskForm>

      <div class="loading" v-if="loading">Loading tasks...</div>
      <h2>All tasks: {{ totalCount }}</h2>
      <ul>
        <li v-for="task in tasks" :key="task.id">
          <TaskDetail :task="task"></TaskDetail>
        </li>
      </ul>

      <h2>Fav tasks: {{ favCount }}</h2>
      <ul>
        <li v-for="task in favs" :key="task.id">
          <TaskDetail :task="task"></TaskDetail>
        </li>
      </ul>
    </main>
    <button @click="taskStore.$reset">Reset state</button>
  </div>
</template>


<script setup>
import { storeToRefs } from 'pinia';
import { useTaskStore } from './stores/TaskStore';
import TaskDetail from './components/TaskDetail.vue';
import TaskForm from './components/TaskForm.vue';

const taskStore = useTaskStore();
taskStore.getTasks()

const { tasks, loading, favs, totalCount, favCount } = storeToRefs(taskStore)

</script>

<style>
.loading{
  font-size: 1.5rem;
  color: rgb(234, 210, 72);
}
</style>

