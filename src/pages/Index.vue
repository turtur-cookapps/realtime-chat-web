<template>
  <q-page>
    <div style="width: 500px; max-width: 90vw;">
      <q-chat-message v-for="chat in chats" :key="chat.chatid"
        :name=chat.name
        :avatar=chat.avatar
        :text=chat.text
        sent
      />
    </div>
  </q-page>
</template>

<style>
</style>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      chats: [
        { chatid: '1', name: 'aaa', avatar: 'aaa', text: ['asdggszgsdg'] },
        { chatid: '2', name: 'bbb', avatar: 'bbb', text: ['zsdhshddfcbcfn'] },
        { chatid: '3', name: 'ccc', avatar: 'ccc', text: ['zsgsdgdxdbb'] },
        { chatid: '4', name: 'ddd', avatar: 'ddd', text: ['wtgddnbxn'] },
        { chatid: '5', name: 'eee', avatar: 'eee', text: ['ddfbbbbfbdbxbf'] }
      ],
      chat: { chatid: '1', name: 'aaa', avatar: 'aaa', text: ['agsgzgdgzdgsgfsfzsdff'] }
    }
  }
}
</script>
