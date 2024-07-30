<!-- src/App.vue -->
<template>
  <div id="app">
    <h1>Users List</h1>
    <ul>
      <li v-for="user in users" :key="user.id">{{ user.id }}</li>
      <li v-for="user in users" :key="user.name">{{ user.name }}</li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      users: [],
    };
  },
  mounted() {
    this.fetchUsers();
  },
  methods: {
    async fetchUsers() {
      try {
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/users"
        );
        this.users = response.data;
      } catch (error) {
        console.error("There was an error fetching the users:", error);
      }
    },
  },
};
</script>

<style></style>
