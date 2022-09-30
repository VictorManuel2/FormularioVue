<template>
  <div class="container mt-3">
   <Header />
  <Formulario />
    <!-- <form @submit.prevent="addUser">
      <div>
        <label>
        nombre: <input v-model="nombre" type="text" placeholder="Nombre" required/>
      </label>
      </div>
      <div>
        <label>
        edad: <input v-model="edad" type="number" min="15" max="80" placeholder="edad" required/>
      </label>
      </div>
      <div>
        <label>
        correo: <input v-model="corro" type="email" placeholder="gmail@gmail.com " required/>
      </label>
      </div>
      
      <button type="submit">Enviar</button>
    </form> -->
  </div>
</template>

<script>
  import Header from "./components/Header.vue";
  import Formulario from "./components/Formulario.vue";

  export default{
    components: {
      Header,
      Formulario
    }
  }
</script>



