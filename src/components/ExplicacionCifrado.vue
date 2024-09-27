<template>
  <div class="explicacion-cifrado">
    <h3>{{ titulo }}</h3>
    <p>{{ descripcion }}</p>
  </div>
</template>

<script>
export default {
  name: "ExplicacionCifrado",
  props: {
    titulo: {
      type: String,
      required: true,
    },
    descripcion: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
.explicacion-cifrado {
  margin-top: 15px;
  padding: 10px;
  background-color: #f9f9f9;
  border-radius: 5px;
  border: 1px solid #ddd;
}

h3 {
  margin-bottom: 10px;
  color: #333;
  font-size: 18px;
}

p {
  font-size: 16px;
  color: #555;
}
</style>
