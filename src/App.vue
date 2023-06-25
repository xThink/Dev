<template>
  <div id="app">
    <nav>
      <router-link to="/">JSON格式化</router-link>
      <router-link to="/about">About</router-link>
    </nav>
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;

  margin: 0 5%;
}

nav {
  font-size: 20px;
  padding: 30px 0;
}

nav a {
  margin-right: 20px;
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
}

nav a.router-link-exact-active {
  color: #42b983;
  text-decoration: none;
}
</style>
