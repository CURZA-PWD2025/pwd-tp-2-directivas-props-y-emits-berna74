<template>
  <div class="card">
    <h3>{{ movie.titulo }}</h3>
    <img :src="movie.portada" alt="Portada de la película" />
    <p><strong>Director:</strong> {{ movie.director }}</p>
    <p><strong>Año:</strong> {{ movie.anio }}</p>
    <p><strong>Género:</strong> {{ movie.genero }}</p>
    <p><strong>Likes:</strong> ❤️ {{ movie.likes }}</p>
    <button
      @click="$emit('like', movie.id)"
      :disabled="yaLikeado"
    >
      {{ yaLikeado ? '¡Gracias por tu like!' : 'Me gusta ❤️' }}
    </button>
  </div>
</template>

<script setup lang="ts">
import type { Pelicula } from './components/Pelicula'

defineProps<{
  movie: Pelicula,
  yaLikeado: boolean
}>()

defineEmits<{
  (e: 'like', id: number): void
}>()
</script>

<style scoped>
.card {
  border: 1px solid #ddd;
  border-radius: 12px;
  padding: 16px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  max-width: 300px;
  transition: transform 0.2s;
  background-color: white;
}

.card:hover {
  transform: translateY(-4px);
}

.card img {
  width: 100%;
  height: auto;
  border-radius: 8px;
  margin: 8px 0;
}

button {
  margin-top: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  padding: 8px 12px;
  border-radius: 6px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
</style>