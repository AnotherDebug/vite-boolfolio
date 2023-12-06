<script>
export default {
  name: 'ProjectCard',
  props: {
    item: Object,
  },
}
</script>

<template>
  <div class="card m-2" style="width: 18rem;">
 
      <img :src="!!item?.image ? `http://127.0.0.1:8000/storage/` + item.image : 'https://via.placeholder.com/200x200'" 
        	  class="card-img-top" 
            :alt="item.image_original_name">

    <div class="card-body">
      <h5 class="card-title"><strong>Project:</strong> {{ item.name }}</h5>
      <p class="card-text"><strong>Type:</strong> {{ item.type.name }}</p>
      <p 
        class="card-text"><strong>Technologies:</strong> <span 
          v-for="technology in item.technologies"
          :key="technology.id">{{ item.technologies.map(tech => tech.name).join(', ') }}</span>
      </p>
      <p class="card-text"><strong>Description:</strong> <span v-html="item.description"></span></p>
      <!-- <a href="#" class="btn btn-primary">Go somewhere</a> -->

    </div>
  </div>
</template>

<style lang="scss" scoped></style>
