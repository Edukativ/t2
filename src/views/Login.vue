<template>
    <div class="login-page py-4 pr-4 mx-auto shadow-neutral-300 shadow-md rounded-xl w-fit">
      <div class="flex ">
        <p class="text-xl font-bold ml-4">Authorization</p>
        <p v-if="error" class=" ml-20 text-red-500 font-bold text-nowrap text-lg">{{ error }}</p>
      </div>
      <form @submit.prevent="login" class="mx-20 mt-4 flex flex-col">
        <div class="mb-4 justify-center">
          <label for="username" class="block text-gray-700">Login</label>
          <input type="text" v-model="username" id="username" class="w-fit px-3 py-2 shadow-neutral-300 shadow-md rounded-xl ">
        </div>
        <div class="mb-4 justify-center ">
          <label for="password" class="block text-gray-700">Password</label>
          <input type="password" v-model="password" id="password" class="w-fit px-3 py-2 shadow-neutral-300 shadow-md rounded-xl ">
        </div>
        <button type="submit" class="justify-center px-4 py-2 text-gray-700">Submit</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Login',
    data() {
      return {
        username: '',
        password: '',
        error: null,
      };
    },
    methods: {
      login() {
        fetch('https://dummyjson.com/auth/login', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify({
            username: this.username,
            password: this.password,
          }),
        })
          .then((response) => response.json())
          .then((data) => {
            if (data.accessToken) {
              localStorage.setItem('token', data.accessToken);
              this.$router.push('/profile');
            } else {
              this.error = "Invalid credentials";
            }
          });
      },
    },
  };
  </script>
  
  <style scoped>
  /* Дополнительные стили */
  </style>
  