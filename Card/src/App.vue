<template>
  <div id="app">
    <h1>Lista de Películas</h1>
    <TarjetaPelicula 
      v-for="pelicula in peliculas" 
      :key="pelicula.id" 
      :pelicula="pelicula" 
      @actualizar_megusta="actualizarMeGusta" 
    />
  </div>
</template>

<script>
import TarjetaPelicula from './components/CardComponent.vue';

export default {
  components: {
    TarjetaPelicula
  },
  data() {
    return {
      peliculas: [
        {
          id: 1,
          titulo: "El Padrino",
          descripcion: "Un drama de crimen y mafia.",
          portada: "https://via.placeholder.com/150",
          likes: 10
        },
        {
          id: 2,
          titulo: "Interstellar",
          descripcion: "Viajes espaciales y agujeros de gusano.",
          portada: null,
          likes: 5
        }
      ]
    };
  },
  methods: {
    actualizarMeGusta({ id, likes }) {
      const pelicula = this.peliculas.find(p => p.id === id);
      if (pelicula) {
        pelicula.likes = likes;
      }
    }
  }
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  background-color: #0a192f;
  color: white;
  padding: 20px;
}
</style>