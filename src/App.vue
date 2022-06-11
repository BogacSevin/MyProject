<template>
  <div id="app">
    <login />
    <changePassword/>
  </div>
</template>

<script>
import login from './components/login.vue'
import changePassword from './components/changePassword.vue'

export default {
  name: 'App',
  components: {
    login,
    changePassword
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
