<script>
export default {
    name: 'Loader'
}
</script>


<template>
    <div class="loading d-flex flex-column align-items-center justify-content-center">
        <h1>Loading....</h1>

        <span class="loader"></span>
    </div>
</template>


<style lang="scss" scoped>

@use '../../scss/partials/variables' as *;

.loading {   

    h1 {
        
        color: $white-color;
    }

    height: 100vh;

    background-image: url('/public/img/istockphoto-1224500457-612x612.jpg');

    background-size: contain;

    background-size: 100%;

    background-repeat: no-repeat;

    background-position: 50% 0;

    .loader {
        width: 350px;
        height: 12px;
        display: inline-block;
        background: rgba(255, 255, 255, 0.15);
        position: relative;
        overflow: hidden;
    }

    .loader::after {
        content: '';
        width: 0%;
        height: 12px;
        background-color: #9f2a2a;
        background-image: linear-gradient(45deg, rgba(0, 0, 0, 0.25) 25%, transparent 25%, transparent 50%, rgba(0, 0, 0, 0.25) 50%, rgba(0, 0, 0, 0.25) 75%, transparent 75%, transparent);
        background-size: 30px 30px;
        position: absolute;
        top: 0;
        left: 0;
        box-sizing: border-box;
        animation: animFw 1s ease-in infinite;
    }

    @keyframes animFw {
        0% {
            width: 0;
        }

        100% {
            width: 100%;
        }
    }

}
</style>