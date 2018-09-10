<template>
  <q-page>
    <q-scroll-area ref="scroll" style="width: 400px; height: 500px;">
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
      if (user) {
        console.log(user)
      } else {
        this.$router.replace('/auth')
        return
      }
      this.name = user.displayName
      this.avatar = user.photoURL
      this.db = firebase.database()
      this.db.ref('chats').on('child_added', (snap) => {
        this.chats.push(snap.val())
        this.chats[this.chats.length - 1].id = snap.key
        this.$nextTick(() => {
          this.$refs.scroll.setScrollPosition(this.$refs.scroll.scrollHeight)
        })
      })
    })
  },
  methods: {
    submit (value) {
      const chat = {
        name: this.name,
        avatar: this.avatar,
        text: [this.text]
      }
      // this.chats.push(chat)
      this.db.ref('chats').push(chat)
      this.text = ''
    }
  }
}
</script>

<style>
</style>
