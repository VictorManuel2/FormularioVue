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
      cambiarEstado(proyecto, campo){
       // this.urgente = !this.urgente;
        //this.proyectos[id].urgente = !this.proyectos[id].urgente;
        proyecto[campo] = !proyecto[campo];
      }
    },
    computed: {
      numeroProyectos () {
        return this.proyectos.length;
      },
      porcemtaje (){
        let completados = 0;
        this.proyectos.map(proyecto => {
           if(proyecto.completado)
            completados++;
        })
        console.log((completados * 100) / this.numeroProyectos);
        return;
      },
    },
  };
</script>

<template>
<div class="row">
  <div class="col-12 mb-4">
    <h3 class="text-center">
      Progreso 0%
    </h3>
    <div class="progress">
      <div class="progress-bar progress-bar-striped progress-bar-animated bg-success" role="progressbar" 
            aria-valuenow="25" 
            aria-valuemin="0" 
            aria-valuemax="100"
            style="width: 50%" >

      </div>  
    </div>
  </div>
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
          <option >App m??vil con React Native</option>
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
  <h3>Total de Proyectos: {{numeroProyectos}}</h3>
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
            <td>{{ index + 1 }}</td>
            <td>{{ proyecto.proyecto }}</td>
            <td>{{ proyecto.tipo }}</td>
            <td @click="cambiarEstado(proyecto, 'urgente')" :class="proyecto.urgente ? 'bg-danger' : 'bg-success'">{{proyecto.urgente ? "Si" : "No"}}</td>
            <td @click="cambiarEstado(proyecto, 'completado')" :class="proyecto.completado ? 'bg-success' : 'bg-danger'">{{proyecto.completado ? "Completado" : "Incompleto"}}</td>

          </tr>
        </tbody>
      </table>
    </div>
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
