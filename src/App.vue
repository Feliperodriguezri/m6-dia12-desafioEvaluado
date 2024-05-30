<template>
  <div id="app" class="container text-center justify-content-center py-3">
    <main class="main">
      <h1>Agenda tu cita medica</h1>

      <form class="border rounded pt-2" action="" @submit.prevent="agregarCita">
        <div class="d-md-flex justify-content-around py-2">
          <!-- Paciente -->
          <div>
            <label class="form-label" for="" :class="!cita.paciente ? 'text-danger' : ''">Paciente</label>
            <input type="text" class="form-control" v-model="cita.paciente">
          </div>
          <!-- Fecha -->
          <div>
            <label class="form-label" for="" :class="!cita.fecha ? 'text-danger' : ''">Fecha</label>
            <input type="date" class="form-control" v-model="cita.fecha">
          </div>
          <!-- Hora -->
          <div>
            <label class="form-label" for="" :class="!cita.hora ? 'text-danger' : ''">Hora </label>
            <input type="time" class="form-control" v-model="cita.hora">
          </div>
          <!-- Gravedad -->
          <div>
            <label class="form-label" for="" :class="!cita.gravedad ? 'text-danger' : ''">Gravedad</label>
            <select name="" id="" class="form-select" v-model="cita.gravedad">
              <option :value="gravedad" v-for="(gravedad, index) in gravedades" :key="index">{{ gravedad }}</option>
            </select>
          </div>
          <!-- Motivo -->
          <div>
            <label class="form-label" for="" :class="!cita.motivo ? 'text-danger' : ''">Motivo</label>
            <input type="text" class="form-control" v-model="cita.motivo">
          </div>
        </div>

        <!-- Div Boton -->
        <div class="py-3">
          <button type="submit" class="btn btn-light" :disabled="!cita.paciente || !cita.fecha || !cita.hora || !cita.gravedad
            || !cita.motivo">Agregar</button>
        </div>

      </form>
      <div class="p-3">
        <p class="text-danger" v-if="citas.length < 1">Aun no hay consultas registradas</p>
        <div v-else class="row g-2">
          <div class="col-3" v-for="(cita, index) in citas" :key="index">
            <CardComp :cita="cita" @eliminarCita="eliminarCitaHandler(index)" />
          </div>
        </div>
      </div>
    </main>
  </div>
</template>



<script>
import CardComp from './components/CardComp.vue';


export default {
  name: 'App',

  components: {
    CardComp,
  },

  data() {
    return {
      citas: [],
      cita: {
        paciente: "",
        fecha: "",
        Hora: "",
        gravedad: "",
        motivo: "",
      },
      gravedades: ["Baja", "Media", "Alta"],
    }
  },

  methods: {
    agregarCita() {
      this.citas.push(this.cita);
      this.cita = {};
    },
    eliminarCitaHandler(index) {
      if (confirm("Seguro que deseas eliminar esta cita?")) {
        this.citas.splice(index, 1)
      }
    }
  },
}
</script>

<style>

</style>
