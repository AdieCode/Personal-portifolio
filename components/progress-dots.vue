<template>
    <div class="container" :style="{ top: `${props.yPos || 0}%` }">
      <div v-for="(item, index) in totalProgress" :key="index">
        <div
          v-if="index === props.currentProgress"
          class="circle selected"
        ></div>
        <div v-else class="circle"></div>
      </div>
    </div>
</template>

<script setup>
const props = defineProps({
    currentProgress: Number,
    totalProgress: Number,
    yPos: Number
})
</script>

<style lang="css" scoped>
.container{
    display: flex;
    left: 50%;
    position: absolute;
    transform: translate(-50%, -50%);
}

.circle{
    height: 20px;
    width: 20px;
    border-radius: 100%;
    background-color: #373737;
    margin: 6px;
    animation: unselected 0.6s;
}

.selected{
    background-color: #00FF00;
    animation: selected 0.6s;
}

@keyframes selected {
  0% {
    background-color: #373737;
  }
  100% {
    background-color: #00FF00;
  }
}

@keyframes unselected {
  0% {
      background-color: #00FF00;
    }
    100% {
      background-color: #373737;
  }
}


</style>