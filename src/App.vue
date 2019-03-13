<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
// import login from './components/login/login'
export default {
  name: 'App'
  // components: {
  //   'login': login
  // }
}
</script>

<style lang="less">
  .size{
    width: 100%;
    height: 100%;
  }
  html,body{
    .size;
    overflow: hidden;
    margin: 0;
    padding: 0;
  }
  #app {
    .size;
  }
</style>
