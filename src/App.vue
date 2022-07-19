<template>
<div>
  <img alt="Vue logo" src="./assets/logo.png" />
  <!-- <my-form /> -->
  <!-- <BaseInput label="First Name:" v-model="firstName" /> -->

  <validated-form />
</div>
  
</template>

<script setup>
import { ref } from 'vue'
import MyForm from './components/MyForm.vue'
import BaseInput from './components/BaseInput.vue'
import ValidatedForm from './components/ValidatedForm.vue'


const firstName = ref("");

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>