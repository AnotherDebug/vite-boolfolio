<script>
import ProjectCard from './partials/ProjectCard.vue'
import { store } from '../data/store'

export default {
  name: 'Main',
  components: {
    ProjectCard
  },
  data() {
    return {
      store
    }
  }
}
</script>

<template>
  <main class="container">

    <h1 class="text-center">I miei progetti</h1>

    <div class="row p-5">
      <div class="col d-flex  flex-wrap ">

        <ProjectCard
        v-for="card in store.projectsList"
        :key="card.id"
        :item="card"
        />

      </div>
    </div>


    

  </main>
</template>

<style lang="scss" scoped>
.container {
  margin-top: 20px;
}
</style>
