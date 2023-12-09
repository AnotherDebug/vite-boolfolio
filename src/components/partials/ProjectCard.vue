<script>
export default {
  name: 'ProjectCard',
  props: {
    item: Object,
  },
  
}
</script>

<template>
  <div class="card m-auto mb-5  bg-body-secondary " style="width: 25rem;">

    <div class="card-body">
      <h5 class="card-title"><strong>Project:</strong> {{ item.name }}</h5>
      <p class="card-text"><strong>Type:</strong> {{ item.type.name }}</p>
      <!-- <p 
        class="card-text"><strong>Technologies:</strong> <span 
          v-for="technology in item.technologies"
          :key="technology.id">{{ item.technologies.map(tech => tech.name).join(', ') }}</span>
      </p> -->
      <router-link :to="{ name: 'details', params:{ slug: item.slug } }" class="btn btn-primary">Details <i class="fa-solid fa-square-arrow-up-right fa-rotate-90"></i></router-link>

    </div>
  </div>
</template>

<style lang="scss" scoped></style>
