<template>
    <div>
        <!-- project info in documentation style -->
        <h1>Command Controled Bot # <span class="subtitle">Personal Project</span></h1>
        <animated-paragraph :paragraph="sentence1"/>
        
        <!-- description of solution -->
        <h2 :style="{animationDelay: `${(sentence1.split(' ').length) * 0.02}s`}" >My Solution</h2>
        <animated-paragraph :paragraph="sentence2" :extraDelayDuration="sentence1.split(' ').length"/>

        <!-- code snippet -->
        <h3 :style="{animationDelay: `${((sentence1+sentence2).split(' ').length) * 0.02}s`}" >Example Code:</h3>
        <div class="code-snippet" :style="{animationDelay: `${((sentence1+sentence2).split(' ').length) * 0.02}s`}">                
            <div class="line"><span class="purple-text">const</span> Bot <span class="cyan-text">=</span> <span class="red-text">require</span>(<span class="cyan-text">'../modules/bot'</span>); </div>                     
            <div class="line"><span class="purple-text">const</span> myBot <span class="cyan-text">=</span> <span class="purple-text">new</span> Bot;   </div>    
            <br>                 
            <div class="line"><span class="purple-text">function</span> <span class="red-text">askWord</span>(){  </div>                     
            <div class="line-2">myBot.<span class="red-text">next</span>()  </div>                     
            <div class="line-2"><span class="purple-text">return</span>  <span class="cyan-text">'please enter a word: '</span>;</div>  
            <div class="line">}</div>    
            <br> 
            <div class="line"> <span class="purple-text">function</span> <span class="red-text">repeatWord</span>(){ </div>   
            <div class="line-2"> <span class="purple-text">const</span> word <span class="cyan-text">=</span> myBot.<span class="cyan-text">userInput</span>; </div> 
            <br>
            <div class="line-2"> <span class="purple-text">if</span>  (<span class="red-text">isOnlyWord</span>(word)){ </div> 
            <div class="line-3"> myBot.<span class="red-text">next</span>() </div> 
            <div class="line-3"> <span class="purple-text">return</span> <span class="cyan-text">`your word was: ${word}`</span></div> 
            <div class="line-2"> } <span class="purple-text">else</span>  { </div> 
            <div class="line-3"> <span class="purple-text">return</span>  <span class="cyan-text">'Sorry could you please enter only a word'</span></div> 
            <div class="line-2">}</div>  
            <div class="line">}</div>  
            <br>
            <div class="line"> myBot.<span class="red-text">addStep</span>(<span class="cyan-text">'/word'</span>,askWord); </div>  
            <div class="line"> myBot.<span class="red-text">addStep</span>(<span class="cyan-text">'/word'</span>,repeatWord); </div>
            <br>
            <div class="line"><span class="purple-text">const</span> wordToGive <span class="cyan-text">=</span> <span class="cyan-text">'Hello'</span>;</div>
            <br>
            <div class="line"> console.<span class="red-text">log</span>(<span class="cyan-text">'\nConversation with bot'</span>) ;</div>  
            <div class="line"> console.<span class="red-text">log</span>(<span class="cyan-text">'========================='</span>)  ;</div>  
            <div class="line"> console.<span class="red-text">log</span>(<span class="cyan-text">`bot: </span>${myBot.<span class="red-text">respond</span>(<span class="cyan-text">'/word'</span>)}<span class="cyan-text">`</span>);</div>
            <div class="line"> console.<span class="red-text">log</span>(<span class="cyan-text">'------------------------'</span>);</div> 
             
            <div class="line"> console.<span class="red-text">log</span>(<span class="cyan-text">`user: </span>${wordToGive}<span class="cyan-text">`</span>);</div>  
            <div class="line"> console.<span class="red-text">log</span>(<span class="cyan-text">'------------------------'</span>);</div>  
            <div class="line"> console.<span class="red-text">log</span>(<span class="cyan-text">`bot: </span>${myBot.<span class="red-text">respond</span>(wordToGive)}<span class="cyan-text">`</span>);</div>  
            <div class="line">console.<span class="red-text">log</span>(<span class="cyan-text">'========================='</span>);</div>      
        </div>

        <!-- code snippet -->
        <h3 :style="{animationDelay: `${((sentence1+sentence2).split(' ').length) * 0.02}s`}" >Example Output:</h3>
        <div class="code-snippet" :style="{animationDelay: `${((sentence1+sentence2).split(' ').length) * 0.02}s`}">
            Conversation with bot    <br>
            =========================<br>
            bot: please enter a word:<br>
            ------------------------ <br>
            user: Hello              <br>
            ------------------------ <br>
            bot: your word was: Hello<br>
            =========================
        </div>

        <br>
        <br>

        <!-- description of solution -->
        <animated-paragraph :paragraph="sentence3" :extraDelayDuration="(sentence1+sentence2).split(' ').length"/>
        <animated-paragraph :paragraph="sentence4" :extraDelayDuration="(sentence1+sentence2+sentence3).split(' ').length"/>
        
        <!-- skills and Technologies used -->
        <h2 :style="{animationDelay: `${(sentence1+sentence2+sentence3+sentence4).split(' ').length * 0.02 + 0.02}s`}" >Technical Skills and Technologies Utilized</h2>
        <animated-paragraph :paragraph="sentence5" :extraDelayDuration="(sentence1+sentence2+sentence3+sentence4).split(' ').length"/>
        <div class="tags" :style="{animationDelay: `${(sentence1+sentence2+sentence3+sentence4).split(' ').length  * 0.02 + 0.02}s`}">
            <tags :items="tags_list"/>
        </div>

        <!-- the why paragraph -->
        <h2 :style="{animationDelay: `${((sentence1+sentence2+sentence3+sentence4+sentence5).split(' ').length) * 0.02}s`}" >Why Make This?</h2>
        <animated-paragraph :paragraph="sentence6" :extraDelayDuration="(sentence1+sentence2+sentence3+sentence4+sentence5).split(' ').length"/>

        <!-- redirection and bottom space -->
        <redirect-button link="https://github.com/AdieCode/CCB--command-controled-bot" text="Checkout reposetory" :delayDuration="(sentence1+sentence2+sentence3+sentence4+sentence5).split(' ').length * 0.02"/>
        <redirect-button link="/#contact" text="Contact me"  :delayDuration="(sentence1+sentence2+sentence3+sentence4+sentence5).split(' ').length * 0.02"/>
        <div class="the-bottom"></div>

    </div>
