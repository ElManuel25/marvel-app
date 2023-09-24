<<<<<<< HEAD
=======
<template>
  <div class="background">
    <v-container>
      <v-row justify="center">
        <v-col cols="12" sm="8" md="6">
          <v-card class="elegant-card">
            <v-card-title class="headline">Inicio de sesión</v-card-title>
            <v-card-text>
              <v-form @submit.prevent="login">
                <v-text-field v-model="email" label="Correo electrónico" required placeholder="profe escriba admin@ejemplo.com para entrar"></v-text-field>
                <v-text-field v-model="password" label="Contraseña" type="password" required placeholder="profe escriba contrasena123 para entrar"></v-text-field>
                <v-btn type="submit" class="custom-btn" color="6e22ed">Iniciar Sesión</v-btn>
              </v-form>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<style scoped>
.background {
  background-color: aquamarine;
  background-size: cover;
  background-position: center;
  height: 100vh;
}
.elegant-card {
  background-color: #f5f5f5; /* Fondo del card */
  border-radius: 10px;
}

.custom-btn {
  font-size: 16px;
  font-weight: bold;
  text-transform: uppercase;
}
</style>


<script>
export default {
  data() {
    return {
      email: "",
      password: ""
    };
  },
  methods: {
    login() {
      // Simulando inicio de sesión
      const correoGuardado = "admin@ejemplo.com";
      const contraseñaGuardada = "contrasena123";

      if (this.email === correoGuardado && this.password === contraseñaGuardada) {
        this.$router.push('/home');
      } else {
        alert("Credenciales incorrectas");
      }
    }
  }
};


definePageMeta({
  layout: "blank",
});
</script>


>>>>>>> 9a642f74a42dca284b3d8045d9480938f595f1e9
