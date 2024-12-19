<template>
  <div class="bg-white p-6 rounded-lg shadow-md">
    <h2 class="text-xl font-bold mb-4">Lista de Turnos Aceptados</h2>
    <table class="table-auto w-full text-left border-collapse">
      <thead>
        <tr>
          <th class="border p-2">Turno</th>
          <th class="border p-2">Razón</th>
          <th class="border p-2">Caja</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="turno in turnos" :key="turno.id">
          <td class="border p-2">{{ turno.id }}</td>
          <td class="border p-2">{{ turno.razon }}</td>
          <td class="border p-2">{{ turno.caja }}</td>
        </tr>
      </tbody>
    </table>
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
};
</script>
