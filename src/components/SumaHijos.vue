<template>
  <div>
    <h2>Numero Hijo: {{ number }}</h2>
    <button @click="sumar">Sumar</button>
  </div>
</template>

<script>
export default {
    name:'SumaHijos',
    data () {
        return {
            number: Math.floor(Math.random() * 50) + 1
        }
    },
    methods : {
        sumar() {
            this.$emit('sumar',this.number)
        }
    }
}
</script>

<style>

</style>