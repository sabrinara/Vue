<script>
export default{
  data(){
    return {
      name: "sabrina sabrina",// optional api data() and interpolation
      status: 'active',
      tasks: ['task one','task two','task three','task four','task five']
    };
  },
};
</script>
<template>
 <h1>{{name}}</h1><!-- interpolation -->

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
</template>




