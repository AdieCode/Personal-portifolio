<template>
    <div class="container">
        <h1 :id="color">{{ word }}</h1>
        <button @click="changeLabel">press me</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';
let word = ref('Label1');
let color = ref('white')

const props = defineProps({
    changeText : Boolean,
    changeColor : Boolean
})

const changeLabel = () =>{
    // word.value = props.changeText ? 'Hello World!' : 'Label1';
    // color.value = props.changeColor ? 'purple' : 'white';
    console.log(props.changeText)
    if (props.changeText){
        if (word.value === 'Label1'){
            word.value = 'Hello World!';
        } else {
            word.value = 'Label1';
        }
    }

    if (props.changeColor){
        if (color.value === 'white'){
            color.value = 'purple';
        } else {
            color.value = 'white';
        }
    }
}
</script>

<style lang="css" scoped>
.container{
    height: 475px;
    width: 362px;
    min-width: 362px;
    background-color: #313131;
    box-shadow: 0px 0px 10px 3px #00ff00a2; /* x-ofset | y-ofset | blurr | spread | color*/
    border-radius: 20px;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
    margin: 20px;
}

h1 {
    font-size: 48px;
    color: #ffffff;
}

button {
    height: 72px;
    width: 132px;
    border-radius: 10px;
    border: 2px solid #00ff00;
    background-color: #313131;
    color: #00ff00;
    font-size: 24px;
    cursor: pointer;
    transition: 0.1s;
}

button:hover{
    border: 2px solid #000000;
    background-color: #00ff00;
    color: #000000;
    font-weight: 600;
    transition: 0.1s;
}

#white{
    color: #ffffff;
}

#purple{
    color: #9747ff;
}

@media (max-width: 700px) {
    .container{
        height: 350px;
        min-width: 250px;
        width: 250px;
    }

    h1 {
        font-size: 36px;
        color: #ffffff;
    }

    button{
        font-size: 20px;
    }
}
</style>