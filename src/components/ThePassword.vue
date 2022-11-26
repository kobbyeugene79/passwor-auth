<template>
    
    <div class="input-container">
        <input 
            @keyup.enter="userInputFxn" 
            type="text" 
            v-model="userInput" 
            placeholder="Enter password"
            class="input"
        >

        <div class="passwordLength">{{userInput.length}}</div>
    </div>

    <!-- <div class="status">
        <p v-if="zxcvbn(userInput).score === 0" class="status__name">Weak 
            <span class="status__color status__color--weak"></span>
        </p>
        <p v-else-if="zxcvbn(userInput).score === 1" class="status__name">Meduim 
            <span class="status__color status__color--meduim"></span>
        </p>
        <p v-else-if="zxcvbn(userInput).score === 2" class="status__name">Strong 
            <span class="status__color status__color--strong"></span>
        </p>
        <p v-else-if="zxcvbn(userInput).score >= 3" class="status__name">Strongest 
            <span class="status__color status__color--strongest"></span>
        </p>
    </div>

    <span class="line"></span>

    <div class="crackTime">
        <div><img src="../assets/timer.svg" alt="timer SVG"> </div>
        <div class="crackTime--message"> {{zxcvbn(userInput).crack_times_display.offline_fast_hashing_1e10_per_second}} </div>
    </div>

    <p v-if="zxcvbn(userInput).feedback.warning !== ''" class="feedback"><span class="feedback--info">Warning</span> {{zxcvbn(userInput).feedback.warning}}</p>
    <p v-if="zxcvbn(userInput).feedback.suggestions.length !== 0" class="feedback"><span class="feedback--info">Suggestion</span> {{zxcvbn(userInput).feedback.suggestions[0]}}</p> -->
</template>

<script setup>
import { ref } from 'vue'
import zxcvbn from 'zxcvbn'

const userInput = ref('')
const count = ref('0')

const userInputFxn = () => {
    return console.log(zxcvbn(userInput.value))
}
</script>


<style lang="scss" scoped>

$text-primary-color: #C3DEEF;
$text-secondary-color: #1B4965;
$bg-color: #F5F5F5;
$weak-passowrd-color: #ff5f55;

.input-container{
    position: relative;
    width: 100%;
    border: 1px solid $weak-passowrd-color;
    border-radius: 5rem;

    .passwordLength{
        font-family: Roboto Mono;
        color: $text-primary-color;
        position: absolute;
        align-items: center;
        right: 0;
        top: 0;
        padding: 1.07rem 2rem;
        background: #1B4965;
        border-radius: 5rem;
        box-shadow: 0px 4px 4px 0px rgb(0 0 0 / 25%);
    }
}
.input{
    border: 1px solid $text-primary-color;
    width: 100%;
    outline: $text-primary-color;
    border-radius: 5rem;
    padding: 1rem 2rem;
    box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.06), 0px 1px 3px rgba(0, 0, 0, 0.1);
    
    &[type="text"]{
        font-size: medium;
        color: $text-secondary-color;
    }

    &::placeholder {
        transform: translateX(0);
        opacity: 1;
        transition: 0.5s;
    }

    &:focus::placeholder{
        transform: translateX(10px);
        opacity: 0;
    }
}
</style>