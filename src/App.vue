<script>

import Header from "./components/Header.vue"
import Main from "./components/Main.vue"
import axios from "axios"
import { store } from "./data/store"

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  methods:{
    getApi() {
      axios.get(store.apiUrl + 'projects')
      .then(res => {
        store.projectsList = res.data;
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

<Header/>

<Main/>

</template>

<style lang="scss">
@use "./scss/main.scss";
</style>
