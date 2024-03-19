<template>
    <div class="container">
        <h1>Try it out</h1>
        <input type="text" name="text" id="edit" placeholder="Please enter something" autocomplete="off" :value="editText" @input="editText = $event.target.value"/>
        <div id="buttons-container"> 
            <button @click="encrypt">Incript</button>
            <button @click="decrypt">Decript</button>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

let editText = ref('');

function encrypt() {
    let key = 'abcdefghijklmnopqrstuvwxyz';
    let result = '';
    for (let i = 0; i < editText.value.length; i++) {
        let char = editText.value.charAt(i);
        let index = key.indexOf(char);
        if (index !== -1) {
            result += key.charAt((index + 1) % key.length);
        } else {
            result += char;
        }
    }
    console.log('Encrypted:', result);
    editText.value = result;
}

function decrypt() {
    let key = 'abcdefghijklmnopqrstuvwxyz';
    let result = '';
    for (let i = 0; i < editText.value.length; i++) {
        let char = editText.value.charAt(i);
        let index = key.indexOf(char);
        if (index !== -1) {
            result += key.charAt((index - 1 + key.length) % key.length);
        } else {
            result += char;
        }
    }
    console.log('Decrypted:', result);
    editText.value = result;
}


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
    box-shadow: 0px 0px 10px 3px #00ff00a2;/* x-ofset | y-ofset | blurr | spread | color*/
    justify-content: space-evenly;
    align-items: center;
    z-index: 2;
    margin: 20px;
}

h1{
    font-size: 36px;
    font-weight: 800;
    color: #00ff00;
}
#edit{
    height: 40px;
    width: 300px;
    background-color: #313131;
    border: none;
    outline: none;
    padding: 4px;
    text-align: center;
    border-bottom: 2px solid #00ff00;
    font-size: 24px;
    font-weight: 300;
    color: white;

}

#buttons-container{
    width: 100%;
    display: flex;
    justify-content: space-evenly;
}

button {
    height: 72px;
    width: 132px;
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

@media (max-width: 700px) {
    .container{
        height: 350px;
        min-width: 250px;
        width: 250px;
    }

    h1 {
        font-size: 36px;
    }

    #edit{
        font-size: 20px;
        height: 30px;
        width: 90%;

    }

    button{
        font-size: 20px;
        height: 60px;
        width: 110px;
    }


}
</style>