<template>
  <div class="app">
    <div class="title-box">
      <h1 class="animate__animated fadeIn" style="font-size: 50px; color: #ffffff; font-family: 'Cursive, cursive; animation: bannerAnimation 3s infinite alternate">UTEC SHOP</h1>
    </div>
    <div class="links">
      <router-link to="/" style="margin-right: 20px;">Home  </router-link>
      <router-link to="/login" style="margin-right: 20px;">Login  </router-link>
      <router-link to="/register">Register  </router-link>
    </div>
    <router-view></router-view>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
