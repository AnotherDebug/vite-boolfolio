<script>
export default {
  name: 'Header'
}
</script>

<template>
  <header class="container">
    <ul class="nav">
  <li class="nav-item">
    <router-link class="nav-link" :to="{ name: 'home' }">Home</router-link>
  </li>
  <li class="nav-item">
    <router-link class="nav-link" :to="{ name:'about' }">About</router-link>
  </li>
  <li class="nav-item">
    <router-link class="nav-link" :to="{ name:'projects' }">Projects</router-link>
  </li>
  <li class="nav-item">
    <router-link class="nav-link" :to="{ name:'contacts' }">Contacts</router-link>
  </li>
</ul>
  </header>
</template>

<style lang="scss" scoped>
@use "../scss/partials/variables" as *;

header {
margin-top: 20px;
}
</style>
