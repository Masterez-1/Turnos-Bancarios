<template>
  <div class="bg-white p-6 rounded-lg shadow-md">
    <h2 class="text-xl font-bold mb-4">Caja {{ numero }}</h2>

    <!-- Turnos Pendientes -->
    <div class="mb-6">
      <h3 class="text-lg font-bold mb-2">Turnos Pendientes</h3>
      <div v-if="turnosPendientes.length">
        <div v-for="turno in turnosPendientes" :key="turno.id" class="mb-4">
          <p>Turno: <span class="font-bold">{{ turno.id }}</span></p>
          <p>Razón: <span class="font-bold">{{ turno.razon }}</span></p>
          <button
            @click="aceptarTurno(turno)"
            class="bg-green-500 text-white px-4 py-2 rounded hover:bg-green-600 mt-2"
          >
            Aceptar Turno
          </button>
        </div>
      </div>
      <p v-else class="text-gray-500">No hay turnos pendientes para esta caja.</p>
    </div>

    <!-- Turnos Aceptados -->
    <div>
      <h3 class="text-lg font-bold mb-2">Turnos en Curso</h3>
      <div v-if="turnosAceptados.length">
        <div v-for="turno in turnosAceptados" :key="turno.id" class="mb-4">
          <p>Turno: <span class="font-bold">{{ turno.id }}</span></p>
          <p>Razón: <span class="font-bold">{{ turno.razon }}</span></p>
          <button
            @click="finalizarTurno(turno)"
            class="bg-red-500 text-white px-4 py-2 rounded hover:bg-red-600 mt-2"
          >
            Finalizar Turno
          </button>
        </div>
      </div>
      <p v-else class="text-gray-500">No hay turnos en curso para esta caja.</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    numero: {
      type: Number,
      required: true,
    },
    turnosPendientes: {
      type: Array,
      required: true,
    },
    turnosAceptados: {
      type: Array,
      required: true,
    },
  },
  methods: {
    aceptarTurno(turno) {
      this.$emit('aceptar-turno', turno);
    },
    finalizarTurno(turno) {
      this.$emit('finalizar-turno', turno);
    },
  },
};
</script>
