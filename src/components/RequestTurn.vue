<template>
  <div class="bg-white p-6 rounded-lg shadow-md">
    <h2 class="text-xl font-bold mb-4">Solicitar Turno</h2>
    <select v-model="razon" class="w-full mb-4 p-2 border border-gray-300 rounded">
      <option disabled value="">Seleccione una razón</option>
      <option value="Renovación de tarjeta">Renovación de tarjeta</option>
      <option value="Pérdida de cuenta">Pérdida de cuenta</option>
      <option value="Rehacer firma">Rehacer firma</option>
      <option value="Cambio de PIN">Cambio de PIN</option>
      <option value="Cobros no reconocidos">Cobros no reconocidos</option>

    </select>
    <button
      @click="generarTurno"
      :disabled="!razon"
      class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600"
    >
      Generar Turno
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      razon: '',
    };
  },
  methods: {
    generarTurno() {
      const turno = {
        id: `T${Math.floor(Math.random() * 1000).toString().padStart(3, '0')}`,
        razon: this.razon,
        caja: Math.floor(Math.random() * 4) + 1,
      };
      this.$emit('nuevo-turno', turno);
      this.razon = ''; // Reiniciar selección
    },
  },
};
</script>
