<template>
  <div class="profile-page py-12 max-w-md mx-auto">
    <div v-if="user && !expired" class="p-4 font-semibold text-nowrap text-stone-700 space-y-2">
      <h1 class="text-3xl font-bold mb-16 text-slate-800">My profile</h1>
      <img :src="user.image" alt="Profile Image" class="absolute size-32 rounded-full end-1/4 lg:size-48">
      <p class="profile_p">Username: {{ user.username }}</p>
      <p class="profile_p">Name: {{ user.firstName }}</p>
      <p class="profile_p">Lastname: {{ user.lastName }}</p>
      <p class="profile_p">Gender: {{ user.gender }}</p>
      <p class="profile_p">Email: {{ user.email }}</p>
    </div>
    <div v-else-if="!user && !expired">
      <p>Loading...</p>
    </div>
    <div v-if="expired">
      <h1 class="text-3xl font-bold mb-8 text-center text-slate-800">Authentication Problem</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Profile',
  data() {
    return {
      user: null,
      expired: false
    };
  },
  created() {
    fetch('https://dummyjson.com/auth/me', {
      method: 'GET',
      headers: {
        'Authorization': 'Bearer ' + localStorage.getItem('token'),
      },
    })
      .then((response) => response.json())
      .then((data) => {
        console.log(data);
        if (data.message === 'Invalid/Expired Token!') {
          this.$router.push('/login');
          this.expired = false;
        } else if (data.message === 'Token Expired!') {
          this.expired = true;
        } else {
          this.user = data;
          this.expired = false;
        }
      });
  },
};
</script>

<style scoped>
/* Дополнительные стили */
</style>