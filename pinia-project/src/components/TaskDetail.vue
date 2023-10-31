<template>
    <div class="task">
        <p>{{ task.title }}</p>
        <div class="buttons-action">
            <i class="material-icons" @click="taskStore.deleteTask(task.id)">delete</i>
            <i class="material-icons" :class="{active: task.isFav}" @click="taskStore.toggleFav(task.id)">favorite</i>
        </div>
    </div>
  
</template>

<script setup>
import { useTaskStore } from '../stores/TaskStore';

const props = defineProps(['task'])

const taskStore = useTaskStore()
</script>

<style>
li{
    list-style: none;
}

.task{
    margin: 2rem 0;
    display: flex;
    flex-direction: row;
    align-content: center;
    justify-content: space-between;
    padding: 2rem;
    box-shadow: 0rem 0rem 1rem gray;
    border-radius: 0.5rem;
    width: 30vw;
}

p{
    margin:0;
    padding: 0.5rem;
    font-size: 1rem;
}

.buttons-action{
    margin: 0 2rem;
}

i, button{
    margin: 0 1rem 0 0;
    padding: 0.5rem;
    border-radius: 0.5rem;
    border: rgb(23, 130, 23) solid 0.05rem;
    background: rgb(234, 210, 72);
    cursor: pointer;
}


input {
    margin: 0 1rem;
    padding: 0.5rem;
    border-radius: 0.5rem;
    border: rgb(23, 130, 23) solid 0.05rem;
}

.pinia-logo{
    width: 5rem;
}


h1{
    display: inline;
}

i.active{
    color: rgb(222, 47, 47);
}
</style>