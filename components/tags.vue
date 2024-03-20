<template>
    <div class="tags">
        <div v-for="(tag, index) in props.items" :key="index"  class="tag" >
            {{ tag }}
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';  
const props = defineProps({
    items: Array
})
</script>

<style lang="css" scoped>
.tags{
    width: 80%;
    margin: auto;
    margin-bottom: 20px;
    display: flex;
    /* justify-content: center; */
    flex-wrap: wrap;
}

.tag{
    padding: 20px 20px;
    margin: 10px;
    background-color: #181818;
    color: #00FF00;
    font-weight: 800;
    border: 2px solid #00FF00;
    border-radius: 10px;
    text-align: center;
    transition: 0.3s;
    cursor:default;
}

.tag:hover{
    box-shadow:  0px 0px 6px 4px #00FF00;

}
</style>