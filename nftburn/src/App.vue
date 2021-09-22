<template>
  <div id="app">
    <main-logo></main-logo>
    <connect-wallet></connect-wallet>
    <input-fields></input-fields>
  </div>
</template>

<script>

import MainLogo from '@/components/MainLogo'
import InputFields from '@/components/InputFields.vue'
import ConnectWallet from '@/components/ConnectWallet.vue'

export default {
  name: 'App',
  components: {
    'main-logo': MainLogo,
    'input-fields': InputFields,
    'connect-wallet': ConnectWallet
  }
}
</script>

<style>
@import './assets/scss/style.css';
</style>
