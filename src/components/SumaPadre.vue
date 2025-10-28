<template>
  <div>
    <h1>Numeros Padre</h1>
    <h2>La suma es: {{ count }}</h2>
    <button @click="agregarHijo">Nuevo numero</button>

    <div class="list">
        <SumaHijos 
        v-for="(hijo, index) in hijos" 
        :key="index"
        @sumar="sumar"
      />
        
    </div>
    <p>Hoka</p>
  </div>
</template>

<script>
import SumaHijos from './SumaHijos.vue';

export default {
    name: 'SumaPadre',
    data () {
        return {
            count: 0,
            hijos:[{},{},{},{},]
        }
    },
    components : {
        SumaHijos
    },
    methods : {
        sumar(number) {
            this.count += number;
        },
        agregarHijo() {
            this.hijos.push({})

        }
    }
}
</script>

<style>

</style>