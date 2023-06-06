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

.title-box {
  background-image: url('@/assets/logo_utec.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100px;
}

.links {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-left: 660px;
  margin-right: 660px;
  height: 20px;
  border-radius: 8px;
  background-color: #fffb00;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.router-link {
  margin: 100px;
}

.router-link-active {
  font-weight: bold;
}

.router-link-exact-active {
  color: #4caf50;
}

.router-view {
  margin-top: 20px;
  padding: 20px;
  background-color: #9103f6;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: opacity 0.3s ease;
}

.fadeIn {
  opacity: 0;
  transform: translateY(-20px);
  transition: opacity 1s ease, transform 1s ease;
}

.fadeIn.show {
  opacity: 1;
  transform: translateY(0);
}

.router-view-enter-active,
.router-view-leave-active {
  opacity: 0;
}

.router-view-enter,
.router-view-leave-to {
  opacity: 1;
}

.app {
  height: 1000px;
  background-color: rgb(0, 179, 255);
}

@keyframes bannerAnimation {
  0% {
    transform: translateY(-10px);
  }
  100% {
    transform: translateY(10px);
  }
}

</style>