<script>
export default {
  data() {
    return {
      name: "sabrina sabrina",// optional api data() and interpolation
      status: 'active',
      tasks: ['task one', 'task two', 'task three', 'task four', 'task five'],
      link: "https://google.com",
      link2: "https://facebook.com",
    };
  },
  methods: {
    toggleStatus() {
      if (this.status === 'active') {
        this.status = 'pending';
      } else if (this.status === 'pending') {
        this.status = 'inactive';
      }else{
        this.status = 'active';
      }
    }
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

  <!-- v-bind  -->
  <h1>USe of v-bind</h1>
  <a v-bind:href="link"> click for google</a>
  <br>
  <!-- another way  -->
  <a :href="link2"> click for facebook</a>

  <br>
  <h1>Use of V-on</h1>
  <!-- v-on directive, events & methods -->
  <!-- <button v-on:click="toggleStatus"> Change Status</button> -->
   <!-- another way -->
  <button @click="toggleStatus"> Change Status</button>
</template>
