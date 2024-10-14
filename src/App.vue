<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <!-- A grey horizontal navbar that becomes vertical on small screens -->
  <nav class="navbar navbar-expand-sm bg-light">
    <div class="container-fluid">
      <!-- Links -->
      <ul class="navbar-nav">
        <li class="nav-item">
          <router-link class="nav-link" to="/">Home</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/about">ToDo</router-link>
        </li>
        <li class="nav-item"></li>
      </ul>
    </div>
  </nav>
  <RouterView />
</template>

<script>
export default {
  name: 'App'
}
</script>
<style scoped></style>
