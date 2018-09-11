<template>
  <q-page>
    <q-scroll-area style="width: 400px; height: 500px;" ref="scroll">
      <q-chat-message v-for="chat in chats" :key="chat.id"
        :name="chat.name"
        :avatar="chat.avatar"
        :text="chat.text"
        :sent="chat.name === name"
      />
    </q-scroll-area>
    <div class="row">
      <q-input style="width: 100px;" v-model="name" stack-label="이름" @keyup.enter="submit" />
      <q-input style="width: 300px;" v-model="text" stack-label="내용" @keyup.enter="submit" />
    </div>
  </q-page>
</template>

<script>

import firebase from 'firebase'

export default {
  name: 'Index',
  data () {
    return {
      db: null,
      name: '',
      avatar: '',
      text: '',
      chats: []
    }
  },
  mounted () {
    firebase.auth().onAuthStateChanged((user) => {
      if (!user) {
        this.$router.replace('/auth')
        return
      }
      this.name = user.displayName
      this.avatar = user.photoURL
    })
    this.db = firebase.database()
    this.db.ref('chats').limitToLast(7).on('child_added', (snap) => {
      let chat = snap.val()
      chat.id = snap.key
      this.chats.push(chat)
      this.$refs.scroll.setScrollPosition(this.$refs.scroll.scrollHeight, 1000)
    })
  },
  beforeDestroy () {
    this.db.ref('chats').off('child_added')
  },
  methods: {
    submit (value) {
      const chat = {
        name: this.name,
        avatar: this.avatar,
        text: [this.text]
      }
      this.db.ref('chats').push(chat)
      this.text = ''
    }
  }
}
</script>

<style>
</style>
