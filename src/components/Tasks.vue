<template>
  
    <div
      class="flex w-3/5 mt-5  py-3 px-4 rounded justify-between items-center bg-cyan-50 text-black"
      v-for="(task, index) in tasks" :key="index"
    >
      <h4>{{ task }}</h4>
      <button @click="handleRemove(index)"  class="text-red-600 ">x</button>
    </div>
    
  
</template>

<script setup>
import { ref ,defineProps,defineEmits } from 'vue';

const emit = defineEmits(['removeTask']);


const handleRemove = (index) => { 
    emit('removeTask', index);
 }



const props = defineProps({
  tasks: Array
});



</script>

<style scoped></style>
