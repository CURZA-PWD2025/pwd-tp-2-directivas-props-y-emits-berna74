<template>
  <div class="tarjeta">
    <div class="portada" v-if="pelicula.portada">
      <img :src="pelicula.portada" :alt="pelicula.titulo" />
    </div>
    <div v-else class="sin-portada">Portada no disponible</div>
    
    <div class="detalles">
      <h3>{{ pelicula.titulo }}</h3>
      <p>{{ pelicula.descripcion }}</p>
      <button @click="alternarLike">{{ meGusta ? 'Quitar Me Gusta' : 'Me Gusta' }} ({{ meGustaCantidad }})</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    pelicula: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      meGusta: false,
      meGustaCantidad: this.pelicula.likes || 0
    };
  },
  methods: {
    alternarLike() {
      this.meGusta = !this.meGusta;
      this.meGustaCantidad += this.meGusta ? 1 : -1;
      this.$emit('actualizar_megusta', this.meGustaCantidad);
    }
  }
};
</script>

<style scoped>

.tarjeta {
  background: #0d1b2a;
  border: 1px solid #1b263b;
  border-radius: 8px;
  padding: 16px;
  max-width: 300px;
  text-align: center;
  box-shadow: 2px 2px 10px rgba(173, 216, 230, 0.2);
  color: #e0e1dd;
}
.portada img {
  width: 100%;
  border-radius: 8px;
}
.sin-portada {
  font-size: 14px;
  color: #a8dadc;
  padding: 20px;
  background: #1b263b;
  border-radius: 8px;
}
.detalles h3 {
  margin: 10px 0;
  color: #f5f5f5;
}
button {
  background: #0077b6;
  color: white;
  border: none;
  padding: 8px 12px;
  cursor: pointer;
  border-radius: 4px;
  font-weight: bold;
}
button:hover {
  background: #00b4d8;
}
</style>