<script setup>
import { ref } from 'vue';
import zxcvbn from 'zxcvbn';
import Prototype from './components/Prototype.vue';
import ThePassword from './components/ThePassword.vue';

const passwordInput = ref('')
</script>

<template>
  <div class="container">
    <h1 class="heading">"Check the <span>Strength</span> of your password"</h1>
    <form @submit.prevent="">
      <ThePassword v-model="passwordInput" />
    </form>
    <!-- <Prototype
      class="Prototype"
    /> -->
  </div>

</template>

<style lang="scss">
@import './assets/base.scss';
</style>
