<template>
  <div class="min-h-screen bg-gray-100 text-gray-800">
    <div class="container mx-auto py-10">
      <h1 class="text-3xl font-bold text-center mb-6">Sistema de Turnos Bancarios</h1>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <RequestTurn @nuevo-turno="agregarTurno" />
        <TurnList :turnos="turnosAceptados" />
      </div>
      <h2 class="text-2xl font-bold text-center my-6">Paneles de Cajas</h2>
      <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
        <BoxPanel
          v-for="caja in cajas"
          :key="caja"
          :numero="caja"
          :turnos-pendientes="turnosPendientes.filter(turno => turno.caja === caja)"
          :turnos-aceptados="turnosAceptados.filter(turno => turno.caja === caja)"
          @aceptar-turno="aceptarTurno"
          @finalizar-turno="finalizarTurno"
        />
      </div>
    </div>
  </div>
</template>

<script>
import RequestTurn from './components/RequestTurn.vue';
import TurnList from './components/TurnList.vue';
import BoxPanel from './components/BoxPanel.vue';

export default {
  data() {
    return {
      turnosPendientes: [], // Turnos en espera de aceptación
      turnosAceptados: [], // Turnos aceptados y en curso
      cajas: [1, 2, 3, 4], // Número de cajas disponibles
    };
  },
  methods: {
    agregarTurno(turno) {
      this.turnosPendientes.push(turno); // Añadir a los turnos pendientes
    },
    aceptarTurno(turnoAceptado) {
      this.turnosPendientes = this.turnosPendientes.filter(
        turno => turno.id !== turnoAceptado.id
      );
      this.turnosAceptados.push(turnoAceptado);
    },
    finalizarTurno(turnoFinalizado) {
      this.turnosAceptados = this.turnosAceptados.filter(
        turno => turno.id !== turnoFinalizado.id
      );
    },
  },
  components: {
    RequestTurn,
    TurnList,
    BoxPanel,
  },
};
</script>
