<template>
    <div>
        <!-- project info in documentation style -->
        <!-- project title and description -->
        <h1>Personal portifolio # <span class="subtitle">Personal project</span></h1>
        <div class="sentence">
            <div v-for="(word, index) in wrapWordsInDivs(sentence1)" :key="index"  :class="{ 'word': true, 'symbol': isSymbol(word) }" :style="{ animationDelay: `${index * 0.02}s`,opacity: '0' }" class="animated-word">
                {{ word }}
            </div>
        </div>

        <!-- project screenshots for previewing -->
        <section class="images" :style="{animationDelay: `${(sentence1.split(' ').length) * 0.02}s`}">
            
            <div class="row">
                <div class="img-two img-zoom" @mouseenter="changeCursorSizeBig" >
                    <img src="../images/preview/homepage.png" alt="">
                </div>
            </div>
            <div class="row">
                <div class="img-one img-zoom" @mouseenter="changeCursorSizeBig" >
                    <img src="../images/preview/lang.png" alt="">
                </div>
                <div class="img-one img-zoom" @mouseenter="changeCursorSizeBig" >
                    <img src="../images/preview/contact-portifolio.png" alt="">
                </div>
            </div>
        </section>

        <!-- skills and Technologies used -->
        <h2 :style="{animationDelay: `${(sentence1.split(' ').length) * 0.02 + 0.02}s`}" >Technical Skills and Technologies Utilized</h2>
        <div class="sentence">
            <div v-for="(word, index) in wrapWordsInDivs(sentence2)" :key="index"  :class="{ 'word': true, 'symbol': isSymbol(word) }" :style="{ animationDelay: `${(index + sentence1.split(' ').length) * 0.02}s`,opacity: '0' }" class="animated-word">
                {{ word }}
            </div>
        </div>
        <tags :items="tags_list"/>


        <!-- Personal Reflections or Lessons Learned -->
        <h2 :style="{animationDelay: `${(sentence1.split(' ').length + sentence2.split(' ').length) * 0.02 + 0.02}s`}" >Personal Reflections or Lessons Learned</h2>
        <div class="sentence">
            <div v-for="(word, index) in wrapWordsInDivs(sentence3+sentence4)" :key="index"  :class="{ 'word': true, 'symbol': isSymbol(word) }" :style="{ animationDelay: `${(index + sentence1.split(' ').length + sentence2.split(' ').length) * 0.02}s`,opacity: '0' }" class="animated-word">
                {{ word }}
            </div>
        </div>

        <div class="sentence">
            <div v-for="(word, index) in wrapWordsInDivs(sentence5)" :key="index"  :class="{ 'word': true, 'symbol': isSymbol(word) }" :style="{ animationDelay: `${(index + sentence1.split(' ').length + sentence2.split(' ').length + sentence3.split(' ').length + sentence4.split(' ').length )* 0.02}s`,opacity: '0' }" class="animated-word">
                {{ word }}
            </div>
        </div>


        <div class="the-bottom"></div>
    </div>
</template>

<script setup>
import {ref } from 'vue';  

const sentence1 = "If the customer is very smart, he or she will be able to achieve the desired result. To choose to do whatever pleasures are born of trouble, but this one results in none, so what pain! Let him be the most worthy of these advantages, blinded by sorrows.";
const sentence2 = "These are the skills and technologies I have used throughout the development of this portifolio.";
const sentence3 = "Throughout the development of this portfolio, I have learned a lot of things, like the fact that flexbox is great and that I should really stop setting heights and just let the browser handle it. Lastly, I really hate working with images.";
const sentence4 = "These are just some of the things that I have learned, but there are just too many to list here.";
const sentence5 = "Another thing I have learned is that things can get messy real fast. No matter how many times I tried to plan ahead, I always ended up with something messy. And no matter how hard you try, you are always going to overcomplicate something. But I eventually got really good at giving some readability to the code and making it more understandable.";


const tags_list = ['Vue.js', 'Nuxt.js', 'JavaScript', 'HTML', 'CSS', 'Responsive Design', 'Vue Composition API', 'Conditional Rendering', 'Debugging & Troubleshooting', 'Version Control (Git)',  'UI/UX Design Principles', 'Figma'];

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

.the-bottom{
    width: 100%;
    height: 110px;
}
.sentence{
    width: 80%;
    margin: auto;
    margin-bottom: 50px;
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

.images{
    width: 80%;
    margin: auto;
    margin-top: 30px;
    margin-bottom: 80px;
    opacity: 0%;
    position: relative;
    animation: showimg 0.2s forwards;
}

.row{
    display: flex;
    justify-content: space-between;
}

.img-zoom:hover img{
    transform: scale(1.1); 
    transition: 0.6s;
}
.img-one{
    width: 47%;
    height: auto;
    overflow: hidden;
    border-radius: 20px;
    border: 2px solid #00FF00;
    /* box-shadow:  0px 0px 6px #00FF00; */
}

img{
    transition: 0.4s;
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    margin: auto;
}


.img-two{
    margin-bottom: 50px;
    width: 100%;
    height: auto;
    overflow: hidden;
    border-radius: 20px;
    border: 2px solid #00FF00;
    /* box-shadow:  0px 0px 6px #00FF00; */
}


@keyframes showimg {
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
