<template>
  <div class="container mt-5 text-center" v-if="show">
      <h2>Stay Up To Date</h2>
      <form name="email" class="p-3" v-on:submit.prevent="addEmail">
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

// Import the functions you need from the SDKs you need

import Firebase from 'firebase/app'

// TODO: Add SDKs for Firebase products that you want to use

// https://firebase.google.com/docs/web/setup#available-libraries


// Your web app's Firebase configuration

// For Firebase JS SDK v7.20.0 and later, measurementId is optional

const firebaseConfig = {

  apiKey: "AIzaSyA5jF1FTiKhl7rnhoqVEpqJ82k0TtVB3bk",

  authDomain: "fruitheadz-855a3.firebaseapp.com",

  databaseURL: "https://fruitheadz-855a3-default-rtdb.firebaseio.com",

  projectId: "fruitheadz-855a3",

  storageBucket: "fruitheadz-855a3.appspot.com",

  messagingSenderId: "561761387591",

  appId: "1:561761387591:web:c78428b8a066bc9ad19d62",

  measurementId: "G-BBNZ2R94J9"

};


// Initialize Firebase

let app = Firebase.initializeApp(firebaseConfig)
let db = app.database()
let emailRef = db.ref('email')

export default{
  name: 'email-form',
  data(){
    return{
      email: '',
      show: true
    }
  },
  methods:{
    addEmail() {
      emailRef.push(this.email)
      this.email = ''
    }
  }
}
</script>

<style scoped>
</style>
