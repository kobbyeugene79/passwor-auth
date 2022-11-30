<script setup>

import { computed } from 'vue'
   
    const props = defineProps({
        value: Number
    })

    const strengths = [
        'weak',
        'weak',
        'medium',
        'strong',
        'strongest',
    ]

    const strength = computed(() => strengths[props.value])
    const backgroundClass = computed(() => `status__circle--bg-${strength.value}`)
    const selectedBackgroundClass = computed(() => `status__circle--selected status__circle--selected-bg-${strength.value}`)
    
    const isSelected = (index) => index  <= props.value
    
</script>

<template>
  <div class="status">
    <span class="status__description">{{ strength }}</span>
    <div v-for="index in 4" class="status__circle" :class="[isSelected(index) ? selectedBackgroundClass : backgroundClass]"></div>
  </div>
</template>

<style lang="scss">
    $color-weak: #ff5f55;
    $color-medium: #EDB458;
    $color-strong: #4CB963;
    $color-weak-light: #FFBEBA;
    $color-medium-light: #F7DDB4;
    $color-strong-light: #95D6A3; 
    
    .status{
        display: flex;
        align-items: center;
        gap: 0.5em;
        padding: 2em 0;
        
        &__description{ 
            text-transform: uppercase;
            font-style: italic;
            min-width: 10ch;
            opacity: 0.8;
        }

        &__circle{
            width: 2rem;
            height: 2rem;
            border-radius: 999px;
            background-color: color;
            transition: width 0.2s ease-out;
            &--selected{width: 2.75rem;}
            &--bg-weak{background-color: $color-weak-light;}
            &--bg-medium{background-color: $color-medium-light;}
            &--bg-strong{background-color: $color-strong-light;}
            &--bg-strongest{background-color: $color-strong-light;}
            &--selected-bg-weak{background-color: $color-weak;}
            &--selected-bg-medium{background-color: $color-medium;}
            &--selected-bg-strong{background-color: $color-strong;}
            &--selected-bg-strongest{background-color: $color-strong;}
        }
    }
</style>