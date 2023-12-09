<script>

import axios from "axios"
import { store } from '../data/store';
import Navigator from '../components/partials/Navigator.vue';
import Loader from "../components/partials/Loader.vue";
import Main from "../components/Main.vue";

export default {
name: 'Projects',
components: {
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
      this.isLoaded = false;
      axios.get(endpoint)
        .then(res => {
          this.isLoaded = true;
          //chiamata API di projectList
          store.projectsList = res.data.data;
          console.log(store.projectsList);
          //chiamata API links dell'oggetto paginator
          store.paginator.links = res.data.links;
          console.log(store.paginator.links);
          //chiamata API firstPageUrl dell'oggetto paginator
          store.paginator.firstPageUrl = res.data.first_page_url;
          console.log(store.paginator.firstPageUrl);
          //chiamata API lastPageUrl dell'oggetto paginator
          store.paginator.lastPageUrl = res.data.last_page_url;
          console.log(store.paginator.lastPageUrl);
          //chiamata API currentPage dell'oggetto paginator
          store.paginator.currentPage = res.data.current_page;
          console.log(store.paginator.currentPage);
          //chiamata API lastPage dell'oggetto paginator
          store.paginator.lastPage = res.data.last_page;
          console.log(store.paginator.lastPage);
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
    @callApi="getApi"
  />
</template>



<style lang="scss" scoped>
.container {
  margin-top: 30px;
}
</style>