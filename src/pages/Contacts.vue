<script>

import ContactForm from '../components/partials/ContactForm.vue';

export default {
  name: 'Contacts',
  components: {
    ContactForm,
  },
}
</script>


<template>
  <div class="container">
    <h1>Contacts</h1>
    <ContactForm />
  </div>
</template>



<style lang="scss" scoped>
.container {
  margin-top: 30px;
}
</style>