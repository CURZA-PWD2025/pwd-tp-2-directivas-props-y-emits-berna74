<template>
  <div class="cartelera">
    CATELERA
  </div>
  <div class="contenedor">
    <CardComponent
      v-for="pelicula in peliculas"
      :key="pelicula.id"
      :movie="pelicula"
      :yaLikeado="likeados.includes(pelicula.id)"
      @like="sumarLike"
    />
  </div>
       
</template>

<script setup lang="ts">
import { ref } from 'vue'
import CardComponent from './components/CardComponent.vue'
import type { Pelicula } from './interfaces/Pelicula'
import peliculasData from './resources/peliculas' // 

// Ref reactivo con todas las películas
const peliculas = ref<Pelicula[]>(peliculasData)

// Lista de películas a las que se les dio like
const likeados = ref<number[]>([])

// Función para incrementar likes y evitar múltiples likes
function sumarLike(id: number) {
  const peli = peliculas.value.find(p => p.id === id)
  if (peli && !likeados.value.includes(id)) {
    peli.likes++
    likeados.value.push(id)
  }
}
</script>

<style scoped>
.cartelera{
  padding: 10 20;
  color: white;
  font-size: 4.5em;
  font-weight: 400;
  }
.contenedor {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}
</style>