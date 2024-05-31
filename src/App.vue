<script setup>
import Header from"./components/Header.vue"
import AddTask from "./components/AddTask.vue";
import Tasks from "./components/Tasks.vue"

import { ref ,defineProps } from 'vue';

const tasks=ref([]);

const Id=ref(0);

const handleAddTask=(newTask) => { 
  tasks.value.Id=Id.value++;
tasks.value.push(newTask);


 }

 const handleRemoveTask=(e) => { 
  tasks.value.splice(e,1)
  
  }
</script>

<template>
  <div class="flex items-start pt-9 justify-center h-screen bg-neutral-300">

  
  <div class=" min-h-96  w-4/5 md:w-2/5 flex flex-col items-center py-9  justify-start bg-cyan-800 rounded-2xl ">

    <Header/>
    
    <AddTask @addTask="handleAddTask"/>
    <Tasks :tasks="tasks" @removeTask="handleRemoveTask"/>
  </div>
</div>
</template>

<style scoped>

</style>
