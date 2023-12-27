<script>

import axios from 'axios';
import { store } from '../../data/store';
import Loader from './Loader.vue';

export default {
    name: 'ContactForm',
    components: {
        Loader
    },
    data() {
        return {
            name: '',
            email: '',
            message: '',
            success: false,
            errors: {
                name: [],
                email: [],
                message: [],
            },
            isLoaded: false,
        }
    },
    methods: {
        sendForm() {
            console.log('invio form');
            this.isLoaded = true;
            const formData = {
                name: this.name,
                email: this.email,
                message: this.message
            }

            axios.post(store.apiUrl + 'send-email', formData)
                .then(res => {
                    this.success = res.data.success;
                    this.isLoaded = false;
                    console.log(res.data);
                    if (!this.success) {
                        this.errors = res.data.errors;
                        console.log(this.errors);
                    }
                }).catch(e => { console.log(e); });
        }
    },
}
</script>


<template>
    <div class="container">
        <form v-if="!this.success" @submit.prevent="sendForm()">
            <div v-if="!isLoaded">
                <div class="mb-3">
                    <label for="name" class="form-label">Name</label>
                    <input v-model="name" type="text" class="form-control" id="name" name="name">
                    <span v-for="error in errors.name" :key="error" class="badge text-bg-danger">{{ error }}</span>
                </div>
                <div class="mb-3">
                    <label for="email" class="form-label">Email address</label>
                    <input v-model="email" type="email" class="form-control" id="email" name="email">
                    <span v-for="error in errors.email" :key="error" class="badge text-bg-danger">{{ error }}</span>
                </div>
                <div class="mb-3">
                    <label for="message" class="form-label">Message:</label>
                    <textarea v-model="message" class="form-control" id="message" rows="5" name="message"></textarea>
                    <span v-for="error in errors.message" :key="error" class="badge text-bg-danger">{{ error }}</span>
                </div>
                <button type="submit" class="btn btn-primary">Invia</button>
            </div>
            <Loader v-else />
        </form>
        
        <span v-else class="badge text-bg-success">Email inviata correttamente</span>
    </div>
</template>



<style lang="scss" scoped>
.container {
    margin-top: 30px;
}
</style>