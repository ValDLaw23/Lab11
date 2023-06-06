<template>
  <div class="container">
    <h1>Acceso usuario</h1>
    <form id="login-form">
      <p>Correo Institucional</p>
      <input
        type="email"
        placeholder="Ingresa email"
        v-model="email"
      >
      <p>Contraseña</p>
      <input 
        type="password"
        placeholder="Ingresa Contraseña"
        v-model="password"
      >
      <div class="submit-button">
        <button type="submit">Login</button>
      </div>
    </form>
    <br/> <br/>

    <div>
        <div class>¿No tienes una cuenta?</div>
        <div class>
          <router-link to="/register">Regístrate</router-link>
        </div>
      </div>

  </div>
</template>

<script>
export default{
  name : "Login",
  data() {
    return {
      email : "",
      password : ""
    }
  }
}

</script>
