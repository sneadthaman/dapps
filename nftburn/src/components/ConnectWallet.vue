<template>
  <div class="justify-center">
    <button v-if='!isConnected' @click='connectWallet'>Connect Wallet</button>
    <button v-else>Connected</button>
  </div>
</template>

<script>

export default{
  name: 'connect-wallet',
  data(){
    return{
      isConnected: false
    }
  },
  methods:{
    connectWallet() {
    window.ethereum
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
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');

.justify-center {
  display: flex;
  justify-content: center;
}

button {
  color: green;
  background-color: #171717;
  border: none;
  font-weight: bold;
  font-size: 2rem;
  margin: 2rem;
  margin-bottom: 3rem;
  letter-spacing: .2rem;
  padding: .25rem .8rem;
  font-family: 'Press Start 2P', cursive;
}
button:hover {
  cursor: pointer;
}
</style>
