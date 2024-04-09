<template>
    <div class="main" :style="{ height: `${props.height}px`, width: `${props.width}px`, transform: `rotate(${props.rotation}deg)` }">
        <div class="shadow">
            <img :src="props.imageSource" :alt="props.imageSource" >
            <img :src="`../${props.imageSource}`" :alt="props.imageSource" >
            <h2>{{ props.title }}</h2>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
    imageSource : String,
    title: String,
    height: String,
    width: String,
    rotation: String
});

</script>

<style lang="css" scoped>

.shadow {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: #313131;
    border-radius: 20px;
    box-shadow: 0 4px 10px 3px #00ff0090; /* x-ofset | y-ofset | blurr | spread | color*/
    position: relative;
    transition: 0.4s;
}

.main:hover .shadow { /* Apply box-shadow on hover */
    box-shadow: 0 4px 10px 7px #00FF00;
    transition: 0.1s;
}

img{
    height: 90;
    width: 90;
    object-fit: contain;
}

h2 {
 color: #00FF0070;
 text-shadow: 0 4px 4px  #00000050; /* x-ofset | y-ofset | blurr | spread | color*/
 font-size: 36px;
 position: fixed;
 bottom: 20px;
}

.photo{
    height: 90px;
    width: 90px;

}

@media (max-width: 1300px) {
    .main {
        width: 230px !important; 
        height: 240px !important;
        transform: rotate(0deg) !important;
        margin: 20px;
    }
    h2 {
        color: #00FF0070;
        text-shadow: 0 4px 4px  #00000050; /* x-ofset | y-ofset | blurr | spread | color*/
        font-size: 24px;
        position: fixed;
        bottom: 20px;
    }

}

@media (max-width: 600px) {
    .main {
        margin: 20px 0px;
    }

}
</style>