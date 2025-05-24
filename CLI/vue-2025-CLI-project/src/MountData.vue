<script setup>
import { onMounted, ref } from "vue";

    const name = ref( "sabrina sabrina");
    const status = ref( 'active');
    const tasks = ref( ['task one', 'task two', 'task three', 'task four', 'task five']);
    const newTask=ref('');
    const toggleStatus = () => {
      if (status.value === 'active') {
        status.value = 'pending';
      } else if (status.value === 'pending') {
        status.value = 'inactive';
      } else {
        status.value = 'active';
      }
    };

  const addTask= () =>{
    if(newTask.value.trim() !== ''){
      tasks.value.push(newTask.value);
      newTask.value= '';
    }
  };


  const deleteTask= (index) => {
    tasks.value.splice(index, 1);
  } 

onMounted(async () =>{
try{
  const response = await fetch('https://jsonplaceholder.typicode.com/todos');
  const data = await response.json();
  tasks.value = data.map((task) => task.title);
} catch (error){
  console.log('Error fetching tasks');
}
});
</script>
<template>
  <h1>{{ name }}</h1><!-- interpolation -->

  <!-- directives  -->
  <!-- contional v-if, v-else-if, v-else  -->
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is inactive</p>


<!-- v-model form use of event.prevent  -->
  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask">
    <button type="submit">Submit</button>
  </form>
 
 
 
  <!-- loop v-for  -->
  <h1>Tasks:</h1>
  <ul>
    <li v-for="(task,index) in tasks" :key="task">
    <span>
      {{ task }}
    </span>  
    <button @click="deleteTask(index)">X</button>
    </li>
  </ul>


  <br>
  <h1>Use of V-on</h1>
  <!-- v-on directive, events & methods -->
  <button v-on:click="toggleStatus"> Change Status</button>
  <!-- another way -->
  <!-- <button @click="toggleStatus"> Change Status</button> -->
</template>
