<template>
  <div>
    <img
      src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/International_Pok%C3%A9mon_logo.svg/320px-International_Pok%C3%A9mon_logo.svg.png"
      alt=""
    />
    <h1>PokeGuía</h1>

    <Buscar />
    <Img />
    <Movimientos />
    <Habilidades />
  </div>
</template>

<script>
import Buscar from "./components/Buscar.vue";
import Img from "./components/Img.vue";
import Movimientos from "./components/Movimientos.vue";
import Habilidades from "./components/Habilidades.vue";

export default {
  name: "App",
  components: { Buscar, Img, Movimientos, Habilidades },
  data: () => ({}),
  created() {
    // fetch recibe un 1er parametro que es la url. Luego lo "transforma" de Json a JS
    fetch("https://pokeapi.co/api/v2/pokemon/pikachu")
      .then((response) => {
        // esto devuelve una promsesa
        return response.json();
      })
      .then((datosPokemon) => {
        console.log({ ConFetch: datosPokemon });
      });
  },
};
</script>

<style>
body {
  font-family: sans-serif;
  text-align: center;
}
</style>
