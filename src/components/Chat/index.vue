<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <PostForm v-bind:setMessages="setMessages" />
        <Messages v-bind:messages="messages" msg="messages"></Messages>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Messages from './Messages'
import PostForm from './PostForm'
import axios from 'axios'
import moment from 'moment'

export default {
  name: 'Chat',
  components: {
    Messages,
    PostForm
  },
  data() {
    return {
      messages: null
    }
  },
  mounted () {
    axios
      .get(process.env.VUE_APP_KEIZIBAN_MESSAGE_API_URL)
      .then(response => (this.messages = JSON.parse(response.data.body)))
  },
  methods: {
    setMessages(res) {
      this.messages.splice(0, 0, { id: res.user_id + `${Date.now()}`, message: res.message, created_at: moment(Date.now()).format('LLLL') })
    }
  }
}
</script>

<style>

</style>