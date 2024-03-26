<template>
    <div class="what-i-know-main">
      <back-button/>

      <section class="part-one">
        <div class="heading-container">
          <h1>What I Know</h1>
          <img src="../images/brain.png" alt="">
        </div>
        <div id="background-1"></div>
        <div id="background-2"></div>

      </section>
      
      <section class="part-two">
        <div class="switch-container">
          <h1>Here we go (languages)</h1>
          <div class="items-scroller" >
            <progress-dots :currentProgress="progressLanguages" :totalProgress="2" :yPos="90"/>
            <div class="next-left" @click="moveContainerRight">
              <img src="../images/icons8-triangle-96.png" alt="">
            </div>
            <div class="next-right" @click="moveContainerLeft">
              <img src="../images/icons8-triangle-96.png" alt=""> 
            </div>
            <div class="items-container-1" :class="containerOneSlide" @touchend="moveContainerLeft">
              <language-card imageSource="images/languages/icons8-css-480.png"/>
              <language-card imageSource="images/languages/icons8-html-480.png"/>
              <language-card imageSource="images/languages/icons8-javascript-480.png"/>
              <language-card imageSource="images/languages/icons8-typescript-480.png"/>
              <language-card imageSource="images/languages/icons8-python-480.png"/>
              <language-card imageSource="images/languages/icons8-c-sharp-logo-480.png"/>
            </div>

            <div class="items-container-2" :class="containerTwoSlide" @touchend="moveContainerLeft">
              <language-card imageSource="images/languages/icons8-html-480.png"/>
              <language-card imageSource="images/languages/icons8-html-480.png"/>
              <language-card imageSource="images/languages/icons8-html-480.png"/>
              <language-card imageSource="images/languages/icons8-html-480.png"/>
              <!-- <language-card imageSource="images/languages/icons8-html-480.png"/> -->
              <!-- <language-card imageSource="images/languages/icons8-html-480.png"/> -->
            </div>
          </div>
        </div>
      </section>

      <section class="part-four">
        <div class="scroll-container">

          <div class="moving-container"  @mouseover="slowDown" @mouseout="speedUp">
            <div class="card">1</div>
            <div class="card">2</div>
            <div class="card">3</div>
            <div class="card">4</div>
            <div class="card">5</div>
            <div class="card">6</div>
          </div>

          <!-- <div class="moving-container-2"  @mouseover="slowDown" @mouseout="speedUp">
            <div class="card">7</div>
            <div class="card">8</div>
            <div class="card">9</div>
            <div class="card">10</div>
            <div class="card">11</div>
            <div class="card">12</div>
          </div> -->

        </div>
      </section>
    </div>
</template>

<script setup>
import { ref } from 'vue';
const containerOneSlide = ref('')
const containerTwoSlide = ref('')
const progressLanguages = ref(0)
const previousMouseX = ref(0);
const mouseX = ref(0);
// const grabbed = ref(false)
const cursor = ref("")

const moveContainerLeft = () =>{

  if (progressLanguages.value === 0){
    containerOneSlide.value = 'slide-left-one';
    containerTwoSlide.value = 'slide-left-two';
    progressLanguages.value += 1;
  } else if (progressLanguages.value === 1){
    containerOneSlide.value = 'slide-left-two';
    containerTwoSlide.value = 'slide-left-one';
    progressLanguages.value -= 1;
  }

}

const moveContainerRight = () =>{

  if (progressLanguages.value === 0){
    containerOneSlide.value = 'slide-right-one';
    containerTwoSlide.value = 'slide-right-two';
    progressLanguages.value += 1;
  } else if (progressLanguages.value === 1){
    containerOneSlide.value = 'slide-right-two';
    containerTwoSlide.value = 'slide-right-one';
    progressLanguages.value -= 1;
  }

}

// Function to slow down scrolling
function slowDown() {
  scrollSpeed = 1; // Adjust to desired slowdown speed
}

// Function to speed up scrolling
function speedUp() {
  scrollSpeed = 10000; // Adjust to desired normal speed
}
</script>


<style>
@import url('https://fonts.googleapis.com/css2?family=Inconsolata:wght@200..900&display=swap');
*{
  margin: 0px;
  padding: 0px;
  font-family: "Inconsolata", monospace;
  scroll-behavior: smooth;
}

::-webkit-scrollbar {
  width: 0px; 
  background-color: #373737;
}

::-webkit-scrollbar-thumb {
  background: #009900a2;
  border-radius: 10px;
}

::-webkit-scrollbar-thumb:hover {
  background: #2dfe2dae; 
}

::-webkit-scrollbar-thumb:active {
  background: #2dfe2d; 
}

.what-i-know-main {
    width: 100%;
    background-color: #181818;
    display: block;
    overflow: hidden  ;
}

</style>

<style  scoped>
/* alternate ease-in-out */

@keyframes bounce {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
  100% {
    transform: translateY(0);
  }
}

/* |||||||||||||||||||||||||||||||||
   ||||||| SECTION ONE |||||||||||||
   |||||||||||||||||||||||||||||||||
*/
.part-one {
    height: 100vh;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;

}


