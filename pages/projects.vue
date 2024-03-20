<template>
    <div class="projects-main">
        <back-button/>
        <section class="part-one">
          <projects-preview :projectNumber="projectNumber" ref="previewRef"/>

          <div class="projects-list">
            <ul>
              <li @click="changeCurrentProject(0)">Personal portfolio <span class="category">Web dev</span></li>
              <li @click="changeCurrentProject(1)">CCB <span class="category">Automation</span></li>
              <li @click="changeCurrentProject(2)">Budget Manager <span class="category">API</span></li>
              <li @click="changeCurrentProject(3)">Chat webpage <span class="category">Web dev</span></li>
              <li @click="changeCurrentProject(4)">Manga list <span class="category">Web dev</span></li>
              <li @click="changeCurrentProject(5)">Wiki words <span class="category">Web dev</span></li>
            </ul>
          </div>
        </section>
    </div>
</template>

<script setup>
import { ref } from 'vue'
const previewRef = ref()
const projectNumber = ref(0);

function changeCurrentProject(num){
  projectNumber.value = num;
  previewRef.value.scrollTop = 0;
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
  font-size: 30px;
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

.category{
  color: #00ff00ad;
  font-size: 24px;
  opacity: 0;
  transition: 0.3s;
}

.projects-list li:hover .category{
  opacity: 100%;
  transition: 0.2s;
}
</style>