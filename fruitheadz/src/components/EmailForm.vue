<template>
  <div class="container mt-5 text-center" v-if="show">
      <h2>Stay Up To Date</h2>
      <form name="email" method="POST" class="p-3" netlify>
        <div class="form-group">
          <label for="email">Email Address</label>
          <input type="email" class="form-control" id="email" aria-describedby="emailHelp" placeholder="Enter email" required v-model="email">
          <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
        </div>
        <button type="submit" class="btn btn-primary">Submit</button>
      </form>
  </div>
</template>

<script>
export default{
  name: 'email-form',
  data(){
    return{
      email: '',
      show: true
    }
  },
  methods:{
  }
}
</script>

<style scoped>
</style>
