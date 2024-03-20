<template>
    <div>
        <div id="progress-bar-container">
                <div id="progress-bar" :style="{ height: props.scrollPersentage }"></div>
                <div class="info" v-if="props.scrollPersentage !== '100%'">
                    <div>Scroll</div> 
                    <div>Down</div>
                </div>
        </div>
    </div>
</template>

<script setup>
import { ref,defineProps } from 'vue';  

const props = defineProps({
    scrollPersentage: String
})



</script>

<style lang="css" scoped>
#progress-bar-container {
    position: fixed;
    top: 0;
    left: 0;
    width: 5px;
    height: 100%;
    background-color: #313131;
    z-index: 9999;
}

#progress-bar {
    height:0%;
    background-color: #00FF00;
    transition: 0.1s;
    width: 100%;
}

.info{
    position: absolute;
    color: #00FF00;
    font-size: 36px;
    font-weight: 900;
    bottom: 10px;
    left: 0px;
    pointer-events: none;
    animation: info-animate 2s infinite;
}

@keyframes info-animate {
    0%{
        bottom: 10px;
    }

    80%{
        bottom: 30px;
    }

    100%{
        bottom: 10px;
    }
}
</style>