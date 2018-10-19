<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <router-view/>
  </div>
</template>

<script>
import firebase from 'firebase'
var config = {
  apiKey: 'AIzaSyBcnuVY9ytSsAda474i5VNfDGDvDi-c5BY',
  authDomain: 'test1710-c1c17.firebaseapp.com',
  databaseURL: 'https://test1710-c1c17.firebaseio.com',
  projectId: 'test1710-c1c17',
  storageBucket: 'test1710-c1c17.appspot.com',
  messagingSenderId: '288797476083'
}
firebase.initializeApp(config)
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