</template>

<script setup>
import {ref } from 'vue'; 

let previousIndex = 0;

const sentence1 = "This is a bot that can be preprogrammed by a developer with logic to handle text provided by a user.";

const sentence2 = "This bot needed an easy way to be programmed by any developer. My solution to this is by providing the bot with a command and then a function associated " +
                  "with that command. This could be done multiple times and the order in which the functions were added to a command is the order in which they would be executed. "+
                  "It should also be able to receive multiple functions at once, and they would execute in the order in which they were passed in.";

const sentence3 = "Now you are probably wondering, how did the bot handle these commands and functions passed to it? Well, it checks the command passed to it and sees if the command " +
                  "already exists in an object called CommandSteps and adds the function passed if it does exist, and if not it will add the command and then add the function to the object. "+
                  "But you cannot just add any function to the bot; there is a condition when creating a function. The bot has a built-in function called next() which " +
                  "tells the bot to move on to the next function. This built-in function should be included in each function passed to the bot.";
                  
const sentence4 = "If not, then the bot will not execute the next function in the array " + 
                  "or any other further existing functions in the array. This helps the developer to add their own logic to control when the bot should move on to the next function based on the user input. "+
                  "Speaking of user input, the bot does not pass the user input into the functions; you can access the user input with a getter function called userInput.";
                  
const sentence5 = "These are the skills and technologies I have used throughout the development of this project"
const tags_list = ['JavaScript', 'Debugging & Troubleshooting', 'Version Control (Git)', 'OOP'];

const sentence6 = "Now why would I do this? Well, in another project I worked on, I had to create a chat bot. When I went back to look at the " +
                  "bot's code that handled the user text, I thought to myself, 'there has to be a better way to write this.' So I sat down and came up " +
                  "with this.";

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

.code-snippet{
    width: 73%;
    padding: 40px;
    margin: auto;
    border-radius: 20px;
    background-color: #181818;
    color: #00FF00;
    margin-top: 20px;
    opacity: 0%;
    animation: showHeading 0.3s forwards;
}

.line{
    margin: 5px 0px;
}

.line-2{
    margin: 5px 50px;
}

.line-3{
    margin: 5px 100px;
}

.purple-text{
    color: #9747FF;
}

.red-text{
    color:#FFA500 ; 
}

.cyan-text{
    color:#00FFFF ; 
}

.tags{
    opacity: 0%;
    animation: showHeading 0.3s forwards;
}
</style>