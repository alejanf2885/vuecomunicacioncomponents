<template>
  <div>
    <h1>Padre Deporte</h1>
    <h3 v-if="hijoFavorito != ''">Hijo favorito: {{ hijoFavorito }}</h3>
    <ul>
        <li v-for="deporte in deportes" :key="deporte">
            <HijoDeportes v-on:setFavorito="setFavorito" :nombredeporte="deporte" />
        </li>
    </ul>
    
  </div>
</template>

<script>
import HijoDeportes from './HijoDeportes.vue';

export default {
    name:'PadreDeportes',
    components: {
        HijoDeportes
    },
     data() {
        return{
            deportes: ['futbol','voley','tenis','atletismo'],
            hijoFavorito: ''
        }
    },
    methods : {
        setFavorito (deporteFav) {
            console.log('yo soy el padre')
            this.hijoFavorito = deporteFav
        }
    }
}
</script>

<style>

</style>