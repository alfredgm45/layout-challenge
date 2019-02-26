<template>
  <div id="app">
    <HelloWorld/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
@font-face {
  font-family: turing;
  src: url('/src/assets/hinted-GorditaRegular.ttf');
}
#app {
  /* font-family: 'Avenir', Helvetica, Arial, sans-serif; */
  font-family: sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
