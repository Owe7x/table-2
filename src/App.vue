<template>
  <div id="app">
    <!-- <header></header> -->
    <top-header></top-header>
    <div id="nav">
      <router-link to="/register" class="nav-top">Register</router-link>|
      <router-link to="/login" class="nav-top">Login</router-link>|
      <router-link to="/table" class="nav-top">Table</router-link>
    </div>
    <router-view />
  </div>
</template>

<script>
import Header from "./components/Top-Header";
export default {
  components: {
    "top-header": Header
  },
  data() {
    return {
      blah: "erik"
    };
  }
};
</script>  

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
  .nav-top {
    text-transform: uppercase;
    text-decoration: none;
    margin-left: 5px;
    margin-right: 5px;
    
  }
}
</style>
