<script>

import Header from "./components/Header.vue"
import Main from "./components/Main.vue"
import axios from "axios"
import { store } from "./data/store"
import Loader from "./components/partials/Loader.vue"
import Navigator from "./components/partials/Navigator.vue"

export default {
  name: "App",
  components: {
    Header,
    Main,
    Loader,
    Navigator,
  },
  data() {
    return {
      isLoaded: false,
    }
  },
  methods: {
    getApi(endpoint) {
      axios.get(endpoint)
        .then(res => {
          this.isLoaded = true;
          store.projectsList = res.data.data;
          console.log(store.projectsList);
          store.links = res.data.links;
          console.log(store.links);
        })
        .catch(e => {
          console.log(e);
        });
    },
  },
  mounted() {
    this.getApi(store.apiUrl + 'projects');
  }
}
</script>

<template>
  <Loader v-if="!isLoaded" />

  <Main v-else />
  <Navigator 
    :links="links"
    @callApi="getApi"/>
</template>

<style lang="scss">
@use "./scss/main.scss";
</style>
