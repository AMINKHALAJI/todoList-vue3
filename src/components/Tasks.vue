<template>
  
    <div
      class="flex w-3/5 mt-5  py-3 px-4 rounded cursor-pointer justify-between items-center bg-cyan-50 text-black"
      
      :class="{taskDone: task.taskDone}"
      v-for="(task, index) in tasks" :key="index"
      @click="taskDone(index)"
    >
      <h4>{{ task.name }}</h4>
      <button @click="handleRemove(index)"  class="text-red-600 ">Delete</button>
    </div>
    
  
</template>

<script setup>
import { ref ,defineProps,defineEmits } from 'vue';


const props = defineProps({
  tasks: Array
});

const emit = defineEmits(['removeTask','toggleTaskDone']);
const clicked=ref([false]);


const handleRemove = (index) => { 
    emit('removeTask', index);
 }

//  const taskDone = (index) => {
  
//     clicked.value[index]=! clicked.value[index];
    
//  }
 const taskDone = (index) => {
  emit('toggleTaskDone', index);
};







</script>

<style scoped>
.taskDone{
  /* text-decoration: underline; */
  border-left: 0.8rem solid rgb(6, 236, 121);
  color: rgb(218, 239, 238);
  background-color:rgb(17, 75, 78) ;

}
</style>
