<template>
  <div id="app">
    <Header />
    <Main />
    
  </div>
</template>

<script>
import Main from "./components/Main"
import Header from "./components/Header"

export default {
  name: 'App',
  components: {
    Main,
    Header
  }
}
</script>

<style lang="scss">
@import "./style/General";

  #app {
    color: white;
    width: 100%; 
    height: 100vh;
  }
</style>
