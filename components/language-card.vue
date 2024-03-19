<template>
    <div class="container">
        <div class="shadow">
            <img :src="`/_nuxt/${props.imageSource}`" :alt="props.imageSource" >
            <h2>{{ props.title }}</h2>
        </div>
    </div>
</template>

<script setup>
const props = defineProps({
    imageSource : String
});

</script>

<style scoped>
.container{
    height: 200px;
    width: 200px;
    border-radius: 20px;
    background-color: #313131;
    box-shadow: 0 4px 10px 4px #0000008a; /* x-ofset | y-ofset | blurr | spread | color*/
    display: flex;
    justify-content: center;
    align-items: center;
    transition: 0.5s;
    margin: 20px;
}

.container:hover{
    box-shadow: 0 4px 10px 4px #00ff00b3; /* x-ofset | y-ofset | blurr | spread | color*/
    transition: 0.1s;
}

.container img{
    height: 150px;
    width: 150px;
}

</style>