<script>

import Header from './components/Header.vue';

export default {
  name: "App",
  components: {
    Header,
  },
  data() {
    return {
    }
  },

}
</script>

<template>
  <Header />

  <Router-view />
</template>

<style lang="scss">
@use "./scss/main.scss";
</style>
