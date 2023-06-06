<template>
  <div class="container">
    <div>
      <div class="form-header">
        <h1>Registrar</h1>
      </div>
      <form id="register-form" >
        <label>Nombres</label>
        <input
          id="nombres"
          name="nombres"
          type="text"
          required
          v-model="nombres"
        />    
        <br/> <br/>

        <label>Correo</label>
        <input
          id="correo"
          name="correo"
          type="email"
          required
          v-model="email"
        />    
        <br/> <br/>

        <label>Contraseña</label>
        <input
          id="password"
          name="password"
          type="text"
          required
          v-model="password"
        />    
        <br/> <br/>

        <input
          type="submit"
          value="Registrar"
          class="btn btn-primary btn-lg"
        />
      </form>

      <div class="d-flex mt-3 align-items-center">
        <div class="p-2">¿Ya tienes una cuenta?</div>
        <div class="p-2">
          <router-link to="/login">Login</router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default{
  name : "Register",
  data() {
    return {
      nombres : "",
      email : "",
      password : ""
    }
  }
}

</script>
