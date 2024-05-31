<template>
    <div class="w-full"  >
        <form action="#" @submit.prevent="handleSubmit" class="py-10 w-full flex  justify-around ">
            <input type="text" class="py-2 px-4 rounded-lg w-3/5" v-model="task" name="task" id="" placeholder="Enter a new task">
            <button class= " py-2 px-4 rounded-md bg-cyan-50 text-teal-600">Add Task</button>
            
        </form>
    </div>
</template>

<script setup>

import { ref,defineEmits } from 'vue';

const task = ref('');
const emit = defineEmits(['addTask']);


const handleSubmit = () => { 
    if(task.value.trim()!==''){
    emit('addTask', task.value);
    
    task.value = '';
    }else{
        alert('task cant be empty')
    }
 }

</script>

<style scoped>

</style>