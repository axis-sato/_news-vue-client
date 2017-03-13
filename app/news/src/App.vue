<template>
  <div id="app">
    <md-toolbar>
      <h1 class="md-title">News</h1>
    </md-toolbar>
    <!--<img src="./assets/logo.png">-->
    <div id="main-content">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
};
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    /*margin-top: 60px;*/
  }

  #main-content {
    padding: 20px 50px;
  }
</style>
