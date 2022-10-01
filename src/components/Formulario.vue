<script>
  export default {
    data: () => ({
      proyecto: "",
      tipo: "",
      urgente: false,
      proyectos: [],
    }),
    methods: {
      registrarProyecto(){
        const proyecto = {
          proyecto: this.proyecto,
          tipo: this.tipo,
          urgente: this.urgente,
          completado: false,
        };
        this.proyectos.push(proyecto);
        
        this.proyecto = "";
        this.tipo = "";
        this.urgente = false;

      },
      cambiarEstado(proyecto){
       // this.urgente = !this.urgente;
        //this.proyectos[id].urgente = !this.proyectos[id].urgente;
      }
    },
    computed: {
      numeroProyectos () {
        return this.proyectos.length;
      }
    }
  }
</script>

<template>
<div class="row">
  <div class="col-12 col-md-4">
    <form @submit.prevent="registrarProyecto">
      <div class="mb-3">
        <label class="form-label">Proyecto</label>
        <input v-model.trim="proyecto" type="text" class="form-control" required> 
      </div>
    
      <div class="mb-3">
        <label class="form-label">Actividad</label>
        <select v-model.trim="tipo" class="form-select" required>
          <option disabled selected value="">Selecciona un tipo de actividad</option>
          <option >Aplicaciones Web con Vue.js</option>
          <option >Backend Services con Node</option>
          <option >App móvil con React Native</option>
        </select>
      </div>
    
      <div class="mb-3">
        <label for="exampleInputPassword1" class="form-check-label">Urgente</label> 
        <input v-model="urgente" type="checkbox" class="form-checkbox" />
      </div>
     
      <button type="submit" class="btn btn-primary">Guardar</button>
    </form>
  </div>
  <div class="col-12 col-md-8">

  </div>
  <!-- <h3>Total de Proyectos: {{numeroProyectos}</h3> -->

<div class="table-responsive">
  <table class="table table-dark table-hover">
    <thead>
      <tr>
        <th>#</th>
        <th>Proyecto</th>
        <th>Tipo</th>
        <th>Urgente</th>
        <th>Completado</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(proyecto, index) in proyectos" :key="index">
        <td>{{index + 1}}</td>
        <td>{{proyecto.proyecto}}</td>
        <td>{{proyecto.tipo}}</td>
        <td @click="cambiarEstado(proyecto)" :class="proyecto.urgente ? 'bg-success' : 'bg-danger'">{{proyecto.urgente ? "Si" : "No"}}</td>
        <td @click="cambiarEstado(index)" :class="proyecto.urgente ? 'bg-success' : 'bg-danger'">{{proyecto.urgente ? "Completado" : "Incompleto"}}</td>

      </tr>
    </tbody>
  </table>
</div>
</div>
</template>
<!-- 
<script>
export default {
  data: () => ({
    nombre: "",
    edad: 0,
    correo: "",
  }),
  methods: {
    addUser() {
      console.log(this.nombre, this.edad, this.correo);
    },
  },
};
</script> -->
