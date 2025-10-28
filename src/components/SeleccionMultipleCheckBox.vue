<template>
  <div>
    <h1>Seleccion Multiple</h1>
    <button @click="generarCheckBox">Generar Checkbox</button>
    <form style="display: flex; gap: 10px; flex-wrap: wrap;">
      <div v-for="(check, i) in checkboxs" :key="i">
        <input 
          type="checkbox" 
          :id="'check-' + i" 
          :value="check"
          @change="suma($event, check)"
        >
        <label :for="'check-' + i">{{ check }}</label>
      </div>
    </form>
    <p>La suma seleccionada: {{ count }}</p>
  </div>
</template>

<script>
export default {
  name: 'SeleccionMultipleCheckBox',
  data() {
    return {
      checkboxs: [],
      count: 0
    }
  },
  methods: {
    generarCheckBox() {
      let cantidad = Math.floor(Math.random() * 10) + 1
      let aux = []

      for (let i = 0; i < cantidad; i++) {
        aux.push(Math.floor(Math.random() * 50) + 1)
      }
      this.checkboxs = aux
      this.count = 0  
    },
    suma(event, valor) {
      if (event.target.checked) {
        this.count += valor
      } else {
        this.count -= valor
      }
    }
  }
}
</script>
