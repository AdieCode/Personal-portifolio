<template>
    <div class="about-main">

         <!-- to navigate back to main page -->
        <div class="back-to-main" @click="goToMain">Back</div>
        <!-- <scroll-up topId="/about/#introduction"/> -->

         <!-- the first section -->
        <section class="introduction" id="introduction">
            <div class="random-coment-start">
                <h2>Lets start</h2>
                <h3>shall we</h3>
            </div>
            <div class="intro">
                <h1>I’m Adriaan Kotzé</h1>
                <h2 id="job">a Web Developer</h2>
                <h3 id="location">based in <img src="../images/location.png" alt="" style="height: 48px; width: 48px;">South Africa</h3>
            </div>
            <div class="photo">
                <img src="../images/me_v1.jpg" alt="">
            </div>
        </section>

        <!-- the second section -->
        <section class="part-one">
            <div class="info">
                <h2>Introduction</h2>
                <p>I started my Programming journey in high school at the age of 
                    <span class="w-word">16</span> and started coding in 
                    <span class="w-word">Delphi</span> where i placed my first Button to change a label’s...
                </p>
                
                <div class="selector my-selector" @click="toggleTextBox">
                    <label>Text</label>
                    <checkbox :boxState="textBox"/>
                </div>
                <div class="selector my-selector" @click="toggleColorBox">
                    <label>color</label>
                    <checkbox :boxState="colorBox"/>
                </div>
            </div>
            <div class="dots">

                <labelchanger :changeText="textBox" :changeColor="colorBox"/>
            </div>
        </section>

         <!-- the third section -->
        <section class="part-two">
            <div class="dots">
                <incription-card/>
            </div>
            <div class="info">
                <h2>More about Myself</h2>
                <p>
                    Stuff started getting more complecated after that of course I started learning about
                    <span class="w-word"> Databases, Incription & Decription and Sorting algorithms </span> 
                    and alot of other stuff that really helped me out quite a bit when I started learning on my own after school.
                </p>
            </div>
        </section>

         <!-- the fourth section -->
         <section class="part-three">
             <div class="info">
                <h2>Almost There</h2>
                <p>
                    After some time I did some course’s in data science on Datacamp, 
                    then I tried my hand at game development and then finally switched over to web development.
                </p>
            </div>
            <div class="dots">
                <mini-game-card/>
            </div>
        </section>

        <!-- the fith section -->
        <section class="part-four">
             <div class="info">
                <h1>The End</h1>
                <p>
                    Thanks for exploring my journey through programming and web development. From my first 
                    button click to diving into data science and game development, it's been an exciting ride.
                    Continuously evolving, I'm passionate about tackling new challenges and leveraging technology to make a positive impact. <br> <br>
                    If you're interested in collaboration or just want to connect, feel free to reach out. Let's chat over a cup of coffee,
                    whether in person or virtually. Thanks again for stopping by, and I look forward to connecting with you in the digital realm.
                </p>
            </div>

            <contactarea/>
        </section>
        <!-- my footer component -->
        <!-- <my-footer/> -->
    </div>
</template>

<script setup>
import { ref } from 'vue';
const router = useRouter()

let textBox = ref(true);
let colorBox = ref(true)

const toggleTextBox = () => {
  textBox.value = !textBox.value;
};

const toggleColorBox = () => {
  colorBox.value = !colorBox.value;
};

const goToMain = () => {
  router.push('/');
}

</script>

<style lang="css">
@import url('https://fonts.googleapis.com/css2?family=Inconsolata:wght@200..900&display=swap');
*{
  margin: 0px;
  padding: 0px;
  font-family: "Inconsolata", monospace;
  scroll-behavior: smooth;
}

