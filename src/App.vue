<template>
  <div id="q-app">
    <router-view />
  </div>
</template>

<script>

import firebase from 'firebase'

export default {
  name: 'App',
  mounted () {
    const config = {
      apiKey: 'AIzaSyCTelhl0NdLGvSyAOVNOcKyuoXP9lJ5bb8',
      authDomain: 'realtime-chat-web.firebaseapp.com',
      databaseURL: 'https://realtime-chat-web.firebaseio.com',
      projectId: 'realtime-chat-web',
      storageBucket: 'realtime-chat-web.appspot.com',
      messagingSenderId: '478046047641'
    }
    firebase.initializeApp(config)
  }
}
</script>

<style>
</style>
