<template>
    <div class="users-page py-16 max-w-5xl mx-auto flex justify-center">
      <ul>
        <li v-for="user in users" :key="user.id" class="mb-4 p-4 border shadow-neutral-300 shadow-md rounded-xl flex justify-between">
          <h2 class="text-xl font-semibold">{{ user.name }}</h2>
          <p class="text-gray-600 ml-10">{{ user.email }}</p>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Users',
    data() {
      return {
        users: [],
      };
    },
    created() {
      fetch('https://jsonplaceholder.typicode.com/users')
        .then((response) => response.json())
        .then((data) => {
          this.users = data;
        });
    },
  };
  </script>
  
  <style scoped>
  /* Дополнительные стили */
  </style>
  