<template>
  <div class="container-fluid text-center">
    <h1 class="mb-4">FruitHeadz</h1>
    <div class="fruitImages">
      <img class="img-fluid m-1" src="/images/fh1.png" alt="FruitHead1"/>
      <img class="img-fluid m-1" src="/images/fh2.png" alt="FruitHead2"/>
    </div>
    <button type="button" class="btn btn-secondary btn-lg mt-5" disabled>Minting Soon!</button>
  </div>
</template>

<script>
export default{
  name: 'HomePage',
  data(){
    return{}
  },
  methods:{
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Permanent+Marker&display=swap');


h1 {
  font-family: 'Permanent Marker', cursive;
  color: red;
  font-size: 3rem;
}

</style>
