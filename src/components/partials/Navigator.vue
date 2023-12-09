<script>
import { store } from '../../data/store';

export default {
    name: 'Navigator',

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
    <div class="paginate d-flex justify-content-center ">

        <button
            @click="callApi(store.paginator.firstPageUrl)"
            :disabled="store.paginator.currentPage == 1"
            class="btn btn-primary m-1 px-3 ">
            <i class="fa-solid fa-backward-step"></i>
        </button>

        <button v-for="link in store.paginator.links" 
            :key="link.label" 
            v-html="link.label"
            class="btn btn-primary m-1 px-3 "
            :disabled="link.active || !link.url"
            @click="callApi(link.url)">
        </button>

        <button
            @click="callApi(store.paginator.lastPageUrl)"
            :disabled="store.paginator.lastPage == store.paginator.currentPage"
            class="btn btn-primary m-1 px-3 ">
            <i class="fa-solid fa-forward-step"></i>
        </button>
    </div>
</template>


<style lang="scss" scoped></style>