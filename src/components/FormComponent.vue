<script>
import InputComponent from './InputComponent.vue'
import SelectComponent from './SelectComponent.vue'

export default {
  name: 'FormComponent',
  components: {
    InputComponent,
    SelectComponent
  },
  emits: ['submit-form'],
  data() {
    return {
      paciente: '',
      fecha: '',
      hora: '',
      gravedad: '',
      gravedadOptions: ['Baja', 'Media', 'Alta'],
      motivo: ''
    }
  },
  methods: {
    isFormValid() {
      return (
        this.paciente &&
        this.fecha &&
        this.hora &&
        this.gravedad &&
        this.motivo
      );
    },
    handleSubmit() {
      if (this.isFormValid()) {
        this.$emit('submit-form', {
          paciente: this.paciente,
          fecha: this.fecha,
          hora: this.hora,
          gravedad: this.gravedad,
          motivo: this.motivo
          //envia esta data al padre (pacientes)
        });

        //limpiar el formulario
        this.paciente = ''
        this.fecha = ''
        this.hora = ''
        this.gravedad = ''
        this.motivo = ''
      }
    }
  }
}
</script>

<template>
  <form @submit.prevent="handleSubmit">
  <div class="form-container">
    <InputComponent
        label="Paciente"
        forlabel="paciente"
        type="text"
        id="paciente"
        v-model="paciente"
      />
      <InputComponent
        label="Fecha"
        forlabel="fecha"
        type="date"
        id="fecha"
        v-model="fecha"
      />
      <InputComponent
        label="Hora"
        forlabel="hora"
        type="time"
        id="hora"
        v-model="hora"
      />
      <SelectComponent 
        label="Gravedad"
        forlabel="gravedad"
        id="gravedad"
        v-model="gravedad"
        :options="gravedadOptions"
      />
      <InputComponent
        label="Motivo"
        forlabel="motivo"
        type="text"
        id="motivo"
        v-model="motivo"
      />
  </div>
    <button :disabled="!isFormValid()">Agregar</button>
  </form>
</template>

<style scoped>
form {
  border: 1px solid lightgrey;
  padding: 1.5rem;
  border-radius: .5rem;
}

.form-container {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

button {
  margin-inline: auto;
  margin-top: 1rem;
  display: block;
  padding: .3rem 1rem;
}
</style>