<template>
  <v-list>
    <v-list-item v-for="message in messages" v-bind:key="message.id + `${Date.now()}`" three-line>
      <v-list-item-content>
        <v-list-item-title>{{ message.message }}</v-list-item-title>
        <v-list-item-subtitle>ゲスト</v-list-item-subtitle>
        <v-list-item-subtitle>{{ moment(message.created_at).format('LLLL') }}</v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>
  </v-list>
</template>

<script>
import moment from 'moment'

export default {
  name: 'Messages',
  props: {
    messages: Array
  },
  methods: {
    moment
  }
}
</script>

<style>

</style>