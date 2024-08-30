<script>
import FormComponent from './components/FormComponent.vue'
import CardComponent from './components/CardComponent.vue'

export default {
  components: {
    FormComponent, //recolecta la data
    CardComponent //muestra la data
  },
  data() {
    return {
      cards: [] 
    };
  },
  methods: {
    addCard(paciente) { //paciente objeto que contiene paciente, fecha, hora...
      this.cards.push(paciente); 
    },
    removeCard(index) {
      this.cards.splice(index, 1); 
    }
  }
}
</script>

<template>
  <div>
    <FormComponent @submit-form="addCard" />
    <p v-show="cards.length === 0">Aun no hay consultas registradas</p>
    <div class="cards-container">
      <div v-for="(card, index) in cards" :key="index">
        <CardComponent
          :paciente="card.paciente"
          :fecha="card.fecha"
          :hora="card.hora"
          :gravedad="card.gravedad"
          :motivo="card.motivo"
          @removeCard="removeCard(index)"
        />
      </div>
    </div>
  </div>
</template>

<style scoped>
.cards-container {
  margin: 2rem 0;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1rem;
}

p {
  color: red;
  text-align: center;
  margin-top: 2rem;
}
</style>
