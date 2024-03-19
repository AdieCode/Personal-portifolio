<template>
        <div class="back-to-main" @click="goToMain">Back</div>
</template>

<script setup>
import { ref } from 'vue';
const router = useRouter()

const goToMain = () => {
  router.push('/');
}

</script>

<style lang="css" scoped>

@keyframes set-height {
    0%{
        height: 20px;
    }
    100%{
        height: 80px;
    }
}

@keyframes set-width {
    0%{
        width: 80px;
    }
    100%{
        width: 130px;
    }
}

@keyframes set-radius {
    0% {
        border-radius: 0px;
    }
    100% {
        border-radius: 10px;
    }
}

@keyframes set-background {
    0% {
        background-color: transparent;
    }
    100% {
        background-color: #181818;
    }
}

@keyframes set-border {
    0% {
        border: 2px solid #181818;
    }
    100% {
        border: 2px solid #00FF00;
    }
}

@keyframes set-font-color {
    0% {
        color: #000000;
    }
    100% {
        color: #00FF00;
    }
}

@keyframes set-font-size {
    100% {
        font-size: 24px;
    }
}

@keyframes set-font-weight {
    0% {
        font-weight: 200;
    }
    100% {
        font-size: 400;
    }
}
.back-to-main{
    position: absolute;
    top: 20px;
    right: 20px;
    z-index: 10;
    cursor: pointer;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #D9D9D9;

    animation: set-height 0.5s forwards,
               set-width 0.5s 0.5s forwards,
               set-radius 0.2s 1s forwards,
               set-border 0.2s 1.2s forwards,
               set-background 0.2s 1.4s forwards,
               set-font-color 0.1s 1.6s forwards,
               set-font-size 0.1s 1.7s forwards,
               set-font-weight 0.2s 1.8s forwards;

}

.back-to-main:hover{ 
    background-color: #00FF00 !important;
    border: 2px solid #000000 !important;
    color: #000000 !important;
}

</style>