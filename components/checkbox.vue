<template>
    <div class="box" :id="state || 'checked'">

    </div>
</template>

<script setup>
import { ref } from 'vue';

let state = ref('')

const props = defineProps({
    boxState : Boolean
})

watch(() => props.boxState, (newValue) => {
    state.value = newValue ? 'checked' : 'unchecked';
});
</script>

<style lang="css" scoped>
.box{
    height: 36px;
    width: 36px;
    border: 4px solid #00FF00;
    border-radius: 10px;
    cursor: pointer;
}
#unchecked{
    background-color: transparent;
}

#checked{
    background-color: #9747ffb1;
}

@media (max-width: 700px){
    .box{
        height: 24px;
        width: 24px;
    }
}
</style>