#background-1{
    height: 100vh;
    width: 50%;
    position: absolute;
    top: 0px;
    left: 0px;
    background-image:  url('../images/ccchaos (2).svg');
    background-repeat: no-repeat;
    animation: bounce 8s infinite ease-in-out;

}

#background-2{
    height: 100vh;
    width: 50%;
    position: absolute;
    top: 0px;
    left: 50%;
    background-image:  url('../images/ccchaos (3).svg');
    background-repeat: no-repeat ;
    animation: bounce 8s 4s infinite ease-in-out;

}

.heading-container{
  width: 600px;
  height: 400px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  z-index: 1;
}

.heading-container h1{
  font-size: 96px;
  color: #fff;
  margin-bottom: 60px;
}

/* |||||||||||||||||||||||||||||||||
   ||||||| SECTION TWO |||||||||||||
   |||||||||||||||||||||||||||||||||
*/
.part-two {
    height: auto;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}

.next-left{
  height: 450px;
  width: 150px;
  background-color: #181818;
  border-radius: 20px;
  position: absolute;
  left: -30px;
  z-index: 4;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
}

.next-left img{
  height: 48px;
  width: 48px;
  transform: rotate(180deg);
  transition: 0.2s;
}

.next-left:hover img{
  height: 90px;
  width: 90px;
  transition: 0.3s;
}

.next-right{
  height: 450px;
  width: 150px;
  background-color: #181818;
  border-radius: 20px;
  position: absolute;
  right: -30px;
  z-index: 4;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: 0.4s;
}

.next-right img{
  height: 48px;
  width: 48px;
  transition: 0.2s;
}

.next-right:hover img{
  height: 90px;
  width: 90px;
  transition: 0.3s;
}

.switch-container{
  height: 800px;
  width: 1050px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: relative;
  overflow: hidden;
}

.switch-container h1{
  font-size: 48px;
  color: #fff;
  margin-bottom: 60px;
}

.items-scroller {
  height: 460px;
  width: 740px;
  display: flex;
  /* background-color: rgb(71, 71, 71); */
}

.items-container-1 {
  height: 460px;
  width: 720px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  flex-direction: row;
  flex-wrap: wrap;
  position: absolute;

}

.items-container-2 {
  height: 460px;
  width: 720px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  flex-direction: row;
  flex-wrap: wrap;
  position: absolute;

}

.slide-left-one{
  animation: slideLeftOne 1s forwards ;
}

.slide-left-two{
  animation: slideLeftTwo 1s forwards ;
}

.slide-right-one{
  animation: slideRightOne 1s forwards ;
}

.slide-right-two{
  animation: slideRightTwo 1s forwards ;
}



@keyframes slideLeftOne {
  0% {
    transform: translateX(0);
  }
  15% {
    transform: translateX(10px); /* Move right by 6px */
  }
  40%{
    opacity: 0;
  }
  100% {
    transform: translateX(-100%); /* Move all the way to the left */
    opacity: 0;
  }
}

@keyframes slideLeftTwo {
  0% {
    transform: translateX(100%); /* Move all the way to the left */
    opacity: 0;
  }
  15% {
    opacity: 0;
  }
  40%{
    transform: translateX(-10px); /* Move right by 6px */
  }
  100% {
    transform: translateX(0);
  }
}

@keyframes slideRightOne {
  0% {
    transform: translateX(0);
  }
  15% {
    transform: translateX(-10px); /* Move right by 6px */
  }
  40%{
    opacity: 0;
  }
  100% {
    transform: translateX(100%); /* Move all the way to the left */
    opacity: 0;
  }
}

@keyframes slideRightTwo {
  0% {
    transform: translateX(-100%); /* Move all the way to the left */
    opacity: 0;
  }
  15% {
    opacity: 0;
  }
  40%{
    transform: translateX(10px); /* Move right by 6px */
  }
  100% {
    transform: translateX(0);
  }
}

/* |||||||||||||||||||||||||||||||||
   ||||||| SECTION THREE |||||||||||||
   |||||||||||||||||||||||||||||||||
*/

.part-three{
  height: 100vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}
.scroll-container{
  width: 100%;
  overflow-x: hidden;
  display: flex;
  gap: 2rem;
  margin-top: 200px;
  margin-bottom: 200px;
  position: relative;
}

.part-four{
  width: 100%;
  display: flex;
}

.moving-container{
  width: auto;
  display: flex;
  gap: 2rem;
  margin-top: 200px;
  margin-bottom: 200px;
  position: relative;
  /* animation: leftMoving 12s linear infinite; */
}

.moving-container-2{
  width: auto;
  display: flex;
  gap: 2rem;
  margin-top: 200px;
  margin-bottom: 200px;
  position: relative;

}

.card{
  min-width: 700px;
  height: 400px; 
  background-color: #373737; 
  border-radius: 10px;
  margin: 20px;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #fff;
  font-size: 46px;
  animation: leftMoving 12s linear infinite;
}

@keyframes leftMoving {
  to {
    transform: translate(-100%);
  }
}



</style>