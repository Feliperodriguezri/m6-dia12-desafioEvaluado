<template>
    <div class="CardComp">
        <div id="cardPaciente">
            <div class="card" style="width: 18rem;">
                <div class="card-body" :class="cita.gravedad == 'Alta' ? 'text-bg-danger' : cita.gravedad == 'Media' ? 'text-bg-warning' : cita.gravedad == 'Baja' ? 'text-bg-success' : ''">
                    <h6 class=" card-title">Paciente</h6>
                    <p class="card-text"> {{ cita.paciente }}</p><hr>
                    <h6 class="card-title">Fecha</h6>
                    <p class="card-text"> {{ cita.fecha }}</p><hr>
                    <h6 class="card-title">Hora</h6>
                    <p class="card-text"> {{ cita.hora }}</p><hr>
                    <h6 class="card-title">Motivo</h6>
                    <p class="card-text"> {{ cita.motivo }}</p><hr>
                    <button href="#" class="btn btn-primary" @click="$emit('eliminarCita')">Eliminar</button>
                </div>
            </div>
        </div>

    </div>
</template>

<script>

export default {
    name: "CardComp",
    props: {
        cita: Object,
    },
    data() {
        return {

        }
    }
}
</script>

<style scoped>
.card {
border-radius: 1px solid black;
}
</style>