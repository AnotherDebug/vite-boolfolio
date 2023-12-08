<script>

import Header from "./components/Header.vue"
import Main from "./components/Main.vue"
import axios from "axios"
import { store } from "./data/store"
import Loader from "./components/partials/Loader.vue"

export default {
  name: "App",
  components: {
    Header,
    Main,
    Loader,
  },
  data() {
    return {
      isLoaded: false,
    }
  },
  methods: {
    getApi() {
      axios.get(store.apiUrl + 'projects')
        .then(res => {
          this.isLoaded = true;
          store.projectsList = res.data.data;
          console.log(store.projectsList);
        })
        .catch(e => {
          console.log(e);
        });
    },
  },
  mounted() {
    this.getApi();
  }
}
</script>

<template>
  <Loader v-if="!isLoaded" />

  <Main v-else />
</template>

<style lang="scss">
@use "./scss/main.scss";
</style>
