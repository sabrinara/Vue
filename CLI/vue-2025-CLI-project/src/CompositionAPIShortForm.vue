<script setup>
import { ref } from "vue";

    const name = ref( "sabrina sabrina");
    const status = ref( 'active');
    const tasks = ref( ['task one', 'task two', 'task three', 'task four', 'task five']);
    const toggleStatus = () => {
      if (status.value === 'active') {
        status.value = 'pending';
      } else if (status.value === 'pending') {
        status.value = 'inactive';
      } else {
        status.value = 'active';
      }
    };

</script>
<template>
  <h1>{{ name }}</h1><!-- interpolation -->

  <!-- directives  -->
  <!-- contional v-if, v-else-if, v-else  -->
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is inactive</p>

  <!-- loop v-for  -->
  <h1>Tasks:</h1>
  <ul>
    <li v-for="task in tasks" key="task">{{ task }} </li>
  </ul>


  <br>
  <h1>Use of V-on</h1>
  <!-- v-on directive, events & methods -->
  <button v-on:click="toggleStatus"> Change Status</button>
  <!-- another way -->
  <!-- <button @click="toggleStatus"> Change Status</button> -->
</template>
