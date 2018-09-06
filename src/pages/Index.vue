<template>
  <q-page>
    <div style="width: 500px; max-width: 90vw;">
      <q-chat-message v-for="chat in chats" :key="chat.chatid"
        :name="chat.name"
        :avatar="chat.avatar"
        :text="chat.text"
        :sent="chat.name === me"
      />
      <q-input v-model="text" float-label="입력" />
    </div>
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
        { chatid: '1', name: 'aaa', avatar: 'statics/avatar/joys.jpg', text: ['야'] },
        { chatid: '2', name: 'bbb', avatar: 'statics/avatar/kiwi.jpg', text: ['왜'] },
        { chatid: '3', name: 'ccc', avatar: 'statics/avatar/mumu.jpg', text: ['뭐'] },
        { chatid: '4', name: 'ddd', avatar: 'statics/avatar/coco.jpg', text: ['킄'] }
      ]
    }
  }
}
</script>

<style>
</style>
