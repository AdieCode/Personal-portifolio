<template>
    <div>
        <h1>Personal Budget Manager API # <span class="subtitle">Personal Project</span></h1>
        <div class="sentence">
            <div v-for="(word, index) in wrapWordsInDivs(sentence1)" :key="index"  class="word animated-word" :style="{ animationDelay: `${index * 0.02}s`,opacity: '0' }" >
                {{ word }}
            </div>
        </div>
        <!-- <code-snippet/> -->
        <redirect-button/>

    </div>
</template>

<script setup>

const sentence1 = 'This API allows users to manage their personal budgets by creating envelopes for different expense categories and allocating budgets to each envelope. Users can perform various operations such as creating, updating, deleting envelopes, transferring funds between envelopes, and depleting budgets.'
function wrapWordsInDivs(sentence) {
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
.the-bottom{
    width: 100%;
    height: 110px;
}

.sentence{
    width: 80%;
    margin: auto;
    margin-bottom: 30px;
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
    font-size: 40px;
    position: relative;
    opacity: 0%;
    animation: showHeading 0.3s forwards;
}

.container h2{
    width: 80%;
    margin-inline: auto;
    margin-top: 40px;
    margin-bottom: 15px;
    color: #FFF;
    text-shadow:  0px 4px 4px #000000a2;
    font-size: 36px;
    position: relative;
    opacity: 0%;
    animation: showHeading 0.3s forwards;
}

.container h3{
    width: 80%;
    margin-inline: auto;
    margin-top: 30px;
    padding-left: 40px;
    font-weight: 500;
    margin-bottom: 15px;
    color: #FFF;
    font-size: 30px;
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
    padding-left: 10px;
    padding-bottom: 10px;
    transition: 3s;
    cursor: default;
}

.word:hover{
    color: #00FF00;
    transition: 0s;
}

.symbol{
    padding: 0px;
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

</style>