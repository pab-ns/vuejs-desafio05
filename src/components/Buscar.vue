<template>
  <div>
    <label for="input">Nombre: </label>
    <input type="text" placeholder="Buscar..." v-model="nombreBuscador" />
    <button @click="buscarPokemon()">Buscar</button>
  </div>
</template>

<script>
export default {
  name: "Buscar",
  data: () => ({
    // capturar dato (dentro de script)
    nombreBuscador: "",
  }),
  methods: {
    buscarPokemon() {
      console.log(this.nombreBuscador);
    },
  },
};
</script>

<style></style>
