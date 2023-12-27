<script>
import axios from 'axios'
import { store } from '../data/store'

export default {
    name: 'Details',
    data() {
        return {
            store,
            slug: '',
            project: {},
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
        <h1 class="text-center mb-5">Project Details</h1>
        <div class="card mb-3 m-auto" style="max-width: 900px;">
            <div class="row g-0">
                <div class="col-md-4">
                    <img :src="project.image" class="rounded-start w-100 object-fit-cover" :alt="project.image_original_name">
                </div>
                <div class="col-md-8">
                    <div class="card-body">
                        <h5 class="card-title"><strong>Title: </strong>{{ project.name }}</h5>
                        <p class="card-text"><strong>Date start: </strong>{{ project.date_start }}</p>
                        <p class="card-text"><strong>Type:</strong> {{ project.type?.name }}</p>
                        <p class="card-text"><strong>Technologies:</strong> <span 
                            v-for="technology in project.technologies"
                            :key="technology.id">{{ project.technologies.map(tech => tech.name).join(', ') }}</span>
                        </p>
                        <p class="card-text"><strong>Description: </strong><span v-html="project.description"></span></p>
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