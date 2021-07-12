<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style lang="scss">
* {
  font-family: "Quicksand", sans-serif !important;
}
// Your variable overrides
$blue: rgb(255, 123, 0);
$secondary: rgb(157, 255, 0);
$bg-grey: grey;
@import "~bootstrap/scss/bootstrap.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
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
}
</style>
