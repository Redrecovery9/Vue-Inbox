<template>
  <div id="app">
    <toolbar></toolbar>
    <messages></messages>
  </div>
</template>

<script>
import Toolbar from './components/Toolbar'
import Messages from './components/Messages'

export default {
  name: 'app',
  components: {
    Toolbar,
    Messages
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
