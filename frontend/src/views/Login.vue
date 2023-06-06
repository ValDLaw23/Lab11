<template>
  <div class="container">
    <h1>Acceso usuario</h1>
    <form id="login-form">
      <div class="form-group">
        <label for="email">Correo Institucional</label>
        <input
          type="email"
          id="email"
          placeholder="Ingresa email"
          v-model="email"
        >
      </div>
      <div class="form-group">
        <label for="password">Contraseña</label>
        <input 
          type="password"
          id="password"
          placeholder="Ingresa Contraseña"
          v-model="password"
        >
      </div>
      <div class="submit-button">
        <button type="submit">Login</button>
      </div>
    </form>
    <div class="signup-link">
      <p>¿No tienes una cuenta?</p>
      <router-link to="/register">Regístrate</router-link>
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

<style>
.container {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

form {
  display: flex;
  flex-direction: column;
}

.form-group {
  margin-bottom: 10px;
}

label {
  font-weight: bold;
}

input[type="email"],
input[type="password"] {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.submit-button {
  text-align: center;
  margin-top: 20px;
}

button {
  padding: 10px 20px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.signup-link {
  text-align: center;
  margin-top: 20px;
}

p {
  margin-bottom: 10px;
}

router-link {
  color: #007bff;
  text-decoration: underline;
}
</style>
