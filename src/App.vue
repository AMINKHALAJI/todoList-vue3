<script setup>
import Header from"./components/Header.vue"
import AddTask from "./components/AddTask.vue";
import Tasks from "./components/Tasks.vue"
</script>

<template>
  <div class="flex items-center justify-center h-screen bg-neutral-300">

  
  <div class=" h-[40em] w-2/5 flex flex-col items-center  justify-start bg-cyan-800 rounded-2xl ">

    <Header/>
    
    <AddTask/>
    <Tasks/>
  </div>
</div>
</template>

<style scoped>

</style>
