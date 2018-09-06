<template>
  <q-page>
    <q-scroll-area ref="container" style="width: 400px; height: 500px;">
      <q-chat-message v-for="chat in chats" :key="chat.id"
        :name="chat.name"
        :avatar="chat.avatar"
        :text="chat.text"
        :sent="chat.name === me"
      />
    </q-scroll-area>
    <q-input style="width: 400px;" v-model="text" float-label="입력" @keyup.enter="submit" />
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      me: 'aaa',
      text: '',
      chats: [
        { id: '1', name: 'aaa', avatar: 'statics/avatar/joys.jpg', text: ['야'] },
        { id: '2', name: 'bbb', avatar: 'statics/avatar/kiwi.jpg', text: ['왜'] },
        { id: '3', name: 'ccc', avatar: 'statics/avatar/mumu.jpg', text: ['뭐'] },
        { id: '4', name: 'ddd', avatar: 'statics/avatar/coco.jpg', text: ['킄'] }
      ]
    }
  },
  methods: {
    submit (value) {
      let chat = {
        id: this.chats.length + 1,
        name: this.me,
        avatar: 'statics/avatar/joys.jpg',
        text: [this.text]
      }
      this.chats.push(chat)
      this.text = ''
      this.$nextTick(() => {
        this.$refs.container.setScrollPosition(this.$refs.aaa.scrollHeight)
      })
    }
  }
}
</script>

<style>
</style>
