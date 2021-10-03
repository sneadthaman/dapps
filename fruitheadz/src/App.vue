<template>
  <div id="app">
    <home-page></home-page>
  </div>
</template>

<script>
import HomePage from '@/components/HomePage.vue'

export default {
  name: 'App',
  components: {
    HomePage
  }
}
</script>

<style>
body {
  background-color: #000000;
  color: #ffffff;
}

</style>
