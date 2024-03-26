<template>
    <scroll-progress :scrollPersentage="scrollPercentage"/>
    <div class="container"  ref="scrollContainer" @scroll="updateScrollPercentage" >
            
        <project-one v-if="props.projectNumber === 0" />
        <project-two v-if="props.projectNumber === 1" />
        <project-three v-if="props.projectNumber === 2" />
        <project-four v-if="props.projectNumber === 3" />
        <project-five v-if="props.projectNumber === 4" />
        <project-six v-if="props.projectNumber === 5" />


        <!-- <div class="blur-container"></div> -->
    </div>

</template>

<script setup>
import { ref, watch  } from 'vue';  

const scrollPercentage = ref('0%');
const scrollContainer = ref();
// const mousePosition = ref({ x: 0, y: 0 });
let scrollTopPos = 0;

const props = defineProps({
    projectNumber: Number,
})

function updateScrollPercentage() {
    const container = scrollContainer.value;
    if (!container) return;
    scrollTopPos = container.scrollTop;
    const scrollTop = container.scrollTop;
    const scrollHeight = container.scrollHeight - container.clientHeight;
    scrollPercentage.value = (scrollTop / scrollHeight) * 100 + '%';
}

watch(() => props.projectNumber, (newVal, oldVal) => {
//   console.log(`projectNumber changed from ${oldVal} to ${newVal}`);
  if (scrollContainer.value) {
    scrollContainer.value.scrollTop = 0;
  }
})

function isMobileDevice() {
    // Check if navigator object exists
    if (typeof navigator === 'undefined') {
        return false; // Cannot determine, assume not mobile
    }

    // Check if userAgent property exists
    if ('userAgent' in navigator) {
        const userAgent = navigator.userAgent.toLowerCase();
        const mobileKeywords = ['iphone', 'ipad', 'android', 'blackberry', 'windows phone', 'iemobile'];
        return mobileKeywords.some(keyword => userAgent.includes(keyword));
    } else {
        return false; // Cannot determine, assume not mobile
    }
}


</script>



<style scoped>
.big{
    height: 50px;
    width: 50px;
}

::-webkit-scrollbar {
  width: 0px; 
}

.container{
    width: 70%;
    height: 100%;
    position: relative;
    border-right: 2px solid #00FF00;
    box-shadow: 0 4px 10px 3px #00ff0090; /* x-ofset | y-ofset | blurr | spread | color*/
    bottom: 0px;
    left: 0px;
    background-color: #313131;
    overflow-x: hidden;
    overflow-y: scroll;
    scroll-behavior:auto;
}


.cursor-inner{
    height: 10px;
    width: 10px;
    background-color: #00ff00d7;
    border-radius: 100%;
    transform: translate(-50%,-50%);
    position: absolute;
    pointer-events: none;
    transition: 0s ;
    z-index: 999;
}

.cursor-outer{
    height: 20px;
    width: 20px;
    background-color: #00ff00;
    border-radius: 100%;
    transform: translate(-50%,-50%);
    position: absolute;
    pointer-events: none;
    transition: 0s;
    z-index: 999;
}

.info-container{
    width: 80%;
    margin: auto;
    font-size: 36px;
    color: aliceblue;
    display: flex;
    flex-wrap: wrap;
}

.container h1{
    width: 80%;
    margin-inline: auto;
    margin-top: 40px;
    margin-bottom: 20px;
    color: #FFF;
    text-shadow:  0px 4px 4px #000000a2;
    font-size: 48px;
    position: relative;
    opacity: 0%;
    animation: showHeading 0.3s forwards;
}

.container h2{
    width: 80%;
    margin-inline: auto;
    margin-top: 30px;
    margin-bottom: 15px;
    color: #FFF;
    text-shadow:  0px 4px 4px #000000a2;
    font-size: 36px;
    position: relative;
    opacity: 0%;
    animation: showHeading 0.3s forwards;
}

.animated-word {
    animation: showWord 0s forwards;
}

.word{
    color: #FFF;
    font-size: 24px;
    font-weight: 300;
    margin-left: 10px;
    transition: 3s;
}

.word:hover{
    color: #00FF00;
    transition: 0s;
}

.symbol{
    margin: 0px;
}

.subtitle{
    font-size: 36px;
    color: #00FF00;
}

@keyframes showWord {
    0%{
        opacity: 0;
    }
    100%{
        opacity: 100%;
    }
}

@keyframes showHeading {
    0%{
        left: -20px;
        opacity: 0;
    }
    50%{
        opacity: 100%;
    }
    80%{
        left: 4px;
    }
    100%{
        left: 0px;
        opacity: 100%;
    }
}

.container img:hover .cursor-outer {
  height: 40px;
  width: 40px;
}

.blur-container{
    position: fixed;
    left: 0px;
    bottom: 0px;
    width: 70%;
    height: 100px;
    background-color: #2626263d;
    backdrop-filter: blur(10px);
}
</style>