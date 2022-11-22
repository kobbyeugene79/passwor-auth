<template>
    <form @submit.prevent="">
        <!-- no need pass userInput as an argument since you can directly access it in the even handler function->
        <input 
            @keyup.enter="zxcvbn(userInput)" 
            type="text" 
            v-model="userInput" 
            placeholder="Enter password"
        >
    </form>
</template>


<script setup>
/* add an import for zxcvbn here */
import { ref } from 'vue'

const userInput = ref('')

/*
    Didn't say make function called zxcvbn.
    instead make a import the zxcvbn library,
    then you pass userInput to the zxcvbn() function to a calculate the password strength and return an object.
    You then log that object to the console
    
    ---------------------------------------
    
    so it's not a good idea to name your event handler function zxcvbn
*/
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
