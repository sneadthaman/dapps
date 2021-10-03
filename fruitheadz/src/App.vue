<template>
  <div id="app">
    <home-page></home-page>
    <email-form></email-form>
  </div>
</template>

<script>
import HomePage from '@/components/HomePage.vue'
import EmailForm from '@/components/EmailForm.vue'


export default {
  name: 'App',
  components: {
    HomePage,
    EmailForm
  }
}
</script>

<style>
body {
  background-color: #000000 !important;
  color: #ffffff !important;
}
</style>
