<template>
  <div class="flex items-start pt-9 justify-center h-screen bg-neutral-300">

  
  <div class=" min-h-96  w-4/5 md:w-2/5 flex flex-col items-center py-9  justify-start bg-cyan-800 rounded-2xl ">

    <Header/>
    
    <AddTask @addTask="handleAddTask"/>
    <Tasks :tasks="tasks" @toggleTaskDone="handleToggleTaskDone" @removeTask="handleRemoveTask"/>
  </div>
</div>
</template>


<script setup>
import Header from"./components/Header.vue"
import AddTask from "./components/AddTask.vue"
import Tasks from "./components/Tasks.vue"

import { ref ,defineProps, onMounted } from 'vue';

// const tasks=ref([JSON.parse(localStorage.getItem('todoData'))]||[]);
const tasks=ref([]);
const Id=ref(0);

onMounted(() => {
  // Load stored tasks or initialize to an empty array
  const storedTasks = JSON.parse(localStorage.getItem('todoData')) || [];
  tasks.value = storedTasks;
  // Set the Id to the next available number based on the loaded tasks
  Id.value = storedTasks.length > 0 ? storedTasks[storedTasks.length - 1].id + 1 : 0;
});

const handleAddTask=(newTask) => { 
  tasks.value.Id=Id.value++;
tasks.value.push(newTask);
localStorage.setItem('todoData', JSON.stringify(tasks.value));


 }


 const handleRemoveTask=(e) => { 
  tasks.value.splice(e,1);
  localStorage.setItem('todoData', JSON.stringify(tasks.value));

  }

  const handleToggleTaskDone = (index) => {
  tasks.value[index].taskDone = !tasks.value[index].taskDone;
  localStorage.setItem('todoData', JSON.stringify(tasks.value));
};

  
</script>


<style scoped>

</style>
