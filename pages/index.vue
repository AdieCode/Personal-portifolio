<template>

    <div class="main-page"> <!-- Add class here -->
        <!-- Content of the component -->
        <div class="options">
            <div class="greeting">
                <h3>Hi i'm</h3>
                <h1>Adriaan</h1>
            </div>
            <div class="choices">
                <div class="about" @click="goToAbout">
                    <maincard :imageSource="navInfo.about.imageSource" :title="navInfo.about.title" :height="navInfo.about.height" :width="navInfo.about.width" :rotation="navInfo.about.rotation"/>
                </div>
    
                <div class="projects" @click="goToProjects">
                    <maincard :imageSource="navInfo.projects.imageSource" :title="navInfo.projects.title" :height="navInfo.projects.height" :width="navInfo.projects.width" :rotation="navInfo.projects.rotation"/>
                </div>
    
                <div class="what-i-know" @click="goToWhatIKnow">
                    <maincard :imageSource="navInfo.whatIKnow.imageSource" :title="navInfo.whatIKnow.title" :height="navInfo.whatIKnow.height" :width="navInfo.whatIKnow.width" :rotation="navInfo.whatIKnow.rotation"/>
                </div>
    
                <div class="my-likes" @click="goToMyLikes">
                    <maincard :imageSource="navInfo.myLikes.imageSource" :title="navInfo.myLikes.title" :height="navInfo.myLikes.height" :width="navInfo.myLikes.width" :rotation="navInfo.myLikes.rotation"/>
                </div>
            </div>
            

            <div class="contact-way">
                <h2><a href="#contact"> Contact <br>page</a></h2> 
            </div>
        </div>

        <div class="contact" id="contact">
            <div class="contact-container">
                <h1>Contact me</h1>
                <contactarea/>
            </div>
            <div class="describe-contact">
                <h1>Contact me</h1>
                <p>Hi there, if you want to contact me please do so here.</p>
                <p id="notice">(Please note that all feilds are required)</p>
            </div>
        </div>
  </div>
</template>

<script setup>
import contactarea from '~/components/contactarea.vue';
const router = useRouter()

const navInfo = {
  about : {
    imageSource : 'images/user.png',
    title: 'About me',
    height : '290',
    width: '277',
    rotation: '-10'
  },
  projects : {
    imageSource : 'images/folder.png',
    title: 'Projects',
    height : '342',
    width: '250',
    rotation: '25'
  },
  whatIKnow : {
    imageSource : 'images/brain.png',
    title: 'What I know',
    height : '335',
    width: '304',
    rotation: '18'
  },
  myLikes : {
    imageSource : 'images/thumb.png',
    title: 'My likes',
    height : '240',
    width: '232',
    rotation: '-5'
  }
}

function goToAbout() {
  router.push('/about');
}

function goToProjects() {
  router.push('/projects');
}

function goToWhatIKnow() {
  router.push('/what-I-know');
}

function goToMyLikes() {
  router.push('/my-likes');
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
  width: 10px; /* Width of the scrollbar */
  background-color: #373737;
}
/* Handle */
::-webkit-scrollbar-thumb {
  background: #009900a2; /* Color of the scrollbar handle */
  border-radius: 10px;
}
/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #2dfe2dae; /* Color of the scrollbar handle when hovered */
}

/* Track when the handle is being dragged */
::-webkit-scrollbar-thumb:active {
  background: #2dfe2d; /* Color of the scrollbar handle when being dragged */
}
.main-page{

  background-color: #181818;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  position: relative;
  overflow: hidden;
}
</style>

<style lang="css" scoped>
@import url('https://fonts.googleapis.com/css2?family=Inconsolata:wght@200..900&display=swap');
*{
  margin: 0px;
  padding: 0px;
  font-family: "Inconsolata", monospace;
  scroll-behavior: smooth;
}
::-webkit-scrollbar {
  width: 10px; /* Width of the scrollbar */
  background-color: #373737;
}
/* Handle */
::-webkit-scrollbar-thumb {
  background: #009900a2; /* Color of the scrollbar handle */
  border-radius: 10px;
}
/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #2dfe2dae; /* Color of the scrollbar handle when hovered */
}

