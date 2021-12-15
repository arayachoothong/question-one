<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style lang="scss">
body {
  overflow: hidden;
  min-width: 600px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
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

@media screen and (max-width: 599.98px) {
  body {
    overflow: auto;
  }
}
</style>
