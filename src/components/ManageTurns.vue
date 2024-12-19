<template>
    <div class="bg-white p-6 rounded-lg shadow-md">
      <h2 class="text-xl font-bold mb-4">Gestionar Turnos</h2>
      <div v-if="turnos.length" class="mb-4">
        <p class="text-lg">
          Turno Actual: <span class="font-bold">{{ turnos[0].id }}</span>
        </p>
        <p class="text-lg">Caja: <span class="font-bold">{{ turnos[0].caja }}</span></p>
        <button
          @click="completarTurno"
          class="bg-green-500 text-white px-4 py-2 rounded hover:bg-green-600 mt-4"
        >
          Completar Turno
        </button>
      </div>
      <p v-else class="text-gray-500">No hay turnos en espera.</p>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      turnos: {
        type: Array,
        required: true,
      },
    },
    methods: {
      completarTurno() {
        this.turnos.shift(); // Eliminar el turno actual
        this.$emit('actualizar-turnos', this.turnos);
      },
    },
  };
  </script>
  