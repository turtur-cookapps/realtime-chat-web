<template>
  <q-page>
    <div style="width: 500px; max-width: 90vw;">
      <q-chat-message
        name="야임마"
        avatar="statics/boy-avatar.png"
        :text="['뭐']"
        stamp="4 minutes ago"
        sent
      />
      <q-chat-message
        name="ㅎㅎㅎㅎ"
        avatar="statics/linux-avatar.png"
        :text="['hey, if you type in your pw', 'it will show as stars']"
        stamp="7 minutes ago"
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
      chats: [{name: 'aaa', test: 'bbb'}]
    }
  }
}
</script>
