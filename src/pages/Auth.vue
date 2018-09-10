<template>
  <q-page>
    <div id="firebaseui-auth-container"></div>
  </q-page>
</template>

<script>

import firebase from 'firebase'
import firebaseui from 'firebaseui'
import '../../node_modules/firebaseui/dist/firebaseui.css'

export default {
  name: 'Auth',
  data () {
    return {

    }
  },
  mounted () {
    const uiConfig = {
      signInOptions: [
        firebase.auth.FacebookAuthProvider.PROVIDER_ID
      ],
      signInFlow: 'popup'
    }
    let ui = firebaseui.auth.AuthUI.getInstance()
    if (!ui) ui = new firebaseui.auth.AuthUI(firebase.auth())
    ui.start('#firebaseui-auth-container', uiConfig)

    firebase.auth().onAuthStateChanged((user) => {
      if (user) {
        this.$router.push('/')
      } else {
        this.$router.push('/auth')
      }
    })
  },
  methods: {

  }
}
</script>

<style>
</style>
