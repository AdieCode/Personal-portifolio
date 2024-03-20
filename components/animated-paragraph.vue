<template>
    <div class="paragraph">
        <div v-for="(word, index) in splitParagraph(props.paragraph)" :key="index"  class="word animated-word" :style="{ animationDelay: `${(index + props.extraDelayDuration) * 0.02}s`,opacity: '0' }" >
            {{ word }}
        </div>
    </div>
</template>

<script setup>


const props = defineProps({
    paragraph: { type: String, default: "no sentence passed" } ,
    extraDelayDuration: { type: Number, default: 0 } 
})

function splitParagraph(sentence) {
    const wordsArray = [];
    const sentenceSplit = sentence.split(" ");
    for (const word of sentenceSplit) {
        if (word.trim() !== '') {
            wordsArray.push(word.trim());
        }
    }
    return wordsArray;
}

</script>

<style lang="css" scoped>
.paragraph{
    width: 80%;
    margin: auto;
    margin-top: 10px;
    margin-bottom: 40px;
    font-size: 36px;
    color: aliceblue;
    display: flex;
    flex-wrap: wrap;
}

.animated-word {
    animation: showWord 0s forwards;
}

.word{
    color: #FFF;
    font-size: 24px;
    font-weight: 300;
    margin-left: 10px;
    margin-bottom: 6px;
    cursor: default;
    transition: 3s;
}

.word:hover{
    color: #00FF00;
    transition: 0s;
}

.symbol{
    margin: 0px;
}

@keyframes showWord {
    0%{
        opacity: 0;
    }
    100%{
        opacity: 100%;
    }
}
</style>