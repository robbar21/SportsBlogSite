<script>
  import { RouterView, RouterLink } from 'vue-router';
  import loginService from './services/login-service';
  export default {
    components: {
      RouterView,
      RouterLink
    },
    methods: {
      logout() {
        return loginService.logout();
      }
    }
  }
</script>

<template>
  <header>
    <nav v-if="$store.state.token != null">
      <menu>
        <li>
          <router-link to="/">Home</router-link>
        </li>
        <li>
          <router-link to="/about">About</router-link>
        </li>
        <li>
          <router-link to="/posts">Blogs</router-link>
        </li>
      </menu>
      <menu>
        <li v-if="$store.state.user">
          Welcome, {{ $store.state.user?.username }}
        </li>
        <li>
          <a href="#" @click="logout">Logout</a>
        </li>
      </menu>
    </nav>
  </header>
  <main>
    <RouterView />
  </main>
  <footer>
    <p>&copy; 2024</p>
  </footer>
</template>

<style scoped>
  /* Styles for content in this component are in main.css, as they are top-level (directly below #app) */
</style>