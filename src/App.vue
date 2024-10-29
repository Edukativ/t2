<template>
  <div class="app flex h-screen flex-col">

    <header class="bg-white py-4">
      <nav class="space-x-8 font-semibold text-xl flex justify-end mr-28">
        <router-link to="/">Home</router-link>
        <router-link to="/users">Users</router-link>
        <router-link to="/profile">Profile</router-link>
      </nav>
    </header>

    <main class="mb-auto mx-32">
      <router-view></router-view>
    </main>

    <footer>
      <nav class="space-x-8 flex justify-center ">
        <a href="#">
          <FacebookIcon></FacebookIcon>
        </a>
        <a href="#">
          <InstagramIcon></InstagramIcon>
        </a>
        <a href="#">
          <TwitterIcon></TwitterIcon>
        </a>
        <a href="#">
          <LinkedinIcon></LinkedinIcon>
        </a>
      </nav>
      <p class="text-center font-semibold text-xs pt-6 mb-16">Copyright ©2020 All rights reserved </p>
    </footer>

  </div>
</template>


<script>
import FacebookIcon from './icons/Facebook.vue';
import InstagramIcon from './icons/Instagram.vue';
import TwitterIcon from './icons/Twitter.vue';
import LinkedinIcon from './icons/Linkedin.vue';

export default {
  name: 'HomePage',
  components: {
    FacebookIcon,
    InstagramIcon,
    TwitterIcon,
    LinkedinIcon,
  },
};
</script>