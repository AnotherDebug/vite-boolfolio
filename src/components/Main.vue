<script>
import ProjectCard from './partials/ProjectCard.vue';

export default {
  name: 'Main',
  components: {
    ProjectCard
  }
}
</script>

<template>
  <main class="container">

    <div class="row p-5">
      <div class="col d-flex  flex-wrap ">

        <ProjectCard/>

      </div>
    </div>


    

  </main>
</template>

<style lang="scss" scoped>
.container {
  margin-top: 20px;
}
</style>
