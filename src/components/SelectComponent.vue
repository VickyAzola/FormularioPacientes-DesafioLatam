<script>
  export default {
    name: 'SelectComponent',
    props: ['label', 'forlabel', 'id', 'modelValue', 'options'],
    emits: ['update:modelValue'],
    methods: {
      updateValue(event) {
        this.$emit('update:modelValue', event.target.value);
      }
    }
  }
</script>

<template>
  <div class="flex-group">
    <label :for="forlabel" :class="!modelValue ? 'red' : 'black'">{{ label }}</label>
    <select :value="modelValue" @change="updateValue" :id="id" required>
      <option v-for="(option, index) in options" :key="index" :value="option">
        {{ option }}
      </option>
    </select>
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

select {
  padding: .5rem;
  border-radius: .2rem;
  border: 1px solid gray;
  flex: 1;
}
</style>