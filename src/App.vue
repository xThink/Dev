<template>
  <div id="app">
    <nav>
      <router-link to="/json">JSON格式化</router-link>
      <router-link to="/urlencode">URL编解码</router-link>
      <router-link to="/base64">Base64</router-link>
      <router-link to="/hash">Hash</router-link>
      <router-link to="/number">进制转换</router-link>
      <router-link to="/timestamp">时间戳</router-link>
      <router-link to="/color">颜色</router-link>
      <a target="_blank" href="https://cli.im/">草料二维码</a>
      <router-link to="/ascii">ASCII码</router-link>
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
  font-size: 18px;
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
  text-decoration: underline;
}
</style>
