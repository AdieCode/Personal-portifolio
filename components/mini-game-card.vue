<template>
    <div class="container">
        <div class="screen">
            <h1>Score : {{ score }}</h1>
            <div class="wall"  v-for="(value, key) in walls" :key="key" :style="{ top: value.y + 'px', left: value.x + 'px', visibility: value.visibility}"></div>
            <div class="player" :style="{ top: player.y + 'px', left: player.x + 'px' }"></div>
            <div class="menu" :style="{ visibility: menu_state }">
                <h2>Score : {{ score }}</h2>
                <button @click="togglePlay">Play</button>
            </div>
        </div>
        

        <div id="buttons-container"> 
            <button @click="moveLeft" id="left"></button>
            <button @click="moveRight" id="right"></button>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted  } from 'vue';

let score = ref(0);
let playing = false;
let menu_state = 'visible';
let counterCounting = false;


let player = ref({
    x: 123,
    y: 240
})

let walls = ref({
    wall1: {
        x: 60,
        y: 30
    },
    wall2: {
        x: 60,
        y: 30
    },
    wall3: {
        x: 60,
        y: 30
    },
    wall4: {
        x: 60,
        y: 30
    },
    wall5: {
        x: 60,
        y: 30
    }
})

const startTimer = () => {
  setInterval(() => {
    if (counterCounting){
        score.value++;
    }
  }, 2000); 
};

const checkCollision = (newX, newY) => {
    for (let wallKey in walls.value) {
        const wall = walls.value[wallKey];
        const wallX = wall.x;
        const wallY = wall.y;

        if (
            newX < wallX + 60 && 
            newX + 60 > wallX &&
            newY < wallY + 20 &&
            newY + 20 > wallY
        ) {

            return true;
        }
    }

    return false;
}

const checkPlayerCollision = (newX, newY) => {

    const playerWidth = 20;
    const playerHeight = 20;

    // Iterate through each wall
    for (let wallKey in walls.value) {
        const wall = walls.value[wallKey];
        const wallX = wall.x;
        const wallY = wall.y;

        // Check for collision between the player and the wall
        if (
            newX < wallX + 60 &&   // Right side of player is to the left of the right side of the wall
            newX + playerWidth > wallX &&   // Left side of player is to the right of the left side of the wall
            newY < wallY + 20 &&   // Bottom side of player is above the top side of the wall
            newY + playerHeight > wallY   // Top side of player is below the bottom side of the wall
        ) {
            return true; 
        }
    }

    return false; 
};

const isWallOnScreen = (x, y) => {
    const screenWidth = 260;
    const screenHeight = 290;

    // Check if the wall is within the visible area of the screen
    return x >= 0 && y >= 0 && y + 20 <= screenHeight;
}

const wallVisibility = () =>{
    for (let wallKey in walls.value){
        let isVisible = isWallOnScreen(walls.value[wallKey].x, walls.value[wallKey].y)
        if (isVisible){
            walls.value[wallKey].visibility = 'visible'; 
        } else {
            walls.value[wallKey].visibility = 'hidden';
        }

    }
}


const wallPositions = () =>{

     for (let wallKey in walls.value){

             let xCord = Math.floor(Math.random() * 180);
             let yCord = -Math.floor(Math.random() * 250);
   
                 walls.value[wallKey].x = xCord;
                 walls.value[wallKey].y = yCord;
 

    }
}

const wallMove = () =>{
    for (let wallKey in walls.value){
        walls.value[wallKey].y += 1;
        if (walls.value[wallKey].y >= 290) {
            // If the wall hits the floor, reset its position above the screen
            walls.value[wallKey].y = -Math.floor(Math.random() * 20);
            walls.value[wallKey].x = Math.floor(Math.random() * 190);
        }
    }
}
const moveLeft = () =>{
    if (player.value.x - 20 > 0){
        player.value.x -= 20;
    }
}

const moveRight = () =>{
    if (player.value.x + 20 < 245){
        player.value.x += 20;
    }
}

const togglePlay = () =>{
    score.value = 0;
    wallPositions();
    startTimer();
    counterCounting = true;
    playing = true;
    menu_state = 'hidden';

    

}

const calculateTimeInterval = (score) => {
    // Ensure the score is within a certain range
    if (score < 10) {
        return 20;
    } else if (score >= 10 && score < 20) {
        return 5;
    } else if (score >= 20 && score < 30) {
        return 10;
    } else if (score >= 30 && score < 40) {
        return 8;
    } else {
        return 5; // Default value for scores greater than or equal to 40
    }
};
wallPositions()
wallVisibility()

onMounted(() => {
    setInterval(() => {
        if (playing){
            wallMove();
            wallVisibility();
            if (checkPlayerCollision(player.value.x, player.value.y)){
                playing = false;
                counterCounting = false;
                menu_state = 'visible';
            }
        }
    }, 10);  // Move the function call here
});



</script>

<style lang="css" scoped>
.container{
    height: 475px;
    width: 362px;
    min-width: 340px;
    background-color: #313131;
    border-radius: 20px;
    display: flex;
    flex-direction: column;
    box-shadow: 0px 0px 10px 3px #00ff00a2; /* x-ofset | y-ofset | blurr | spread | color*/
    justify-content: space-evenly;
    align-items: center;
    z-index: 2;
    margin: 20px;
}

#buttons-container{
    width: 90%;
    display: flex;
    justify-content: space-evenly;
}

.screen{
    min-height: 290px;
    min-width: 260px;
    border-radius: 10px;
    background-color: #000000;
    position: relative;
}

.screen h1{
    color: #fff;
    text-align: center;
    margin-top: 10px;
}

button {
    height: 72px;
    width: 130px;
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

#left::after{
    content: '<--';
}

#right::after{
    content: '-->';
}

.player{
    background-color: #00ff00;
    position: absolute;
    width: 15px;
    height: 15px; 
}

.wall{
    background-color: #00ff0068;
    position: absolute;
    height: 20px;
    width: 60px;
}

.menu{
    position: absolute;
    min-height: 290px;
    min-width: 260px;
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
    top: 0px;
    background-color: #313131c8;
}

.menu h2{
    font-size: 48px;
    color: #00ff00;
}

.menu h3{
    font-size: 36px;
    color: #00ff00;
}

@media (max-width: 700px) {
    .container{
        height: 360px;
        min-width: 250px;
        width: 260px;
        border-radius: 10px;
    }

    h1 {
        font-size: 24px;
        color: #ffffff;
    }

    .screen, .menu{
        border-bottom-left-radius: 0px;
        border-bottom-right-radius: 0px;
    }

    .menu h2{
        font-size: 36px;
    }

    #buttons-container{
        width: 100%;
    }

    #right{
        font-size: 20px;
        border-bottom-left-radius: 0px;
        border-top-left-radius: 0px;
        border-top-right-radius: 0px;
    }

    #left{
        font-size: 20px;
        border-bottom-right-radius: 0px;
        border-top-right-radius: 0px;
        border-top-left-radius: 0px;
    }
}

</style>