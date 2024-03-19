<template>
    <div class="main-contact" >
        <form action="submit" class="contact-form">
            <label for="email" class="labels">Email</label>
            <input type="text" id="email" class="textinputs">

            <label for="name" class="labels">Name</label>
            <input type="text" id="name" class="textinputs">

            <label for="subject" class="labels">Subject</label>
            <input type="text" id="subject" class="textinputs">

            <label for="message" class="labels">Message</label>
            <textarea name="message" id="message" cols="30" rows="10"></textarea>

            <input type="button" value="Send" id="button" @click="sedit">
        </form>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
    formWidth: Number
})
</script>

<style lang="css" scoped>
.contact-form{
    width: 585px;
    height: 660px;
    min-width: 300px;
    display: flex;
    flex-direction: column;
    margin: 10px;
}

.labels{
    margin-top: 20px;
    margin-bottom: 4px;
    font-size: 36px;
    font-weight: 400;
    color: #00FF00;
}

.textinputs{
    border-radius: 5px;
    border: 2px solid #00FF00;
    padding: 5px 10px;
    background-color: #313131;
    color: white;
    font-size: 24px;
    height: 40px;
}

textarea{
    border-radius: 5px;
    border: 2px solid #00FF00;
    padding: 10px 10px;
    background-color: #313131;
    color: white;
    font-size: 24px;
    min-height: 154px;
    resize: none; 
}

#button {
    width: 158px;
    min-height: 60px;
    color: black;
    font-size: 32px;
    font-weight: 700;
    background-color: #00FF00;
    border-radius: 10px;
    border: none;
    margin-top: 20px;
    cursor: pointer;
}

@media (max-width: 600px) {
    .contact-form {
        width: 300px;
    }
    .textinputs{
        font-size: 20px;
    }
    textarea{
        font-size: 24px;
    }

}

</style>