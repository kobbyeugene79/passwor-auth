<template>
    
    <input 
        @keyup.enter="userInputFxn" 
        type="text" 
        v-model="userInput" 
        placeholder="Enter password"
        class="input"
    >

    <div class="status">
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
    <p v-if="zxcvbn(userInput).feedback.suggestions.length !== 0" class="feedback"><span class="feedback--info">Suggestion</span> {{zxcvbn(userInput).feedback.suggestions[0]}}</p>
</template>

<script setup>
import { ref } from 'vue'
import zxcvbn from 'zxcvbn'

const userInput = ref('')

const userInputFxn = () => {
    return console.log(zxcvbn(userInput.value))
}
</script>
