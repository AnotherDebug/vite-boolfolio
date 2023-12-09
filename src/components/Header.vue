<script>
export default {
  name: 'Header'
}
</script>

<template>
  <header class="container">
    <ul class="nav">
  <li class="nav-item">
    <router-link class="nav-link" :to="{ name: 'home' }"><i class="fa-solid fa-house-chimney"></i> Home</router-link>
  </li>
  <li class="nav-item">
    <router-link class="nav-link" :to="{ name:'about' }"><i class="fa-solid fa-circle-info"></i> About</router-link>
  </li>
  <li class="nav-item">
    <router-link class="nav-link" :to="{ name:'projects' }"><i class="fa-solid fa-layer-group"></i> Projects</router-link>
  </li>
  <li class="nav-item">
    <router-link class="nav-link" :to="{ name:'contacts' }"><i class="fa-solid fa-address-book"></i> Contacts</router-link>
  </li>
</ul>
  </header>
</template>

<style lang="scss" scoped>
@use "../scss/partials/variables" as *;

header {
margin-top: 20px;
.router-link-exact-active {
  color: rgb(0, 255, 4);
}
}
</style>
