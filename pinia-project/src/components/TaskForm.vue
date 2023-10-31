<template>
  <form @submit.prevent="handleSubmit" class="form">
    <input
        type="text"
        placeholder="I need to do ..."
        v-model="newTask"
    >
    <button>Add new task</button>
  </form>
</template>

<script setup>
import { useTaskStore } from '../stores/TaskStore';
import { ref } from 'vue'

const taskStore = useTaskStore()
const newTask = ref('')

const handleSubmit = () => {
    if (newTask.value.length > 0) {
        taskStore.addTask({
            id: Number(new Date()),
            title: newTask.value,
            isFav: false
        })
    }
    newTask.value = ''
}

</script>

<style>
.form {
    margin: 1.5rem 0;
}
</style>