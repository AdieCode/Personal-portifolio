<template>
    <div class="container" @click="goToMainContact" :style="{ '--text-content': `'${props.text}'`, '--transition-duration': `${props.delayDuration}s` }"> <h1>{{ props.text }}</h1> </div>
</template>

<script setup>
import { useRouter } from 'vue-router';
const router = useRouter()

const props = defineProps({
    text: String,
    link: String,
    delayDuration: { type: Number, default: 0.3 } 
})

const goToMainContact = () => {
    console.log(props.link)
    if (props.link.includes('http://') || props.link.includes('https://')) {
        // It's an external link, open in a new tab
        window.open(props.link, '_blank');
    } else {
        // It's an internal link, use Vue Router
        router.push(props.link);
    }
}

</script>

<style lang="css" scoped>

.container{
    width: 76%;
    margin: 20px;
    margin-inline: auto;
    padding: 40px 20px;
    border-radius: 10px;
    position: relative; /* Add position relative */
    overflow: hidden;
    background-color: #000000;
    border: 2px solid #000000;
    color: #00FF00;
    text-align: center;
    font-size: 46px;
    transition: 0.5s;
    cursor:pointer;
    opacity: 0;
    animation: conainerVisaible 0.3s var(--transition-duration) forwards;
}

.container h1{
    font-size: 46px;
    font-weight: 300;
}

.container::after {
    content: var(--text-content);
    position: absolute;
    top: 0;
    left: 0;
    width: 0;
    height: 100%;
    color: #00000000;
    background-color: #00FF00;
    transition: width 0.3s ease; /* Transition for width property */
    display: flex;
    justify-content: center;
    align-items: center;
}

.container:hover::after {
    font-weight: 400;
    font-size: 46px;
    color: #000000;
    animation: textVisible 0.3s forwards;
    width: 100%; /* Width expands to 100% on hover */
}

@keyframes textVisible {
    0%{
        color: #00000022;
    }
    50%{
        color: #00000022;
    }
    100%{
        color: #000000;
    }
}

@keyframes conainerVisaible {
    0%{
        opacity: 0;
    }
    100%{
        opacity: 100%;
    }
}



</style>