<script>
  export default {
    name: 'InputComponent',
        //modelValue trae el valor desde el padre mediante el v-model
    props: ['label', 'forlabel', 'type', 'id', 'modelValue'], 
    emits: ['update:modelValue'],
    methods: {
      //se ejecuta cada vez que el valor del @input cambia
      updateValue(event) { 
        this.$emit('update:modelValue', event.target.value);
        //update:modelValue envia el valor actualizado al padre
      }
    }
  }
</script>

<template>
  <div class="flex-group">
    <label :for="forlabel" :class="!modelValue ? 'red' : 'black'">{{ label }}</label>
    <input :type="type" :id="id" :value="modelValue" @input="updateValue" required />
  </div>
</template>

<style scoped>
.flex-group {
  display: flex;
  flex-direction: column;
  text-align: center;
  flex: 1;
}

label {
  margin-bottom: .5rem;
  font-weight: bold;
}

.red {
  color: red;
}

.black {
  color: black;
}

input {
  padding: .5rem;
  border-radius: .2rem;
  border: 1px solid gray;
  flex: 1;
}
</style>