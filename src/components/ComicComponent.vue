<template>
  <div>
    <h3>Hijo component</h3>
    <p>{{ comic.titulo }}</p>
    <img :src="comic.imagen" alt="" />
    <p>{{ comic.descripcion }}</p>
    <h4
      :class="{
        red: comic.year <= 2000,
        green: comic.year > 2000,
      }"
    >
      <p>Año: {{ comic.year }}</p>
    </h4>
    <button @click="seleccionarfavorito">
        Seleccionar Favorito
    </button>
    <button @click="deleteComic">
        Eliminar 
    </button>
  </div>
</template>

<script>
export default {
  name: "ComicComponent",
  components: {},
  props: ["comic","index"],
  methods : {
    seleccionarfavorito () {
        this.$emit('seleccionarFavorito',this.comic)
    },
    deleteComic() {
        this.$emit('deleteComic',this.index)
    }

  }
  
};
</script>

<style>
@import "./../assets/css/comics.css";
</style>
