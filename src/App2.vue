<script>
export default {
  data() {
    return {
      name: 'Joe Doe',
      status: 'active',
      tasks: ['task1', 'task2', 'task3'],
      link: 'https://www.google.com/'
    };
  },
  methods: {
    toggleStatus() {
      if (this.status === "active") {
        this.status = "inactive";
      } else {
        this.status = "active";
      }
    }
  },
};
</script>

<template>
  <p v-if="status === 'active'">{{name}}, {{status}}</p>
  <p v-else-if="status === 'inactive'">{{status}}</p>
  <p v-else>internalservererror, {{status}}</p>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks" :key="task">{{task}}</li>
  </ul>
<!--  <a v-bind:href="link">google</a>-->
  <a :href="link">google</a>
  <br>
<!--  <button v-on:click="toggleStatus">Change Status</button>-->
  <button @click="toggleStatus">Change Status</button>
</template>
