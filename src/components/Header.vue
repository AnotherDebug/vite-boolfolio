<script>
export default {
  name: 'Header'
}
</script>

<template>
  <header>
    <h1>Projects List</h1>
  </header>
</template>

<style lang="scss" scoped>
@use "../scss/partials/variables" as *;

header {
  background-color: $gray-color;
 
  h1 {
    text-align: center;
    padding-top: 30px;
    height: 120px;
  }
}
</style>
