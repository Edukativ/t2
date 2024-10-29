<template>
  <div class="home-page py-16 flex">
    <div class="space-y-12">
      <h1 class="text-slate-900 text-4xl font-bold mb-4">Home page</h1>
      <p class="text-slate-900 font-sans mb-8 text-wrap w-2/4">
        Amet minim mollit non deserunt ullamco est sit aliqua dolor
        do amet sint. Velit officia consequat duis enim velit mollit.
        Exercitation veniam consequat sunt nostrud
        amet.
      </p>
      <router-link to="/login">
        <button class="my-8 px-12 py-2 bg-red-400 text-white">Authorization</button>
      </router-link>
    </div>
    <!-- <img src="/src/assets/tools.svg" alt="tools image" class="absolute end-10"> -->
    <img src="/src/assets/tools.svg" alt="tools image" class="absolute end-20 size-128">
  </div>
</template>

<script>
export default {
  name: 'Home',
};
</script>

<style scoped>
/* Дополнительные стили */
</style>