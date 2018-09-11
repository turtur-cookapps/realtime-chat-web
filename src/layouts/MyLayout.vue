<template>
  <q-layout view="lHh Lpr lFf">
    <q-layout-header>
      <q-toolbar color="primary" >
        <q-toolbar-title>
          Realtime Chat
        </q-toolbar-title>
        <q-btn label="SignOut" @click="signOut"/>
      </q-toolbar>
    </q-layout-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import firebase from 'firebase'

export default {
  name: 'MyLayout',
  data () {
    return {
      leftDrawerOpen: this.$q.platform.is.desktop
    }
  },
  methods: {
    signOut () {
      firebase.auth().signOut()
      this.$router.push('/auth')
    }
  }
}
</script>

<style>
</style>
