<template>
  <q-page>
    <div style="width: 500px; max-width: 90vw;">
      <q-chat-message
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
      chat: { name: 'aaa', avatar: 'aaa', text: ['agsgzgdgzdgsgfsfzsdff'] }
    }
  }
}
</script>
