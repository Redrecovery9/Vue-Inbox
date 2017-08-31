<template>
  <div class="messages">
    <Message v-for="email in emails" :email="email" key="" :toggle='toggle' :starred='starred'></Message>
  </div>
</template>

<script>
import Message from './Message'

export default {
  name: 'messages',
  props: ['emails', 'toggle', 'starred'],
  components: {
    Message
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
