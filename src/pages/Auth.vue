<template>
  <q-page>
    <q-btn label="Login Facebook"  @click="onClick"/>
  </q-page>
</template>

<script>

import firebase from 'firebase'

export default {
  name: 'Auth',
  mounted () {

  },
  methods: {
    onClick () {
      const provider = new firebase.auth.FacebookAuthProvider()
      firebase.auth().signInWithPopup(provider).then((result) => {
        this.$router.push('/')
      }).catch((message) => {
        this.$router.push('/auth')
      })
    }
  }
}
</script>

<style>
</style>
