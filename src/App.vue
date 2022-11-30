<script setup>
import { ref, computed } from 'vue';
import zxcvbn from 'zxcvbn';
import PasswordStatus from '@/components/PasswordStatus.vue';
// import PasswordStatusCircle from './components/PasswordStatusCircle.vue' 
import Prototype from './components/Prototype.vue';
import ThePassword from './components/ThePassword.vue';

const passwordInput = ref('')


const passwordStrengthData = computed(() => zxcvbn(passwordInput.value))

</script>

<template>
  <div class="container">
    <h1 class="heading">"Check the <span>Strength</span> of your password"</h1>
    <the-password v-model="passwordInput" />
    <password-status :passwordProp="passwordInput"/>
    <!-- <password-status-circle :value="passwordStrengthData.score" /> -->
  </div>

</template>

<style lang="scss">
@import './assets/base.scss';
</style>
