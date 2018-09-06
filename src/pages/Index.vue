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
export default {
  name: 'PageIndex',
  data () {
    return {
      name: 'kim',
      text: '',
      chats: [
        { id: '1', name: 'park', text: ['야'], avatar: 'https://www.mills.edu/uniquely-mills/students-faculty/student-profiles/images/student-profile-gabriela-mills-college.jpg' },
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
        name: this.name,
        avatar: 'https://www.mills.edu/uniquely-mills/students-faculty/student-profiles/images/student-profile-gabriela-mills-college.jpg',
        text: [this.text]
      }
      this.chats.push(chat)
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
