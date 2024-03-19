<template>
    <nuxt-link :to="props.topId">
        <div class="container">
        </div>
    </nuxt-link>
</template>

<script setup>

const props = defineProps({
    topId: String
})

</script>

<style lang="css" scoped>
.container{
    height: 48px;
    width: 48px;
    border-radius: 100%;
    background-color: #00FF00;
    position: fixed;
    bottom: 20px;
    right: 20px;
    z-index: 4px;
}
</style>