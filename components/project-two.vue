<template>
    <div>
        <!-- project info in documentation style -->
        <h1>Command controled bot # <span class="subtitle">project type</span></h1>
        <div class="sentence">
            <div v-for="(word, index) in wrapWordsInDivs(sentence1)" :key="index"  :class="{ 'word': true, 'symbol': isSymbol(word) }" :style="{ animationDelay: `${index * 0.02}s`,opacity: '0' }" class="animated-word">
                {{ word }}
            </div>
        </div>

        <h2 :style="{animationDelay: `${(sentence1.split(' ').length) * 0.02}s`}" >My solution</h2>

        <div class="sentence">
            <div v-for="(word, index) in wrapWordsInDivs(sentence2)" :key="index"  :class="{ 'word': true, 'symbol': isSymbol(word) }" :style="{ animationDelay: `${(index + sentence1.split(' ').length) * 0.02}s`,opacity: '0' }" class="animated-word">
                {{ word }}
            </div>
        </div> 

        <div class="sentence">
            <div v-for="(word, index) in wrapWordsInDivs(sentence3)" :key="index"  :class="{ 'word': true, 'symbol': isSymbol(word) }" :style="{ animationDelay: `${(index + sentence1.split(' ').length + sentence2.split(' ').length) * 0.02}s`,opacity: '0' }" class="animated-word">
                {{ word }}
            </div>
        </div>
    </div>
</template>

<script setup>
import {ref } from 'vue';  

const sentence1 = "This is a bot that can be pre programmed by a developer with logic to handel text provided by a user.";
const sentence2 = "This bot needed an easy way to be programmed by any developer. My solution to this is by providing the bot with a command and then a function associated "+
                  "with that command, this could be done multiple times and the order in wich the functions were added to a command is the order in which they will execute."+
                  "It should have also been able to recieve mutliple multiple functions at once but they would execute in the order in which they were passed in.";
const sentence3 = "now you probaly wondering, how did the bot handel these comands and functions passed to it?";

function wrapWordsInDivs(sentence) {
    const wordsArray = [];
    const sentenceSplit = sentence.split(/\b/);
    for (const word of sentenceSplit) {
        if (word.trim() !== '') {
            wordsArray.push(word.trim());
        }
    }
    return wordsArray;
}


function isSymbol(word) {
    const symbols = ['.', ',', '!', '?', '"', "'"]; // Add more symbols if needed
    const lastChar = word.charAt(word.length - 1);
    return symbols.includes(lastChar);
}
</script>

<style lang="css" scoped>
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
    margin-bottom: 10px;
    transition: 3s;
    cursor: default;
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
</style>