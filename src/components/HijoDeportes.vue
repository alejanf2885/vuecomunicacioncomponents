<template>
  <div>
    <h1>Hijo deporte</h1>
    <p>{{ nombredeporte }}</p>
    <button @click="seleccionarFav">
      Seleccionar Favorito
    </button>
  </div>
</template>

<script>
export default {
    name:'HijoDeportes',
    props: ['nombredeporte',],
    methods : {
      seleccionarFav () {
        console.log('Soy el hijo: ' + this.nombredeporte)
        this.$emit('setFavorito',this.nombredeporte)
        
      }
    }
   
}
</script>

<style>

</style>