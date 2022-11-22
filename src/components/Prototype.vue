<template>
    <form @submit.prevent="">
        <input 
            @keyup.enter="zxcvbn(userInput)" 
            type="text" 
            v-model="userInput" 
            placeholder="Enter password"
        >
    </form>
</template>


<script setup>
import { ref } from 'vue'

const userInput = ref('')

const zxcvbn = (userInput) => {
    console.log(userInput)
}

</script>


<style lang="scss" scoped>
// I will apply the styling later
form{
    position: absolute;
    justify-content: center;
}
</style>