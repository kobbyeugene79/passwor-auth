<script setup>
import { ref, computed } from 'vue';
import zxcvbn from 'zxcvbn';
import TheFeedback from './components/TheFeedback.vue';
// import PasswordStatus from '@/components/PasswordStatus.vue';
import PasswordStatusRefactor from './components/PasswordStatusRefactor.vue' 
import ThePassword from './components/ThePassword.vue';

const passwordInput = ref('')
const passwordStrengthData = computed(() => zxcvbn(passwordInput.value))

</script>

<template>

  <div class="container">
    <h1 class="heading">"Check the <span>Strength</span> of your password"</h1>
    <the-password v-model="passwordInput" />
    <!-- <password-status :passwordProp="passwordStrengthData.score"/> -->
    <password-status-refactor :value="passwordStrengthData.score" />

    <the-feedback 
      name="Warning" 
      :content="passwordStrengthData.feedback.warning" 
    />
    <the-feedback 
      name="Suggestion" 
      v-for="(suggest, index) in passwordStrengthData.feedback.suggestions" 
      :key="index" 
      :content="suggest" 
    />
  </div>

</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;700&family=Roboto+Mono&display=swap');
@import './assets/base.scss';
</style>
