<template>
    <div class="projects-main">
        <back-button/>
        <section class="part-one">
          <projects-preview :projectNumber="projectNumber"/>

          <div class="projects-list">
            <ul>
              <li @click="changeCurrentProject(0)">Personal portifolio</li>
              <li @click="changeCurrentProject(1)">CCB</li>
              <li @click="changeCurrentProject(2)">Personal portifolio</li>
              <li @click="changeCurrentProject(3)">Personal portifolio</li>
              <li @click="changeCurrentProject(4)">Personal portifolio</li>
              <li @click="changeCurrentProject(5)">Personal portifolio</li>
            </ul>
          </div>
        </section>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const projectNumber = ref(0);

function changeCurrentProject(num){
  projectNumber.value = num;
  console.log(projectNumber.value)
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

.projects-main{
    width: 100%;
    background-color: #181818;
    display: block;
    overflow: hidden  ;
}

</style>

<style scoped>
.part-one{
  height: 100vh;
  display: flex;
  background-color: black;
}

.projects-list{
  width: 30%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.projects-list ul{
  list-style-type: none;
  text-align: start;
  margin-left: 20px;
  width: 100%;
}

.projects-list li{
  color: #00FF00;
  padding: 10px 4px;
  font-size: 36px;
  cursor: pointer;
  text-decoration: none;
  transition: 0.2s;
  position: relative;
}

.projects-list li:hover{
  padding-left: 30px;
}

.projects-list li::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background-color: #00FF00;
  transition: width 0.3s ease; /* Transition for width property */
}

.projects-list li:hover::after {
  width: 100%; /* Width expands to 100% on hover */
}
</style>