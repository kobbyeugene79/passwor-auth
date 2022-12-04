<template>
    
    <div class="input-container">
        <!-- @keyup.enter is not needed -->
        <input 
            type="text" 
            :value="modelValue"
            @input="$emit('update:modelValue', $event.target.value)"
            placeholder="Enter password"
            class="input"
        >

        <div class="passwordLength">{{modelValue.length}}</div>
    </div>

</template>

<script setup>
import { ref } from 'vue'
// no need for zxcvbn here

defineProps(['modelValue'])
defineEmits(['update:modelValue'])

const userInput = ref('')

//what does it do?

//remove test functions after test

</script>


<style lang="scss" scoped>

$text-primary-color: #C3DEEF;
$text-secondary-color: #1B4965;
$bg-color: #F5F5F5;
$weak-passowrd-color: #ff5f55;

.input-container{
    position: relative;
    width: 100%;
    border-radius: 5rem;
    //no BEM?
    //also always use keebab case for class names: .password-length
    .passwordLength{
        // font-family: 'Roboto Mono', monospace;
        // font-size: 1.25rem;
        font-family: Roboto Mono;
        color: $text-primary-color;
        position: absolute;
        // display: flex;
        align-items: center;
        right: 0;
        top: 0;
        bottom: 0;
        padding: 1.07rem 2rem;
        background: $text-secondary-color;
        border-radius: 5rem;
        box-shadow: 0px 4px 4px 0px rgb(0 0 0 / 25%)
    }
}
.input{
    // border: none;
    border: 1px solid $text-primary-color;
    width: 100%;
    outline: $text-primary-color;
    border-radius: 5rem;
    font-size: medium;
    color: $text-secondary-color;
    padding: 1rem 2rem;
    box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.06), 0px 1px 3px rgba(0, 0, 0, 0.1);
    

    /*there is no need for this since you are never going to use the .input class for any other type input element
    (just add styles to the block directly)*/

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