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
    <q-input style="width: 400px;" v-model="text" float-label="입력" @keyup.enter="submit" />
  </q-page>
</template>

<script>
import firebase from 'firebase'
export default {
  name: 'PageIndex',
  data () {
    return {
      db: null,
      name: 'kim',
      text: '',
      chats: [
        { id: '1', name: 'kim', text: ['야'], avatar: 'statics/avatar/joys.jpg' },
        { id: '2', name: 'bbb', avatar: 'statics/avatar/kiwi.jpg', text: ['왜'] },
        { id: '3', name: 'ccc', avatar: 'statics/avatar/mumu.jpg', text: ['뭐'] },
        { id: '4', name: 'ddd', avatar: 'statics/avatar/coco.jpg', text: ['킄'] }
      ]
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
  },
  methods: {
    submit (value) {
      let chat = {
        id: this.chats.length + 1,
        name: this.name,
        avatar: 'statics/avatar/joys.jpg',
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
