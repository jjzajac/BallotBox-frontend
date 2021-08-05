<template>
  <div>
    <div id="nav">
      <router-link to="/">TOP_SUBJECT</router-link> |
      <router-link to="/about">SUBJECTS</router-link>
    </div>
    <suspense>
      <router-view/>
    </suspense>
  </div>
</template>

<style lang="scss">
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
