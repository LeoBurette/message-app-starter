<template>
  <div class="app">
    <HelloWorld :msg="'Hello this is the App'"/>
    <Messages v-on:unread="updateUnreadMessages"/>
    <Menu :unread-messages="unreadMessages.value"/>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Messages from "./components/Messages";
import Menu from "./components/Menu";

export default {
  name: "App",
  data(){
    return {
      unreadMessages: {
        value : 0,
      }
    }
  },
  components: {
    HelloWorld,
    Messages,
    Menu
  },
  methods:{
    updateUnreadMessages(value){
      this.unreadMessages.value = value;
    }
  }
};
</script>

<style>
  html, body {
    height: 100%;
  }
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }
  .app{
    border : solid 1px chocolate;
  }
</style>
