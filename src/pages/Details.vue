<script>
import axios from 'axios'
import { store } from '../data/store'

export default {
    name: 'Details',
    data() {
        return {
            store,
            slug: '',
            project: '',
        }
    },
    methods: {
        getProjectApi(slug) {
            axios.get(store.apiUrl + 'project/' + slug)
                .then(res => {
                    this.project = res.data;
                    console.log(this.project);
                }).catch(e => {
                    console.log(e);
                })
        }
    },
    mounted() {
        this.slug = this.$route.params.slug;
        this.getProjectApi(this.slug);
    }
}
</script>


<template>
    <div class="container">
        <h1>Details</h1>
        <div class="card mb-3" style="max-width: 540px;">
            <div class="row g-0">
                <div class="col-md-4">
                    <img src="..." class="img-fluid rounded-start" alt="...">
                </div>
                <div class="col-md-8">
                    <div class="card-body">
                        <h5 class="card-title">Card title</h5>
                        <p class="card-text">This is a wider card with supporting text below as a natural lead-in to
                            additional content. This content is a little bit longer.</p>
                        <p class="card-text"><small class="text-body-secondary">Last updated 3 mins ago</small></p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>



<style lang="scss" scoped>
.container {
    margin-top: 30px;
}
</style>