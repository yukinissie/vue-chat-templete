<template>
<div>
  <v-footer
    app
    color="transparent"
    height="72"
    inset
    class="grey lighten-2"
  >
    <v-row cols="12">
      <v-text-field
        background-color="white lighten-1"
        dense
        flat
        hide-details
        solo
        v-model="message"
        placeholder="メッセージ"
      />
      <v-btn
        color="primary"
        elevation="2"
        v-on:click="loader = 'loading', postMessage(), clearForm()"
        :loading="loading"
        :disabled="loading"
      >
        投稿
      </v-btn>
    </v-row>
  </v-footer>
</div>
</template>

<script>
import axios from 'axios'

export default {
  props: {
    setMessages: Function
  },
  data() {
    return {
      message: '',
      loading: false
    }
  },
  methods: {
    postMessage() {
      const l = this.loader
      this[l] = !this[l]
      axios
        .post(process.env.VUE_APP_KEIZIBAN_MESSAGE_API_URL,{
          user_id: "test-test-test",
          message: this.message
        })
        .then(response => {
          this.setMessages(JSON.parse(response.config.data));
          this[l] = !this[l];
          this.loader = null;
        })
    },
    clearForm() {
      this.message = ''
    }
  }
}
</script>

<style>

</style>