/* Track when the handle is being dragged */
::-webkit-scrollbar-thumb:active {
  background: #2dfe2d; /* Color of the scrollbar handle when being dragged */
}
.main-page{
  width: 100%;
  height: 200vh;
  background-color: #181818;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  position: relative;
  overflow: hidden;
}

.options{
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  position: relative;

}

.choices{
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    width: 100%;
    height: 100%;
}
.about{
  position: absolute;
  top:8%;
  left: 23%;
  cursor: pointer;
}

.projects{
  position: absolute;
  top:14%;
  left: 73%;
  cursor: pointer;
}

.what-i-know{
  position: absolute;
  top:57%;
  left: 14%;
  cursor: pointer;
}

.my-likes{
  position: absolute;
  top: 68%;
  left: 62%;
  cursor: pointer;
}

.greeting{
  position: absolute; 
  top: 50%; 
  left: 50%; 
  transform: translate(-50%, -50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  z-index: 1;
}

.greeting h3{
 font-size: 24px;
 font-weight: 400;
 color: white;
}

.greeting h1{
 font-size: 128px;
 font-weight: 500;
 background-image: linear-gradient(to right, #009900, #2dfe2d, #009900);
  -webkit-background-clip: text; /* Clip text to background gradient */
  color: transparent; /* Make text transparent */
  text-fill-color: transparent; /* Make text fill color transparent */
}

.contact-way{
  color: white;
  font-size: 36px ;
  font-weight: 100;
  text-decoration: underline;
  text-align: end;
  position: absolute;
  right: 60px;
  bottom: 80px;
  display: flex;
}
.contact-way a{
  text-decoration: none;
  color: white;
}

.contact{
  width: 100%;
  height: auto;
  display: flex;
  justify-content: center;
  align-items: center;
}

.contact-container{
 margin-top: 100px;
}

.contact-container h1{
    color: #00FF00;
    font-size: 64px;
    font-weight: 500;
    margin-bottom: 25px;
    text-align: center;
    visibility: hidden;
}

.describe-contact{
  margin-left: 150px;
  width: 352px;
  color: #00FF00;
}

.describe-contact h1{
  font-size: 64px;
  font-weight: 500;
  margin-bottom: 25px;
}

.describe-contact p{
  font-size: 36px;
  font-weight: 400;

}

#notice{
  font-size: 24px;
  color: #9747FF;
  font-weight: 400;
}

@media (max-width: 1300px) {
    .my-likes {
        position: static !important;
    }
    .about {
        position: static !important;
    }
    .what-i-know {
        position: static !important;
    }
    .projects {
        position: static !important;
    }
    .choices{
        display: flex;
        flex-wrap: wrap;
        width: 550px;
        height: 560px;
    }
    .greeting{
        margin-top: 20px;
        transform : translate(0);
        position: static;
        left: 230px;
        top: 200px;
    }

    .contact{
        position: static;
        display: flex;
        justify-content: center;
    }

    .contact-container h1{
        visibility: visible;

    }
    .describe-contact{
        visibility: hidden;
        position: fixed;
    }
    .contact-way{
        visibility: hidden;
    }
    .main-page{
      height: 230vh;
    }
}

@media (max-width: 600px) {
  .greeting h3{
    font-size: 24px;
   }

  .greeting h1{
    font-size: 68px;
   }
   
   .main-page{
    height: 340vh;
   }
   .choices{
    justify-content: flex-start;
    flex-wrap: nowrap;
    height: 1080px;
   }
   .options{
    height: 200vh;
   }

    .describe-contact{
        visibility: hidden;
        position: fixed;
    }
    .contact-way{
        visibility: hidden;
    }

    .describe-contact h1{
      font-weight: 900;
    }
}

</style>