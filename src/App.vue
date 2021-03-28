<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Keiziban Logo"
          class="shrink mr-2"
          contain
          src="./assets/keiziban.png"
          transition="scale-transition"
          width="40"
        />

        <div
          class="text-h5 shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          width="100"
        >
          Keiziban
        </div>
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/yukinissie/vue-chat-templete"
        target="_blank"
        text
      >
        <span class="mr-2">GITHUB</span>
        <v-icon>fab fa-github</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <Chat/>
    </v-main>
  </v-app>
</template>

<script>
import Chat from './components/Chat'
export default {
  name: 'App',
  components: {
    Chat
  }
};
</script>
