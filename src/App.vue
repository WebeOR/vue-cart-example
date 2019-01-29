<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Hello-World msg="Welcome to Your Vue.js App"/>
    <Cart />
  </div>
</template>

<script>

import HelloWorld from './components/HelloWorld.vue'
import Cart from './components/Cart.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Cart,
  },
};

</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
