<template>
  <div class="home">
    <router-link to="/" > Home  </router-link>
    <router-link to="/login" > Login  </router-link>
    <router-link to="/register" > Register  </router-link>
    
    <router-view/>

  </div>
</template>

<script>

export default {
  name: 'HomeView',
  components: {
    
  }
}
</script>
