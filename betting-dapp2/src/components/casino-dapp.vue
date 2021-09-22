<template>
<div>
  <hello-metamask/>
  <button @click='connectWallet'>Connect Wallet</button>
</div>
</template>

<script>
import HelloMetamask from '@/components/hello-metamask'

export default {
 name: 'casino-dapp',
 beforeCreate() {
   console.log('registerWeb3 Action dispatched from casino-dapp.vue')
   this.$store.dispatch('registerWeb3')
 },
 components: {
 'hello-metamask': HelloMetamask
 },
 data() {
   return {

   }
 },
 methods: {
   connectWallet() {
    ethereum
    .request({ method: 'eth_requestAccounts' })
    .catch((error) => {
      if (error.code === 4001) {
        // EIP-1193 userRejectedRequest error
        console.log('Please connect to MetaMask.');
      } else {
        console.error(error);
      }
    });
   }
 }
}
</script><style scoped></style>