::-webkit-scrollbar {
  width: 10px; 
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

.about-main{
    background-color: #181818;
    display: block;
    overflow: hidden;
}

.w-word{
    color: #fff;

}

/* |||||||||||||||||||||||||||||||||
   ||||||| SECTION ONE |||||||||||||
   |||||||||||||||||||||||||||||||||
*/
.random-coment-start{
    height: 100px;
    width: 300px;
    font-size: 48px;
    color: white;
    position: absolute;
    top: 100px;
    left: 100px;
    transform: rotate(-15deg);
}

.random-coment-start h2{
    font-size: 48px;
    font-weight: 400;
    
}

.random-coment-start h3{
    font-size: 48px;
    font-weight: 400;
    text-decoration: underline;
}

@keyframes rotate {
    0% {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(360deg);
    }
}

.introduction{
    height: 100vh;
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    align-items: center;
    background-image: linear-gradient(to bottom, #181818dc, #18181870, #181818e9), url('../images/ccchaos.svg');
    background-repeat: no-repeat;
    /* animation: rotate 30s linear infinite; */

}

.intro h1{
    font-size: 96px;
    font-weight: 500;
    color: white;
}

#job{
    font-size: 48px;
    font-weight: 400;
    color: white;
}

#location{
    font-size: 48px;
    font-weight: 400;
    color: #00FF00;
}

@keyframes sway {
    0% {
        transform: translateX(0) rotate(0deg);
    }
    25% {
        transform: translateX(10px) rotate(-5deg);
    }
    75% {
        transform: translateX(-10px) rotate(5deg);
    }
    100% {
        transform: translateX(0px) rotate(0deg);
    }
}

.photo{
    height: 575px;
    width: 430px;
    border-radius: 20px;
    transform: rotate(-5deg);
    margin-left: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    box-shadow: -2PX 4px 14px 4px #00000090; /* x-ofset | y-ofset | blurr | spread | color*/
    animation: sway 5s  infinite;
}

.photo img{
    height: 640px;
    width: 435px;
    object-fit: contain;
}

/* |||||||||||||||||||||||||||||||||
   ||||||| SECTION TWO |||||||||||||
   |||||||||||||||||||||||||||||||||
*/
.part-one{
    height: 100vh;
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content:space-around;
    align-items: center;
    /* background-image: linear-gradient(to bottom, #181818, #18181870, #1818185d), url('../images/ffflurry.svg'); */

}

.info {
    width: 800px;
    margin: 20px;
}

.info h2{
    font-size: 48px;
    color: white;
    font-weight: 400;
    margin-bottom: 20px;
}

.info p{
    font-size: 36px;
    color: #00FF00;
    font-weight: 400;
    margin-bottom: 25px;
}

.selector.my-selector{
    font-size: 36px !important;
    color: #fff;
    font-weight: 400;
    display: flex;
    justify-content: space-between;
    width: 150px;
    margin-bottom: 6px;
}

@keyframes set-height {
    0%{
        height: 20px;
    }
    100%{
        height: 80px;
    }
}

@keyframes set-width {
    0%{
        width: 80px;
    }
    100%{
        width: 130px;
    }
}

@keyframes set-radius {
    0% {
        border-radius: 0px;
    }
    100% {
        border-radius: 10px;
    }
}

@keyframes set-background {
    0% {
        background-color: transparent;
    }
    100% {
        background-color: #181818;
    }
}

@keyframes set-border {
    0% {
        border: 2px solid #181818;
    }
    100% {
        border: 2px solid #00FF00;
    }
}

@keyframes set-font-color {
    0% {
        color: #000000;
    }
    100% {
        color: #00FF00;
    }
}

@keyframes set-font-size {
    100% {
        font-size: 24px;
    }
}

@keyframes set-font-weight {
    0% {
        font-weight: 200;
    }
    100% {
        font-size: 400;
    }
}
.back-to-main{
    position: absolute;
    top: 20px;
    right: 20px;
    cursor: pointer;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #D9D9D9;

    animation: set-height 0.5s forwards,
               set-width 0.5s 0.5s forwards,
               set-radius 0.2s 1s forwards,
               set-border 0.2s 1.2s forwards,
               set-background 0.2s 1.4s forwards,
               set-font-color 0.1s 1.6s forwards,
               set-font-size 0.1s 1.7s forwards,
               set-font-weight 0.2s 1.8s forwards;

}

.back-to-main:hover{ 
    background-color: #00FF00 !important;
    border: 2px solid #000000 !important;
    color: #000000 !important;
}

/* |||||||||||||||||||||||||||||||||
   ||||||| SECTION THREE |||||||||||||
   |||||||||||||||||||||||||||||||||
*/
.part-two{
    height: 100vh;
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content:space-around;
    align-items: center;
    position: relative;
}

