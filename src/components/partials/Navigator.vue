<script>
import { store } from '../../data/store';

export default {
    name: 'Navigator',
    props: {
        links: Array,
    },
    data() {
        return {
            store,
        }
    },
    methods: {
        callApi(linkUrl) {
            //il this lo uso perche lo genero dal methods
            this.$emit('callApi', linkUrl)
        }
    },
}
</script>


<template>
    <div class="paginate d-flex justify-content-center">
        <button v-for="link in store.links" 
        :key="link.label" 
        v-html="link.label"
        class="btn btn-primary m-1 px-3 "
        :disabled="link.active || !link.url"
        @click="callApi(link.url)"
        ></button>
    </div>
</template>


<style lang="scss" scoped></style>