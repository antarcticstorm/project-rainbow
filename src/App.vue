<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <PromosView promoType="Event" />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import PromosView from './components/PromosView.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    PromosView
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
