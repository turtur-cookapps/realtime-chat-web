<template>
  <q-page>
    <q-scroll-area ref="messages" style="width: 400px; height: 500px;">
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
  name: 'PageIndex',
  data () {
    return {
      db: null,
      name: 'joyce',
      text: '',
      chats: []
      /*
      chats: [
        { name: 'joyce', text: ['야'], avatar: 'https://web.cookappslab.com/avatar/joyce.jpg' },
        { name: 'kiwi', text: ['왜'], avatar: 'https://web.cookappslab.com/avatar/kiwi.jpg' },
        { name: 'mumu', text: ['뭐'], avatar: 'https://web.cookappslab.com/avatar/mumu.jpg' },
        { name: 'coco', text: ['킄'], avatar: 'https://web.cookappslab.com/avatar/coco.jpg' }
      ]
      */
    }
  },
  mounted () {
    let config = {
      apiKey: 'AIzaSyCTelhl0NdLGvSyAOVNOcKyuoXP9lJ5bb8',
      authDomain: 'realtime-chat-web.firebaseapp.com',
      databaseURL: 'https://realtime-chat-web.firebaseio.com',
      projectId: 'realtime-chat-web',
      storageBucket: 'realtime-chat-web.appspot.com',
      messagingSenderId: '478046047641'
    }
    firebase.initializeApp(config)
    this.db = firebase.database()
    this.db.ref('chats').limitToLast(10).on('value', (snap) => {
      this.chats = []
      snap.forEach(child => {
        this.chats.push(child.val())
        this.chats[this.chats.length - 1].id = child.key
      })
    })
  },
  methods: {
    submit (value) {
      let chat = {
        name: this.name,
        avatar: 'https://web.cookappslab.com/avatar/' + this.name + '.jpg',
        text: [this.text]
      }
      this.chats.push(chat)
      this.db.ref('chats').push(chat)

      this.text = ''
      this.$nextTick(() => {
        this.$refs.messages.setScrollPosition(this.$refs.messages.scrollHeight)
      })
    }
  }
}
</script>

<style>
</style>
