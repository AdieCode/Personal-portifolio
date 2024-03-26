<template>
    <div class="card"  @mousemove="mousePositionOnCard" :style="{ left: `${positionX}px` }" ref="containerRef" >
        <div class="photo">

        </div>
        <div class="info">
            <h1>hello there</h1>
            <p> this is a paragraph</p>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const positionX = ref(0);
const containerRef = ref()
let containerLeft = 0;
const getThecurrent = ref(false)

const props = defineProps({
    posX: Number,
    grabbed : Boolean
})

watch(() => props.grabbed, (newVal, oldVal) => {
    getThecurrent.value = props.grabbed;
})

watch(() => props.posX, (newVal, oldVal) => {
    if (props.grabbed){
  
        if (containerRef.value && getThecurrent.value) {
            const computedStyle = window.getComputedStyle(containerRef.value);
            containerLeft = parseInt(computedStyle.getPropertyValue('left').replace('px', ''));
            getThecurrent.value = false
            console.log(getThecurrent.value)
        }
        positionX.value = containerLeft + props.posX;
    }
})


</script>

<style lang="css" scoped>
.card{
    width: 500px;
    height: 400px;
    background-color:#373737;
    border-radius: 10px;
    position: relative;
    cursor: grab;
    margin: 20px;
    pointer-events: none;
    display: flex;
    justify-content: center;
    align-items: center;
}

.photo{
    width: 100px;
    height: 100px;
    margin: 40px;
    background-color: aqua;
}

.info{
    width: 400px;
    height: 400px;
    color: #fff;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}


</style>