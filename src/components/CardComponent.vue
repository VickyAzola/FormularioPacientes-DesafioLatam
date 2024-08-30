<script>
export default {
  name: 'CardComponent',
  props: ['paciente', 'fecha', 'hora', 'gravedad', 'motivo'],
  emits: ['removeCard'],
  methods: {
    removeCard() {
      this.$emit('removeCard');
    }
  }
}
</script>

<template>
  <div class="card" :class="gravedad === 'Baja' ? 'green' : gravedad === 'Media' ? 'yellow' : 'red'">
    <b>Paciente</b>
    <p>{{ paciente }}</p>
    <b>Fecha</b>
    <p>{{ fecha }}</p>
    <b>Hora</b>
    <p>{{ hora }}</p>
    <b>Motivo</b>
    <p>{{ motivo }}</p>
    <button @click="removeCard">Eliminar</button>
  </div>
</template>

<style scoped>
.card {
  min-width: 11rem;
  padding: 1rem;
  border-radius: .5rem;
  text-align: center;
}

b {
  font-weight: bold;
  text-transform: uppercase;
}

p {
  margin-block: .5rem;
}

button {
  margin-top: 1rem;
  padding: .3rem 1rem;
}

.yellow {
  background-color: rgb(247, 247, 129);
}

.green {
  background-color: rgb(140, 226, 140);
}

.red {
  background-color: rgb(238, 125, 125);
}
</style>
