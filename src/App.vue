<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import 'normalize.css'
import 'concrete.css'

export default {
  name: 'app',
  components: {
    HelloWorld
  }
}
</script>
