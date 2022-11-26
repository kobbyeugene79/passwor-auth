<script setup>

import Prototype from './components/Prototype.vue';

</script>

<template>
  <div class="container">
    <h1 class="heading">"Check the <span>Strength</span> of your password"</h1>
    <Prototype
      v-model="userInput" 
      class="Prototype"
    />
  </div>

</template>

<style lang="scss">
@import './assets/base.scss';
</style>
