<template>
  <div style="width: 500px; max-width: 90vw;">
    <q-page>
      <q-chat-message
        name="me"
        avatar="statics/boy-avatar.png"
        :text="['hunter2']"
        stamp="4 minutes ago"
        sent
      />
      <q-chat-message
        name="ㅎㅎㅎㅎ"
        avatar="statics/linux-avatar.png"
        :text="['hey, if you type in your pw', 'it will show as stars']"
        stamp="7 minutes ago"
      />
    </q-page>
  </div>
</template>

<style>
</style>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      chats: [{name: 'aaa', test: 'bbb'}]
    }
  }
}
</script>
