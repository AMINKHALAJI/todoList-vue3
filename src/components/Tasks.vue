<template>
  
    <div
      class="flex w-3/5 mt-5  py-3 px-4 rounded cursor-pointer justify-between items-center bg-cyan-50 text-black"
      
      :class="{ taskDone: clicked[index] }"
      v-for="(task, index) in tasks" :key="index"
      @click="taskDone(index)"
    >
      <h4>{{ task }}</h4>
      <button @click="handleRemove(index)"  class="text-red-600 ">Delete</button>
    </div>
    
  
</template>

<script setup>
import { ref ,defineProps,defineEmits } from 'vue';

const emit = defineEmits(['removeTask']);
const clicked=ref([false]);


const handleRemove = (index) => { 
    emit('removeTask', index);
 }

 const taskDone = (index) => {
  
    clicked.value[index]=! clicked.value[index];
    
 }



const props = defineProps({
  tasks: Array
});



</script>

<style scoped>
.taskDone{
  text-decoration: line-through;
  /* background-color: rgb(40, 156, 160); */
  border-left: 1rem solid red;

}
</style>