.dots{
    height: 600px;
    width: 600px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-image: radial-gradient(
    circle at center,
    #18181834, 
    #18181850, 
    #18181878, 
    #181818c0, 
    #181818
    ), url('../images/ooorganize_green.svg');
    background-size: contain; 
}

/* |||||||||||||||||||||||||||||||||
   ||||||| SECTION FOUR |||||||||||||
   |||||||||||||||||||||||||||||||||
*/
.part-three{
    height: 100vh;
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content:space-around;
    align-items: center;
    position: relative;
}

/* |||||||||||||||||||||||||||||||||
   ||||||| SECTION FIVE |||||||||||||
   |||||||||||||||||||||||||||||||||
*/
.part-four{
    height: 100vh;
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content:space-around;
    align-items: center;
    position: relative;
}

.info h1{
    font-size: 96px;
    color: white;
    font-weight: 400;
    margin-bottom: 20px;
}


@media (max-width: 1300px) {
    .about-main {
        height: 570vh;

    }

    .random-coment-start{
        height: 100px;
        width: 300px;
        top: 50px;
        left: 50px;
    }

    .random-coment-start h2{
        font-size: 36px;
    }

    .random-coment-start h3{
        font-size: 36px;
    }

    .introduction{
        height: 100vh;
        width: 90%;
        margin: auto;
    }

    .intro h1{
        font-size: 64px;
        font-weight: 500;
        color: white;
    }

    #job{
        font-size: 36px;
        font-weight: 400;
        color: white;
    }

    #location{
        font-size: 36px;
        font-weight: 400;
        color: #00FF00;
    }

    .photo{
        height: 420px;
        width: 315px;
    }

    .photo img{
        height: 500px;
        width: 315px;
    }

    .part-one{
        width: 90%;
        margin: auto;
    }

    .part-two{
        width: 90%;
        margin: auto;
    }

    .part-two .info{
        margin-left: 40px;
    
    }

    .part-three{
        width: 90%;
        margin: auto;
    }

    .info {
        width: 80%;
        margin: 20px;
    }
     
    .info h1{
        font-size: 82px;
    }


    .info h2{
        font-size: 36px;
    }

    .info p{
        font-size: 24px;
    }

    .selector.my-selector{
        font-size: 36px !important;
    }

    .part-four{
        height: 160vh;
        flex-direction: column;
        justify-content: space-evenly;

    }


}

@media (max-width: 700px) {
    .about-main {
        height: 760vh;

    }

    .random-coment-start{
        height: 100px;
        width: 300px;
        top: 10px;
        left: 15px;
    }

    .random-coment-start h2{
        font-size: 24px;
    }

    .random-coment-start h3{
        font-size: 24px;
    }

    .introduction{
        height: 110vh;
        width: 90%;
        flex-direction: column;
        justify-content: space-evenly;
        margin: auto;
        margin-top: 50px;
    }

    .intro h1{
        font-size: 48px;
        font-weight: 500;
        color: white;
    }

    #job{
        font-size: 24px;
        font-weight: 400;
        color: white;
    }

    #location{
        font-size: 24px;
        font-weight: 400;
        color: #00FF00;
    }

    .photo{
        height: 390px;
        width: 290px;
        margin: 0;
    }

    .photo img{
        height: 490px;
        width: 290px;
    }

    .part-one{
        height: 140vh;
        flex-direction: column;
    }

    .part-two{
        height: 150vh;
        flex-direction: column-reverse;
    }
    .part-three{
        height: 130vh;
        flex-direction: column;
    }

    .part-four{
        height: 220vh;
        flex-direction: column;
        justify-content: space-evenly;

    }

    .info {
        width: 80%;
        margin: 20px;
    }
     
    .info h1{
        font-size: 82px;
    }


    .info h2{
        font-size: 36px;
    }

    .info p{
        font-size: 24px;
    }

    .selector.my-selector{
        font-size: 24px !important;
        color: #fff;
        font-weight: 400;
        display: flex;
        justify-content: space-between;
        width: 110px;
        margin-bottom: 6px;
    }


    .dots{
        background-image: linear-gradient(to bottom, #181818ee, #1818185c, #181818ee), url('../images/ooorganize_green.svg');
    }


}

</style>