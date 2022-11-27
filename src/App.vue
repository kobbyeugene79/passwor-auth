<script setup>

import Prototype from './components/Prototype.vue';
import ThePassword from './components/ThePassword.vue';

</script>

<template>
  <div class="container">
    <h1 class="heading">"Check the <span>Strength</span> of your password"</h1>
    <form @submit.prevent="">
      <ThePassword v-model="userInput" />
    </form>
    <Prototype
      class="Prototype"
    />
  </div>

</template>

<style lang="scss">
@import './assets/base.scss';
</style>
