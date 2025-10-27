<template>
  <div>
    <h1>Padre Deporte</h1>
    <ul>
        <li v-for="deporte in deportes" :key="deporte">
            <HijoDeportes :nombredeporte="deporte" />
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
            deportes: ['futbol','voley','tenis','atletismo']
        }
    }
}
</script>

<style>

</style>