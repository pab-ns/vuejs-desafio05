<template>
  <div>
    <img
      src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/International_Pok%C3%A9mon_logo.svg/320px-International_Pok%C3%A9mon_logo.svg.png"
      alt=""
    />
    <h1>PokeGuía</h1>

    <label for="">Nombre: </label>
    <input type="text" v-model="pokemonName" placeholder="Pikachu" />
    <button @click="pokemonBuscar()">Buscar</button>

    <img :src="pokemon.sprites.front_default" class="poke-img mx-auto" alt="" />

    <div class="row">
      <!-- mov -->
      <div class="col-6">
        <h2>Movimientos</h2>
        <p v-for="(pokemonMove, $index) in moves" :key="$index">
          {{ pokemonMove.move.name }}
        </p>
      </div>

      <!-- habili -->
      <div class="col-6">
        <h2>Habilidades</h2>
        <p v-for="(pokemonAbility, $index) in abilities" :key="$index">
          {{ pokemonAbility.ability.name }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    //   por defecto será este
    pokemonName: "pikachu",
    pokemon: null,
  }),

  methods: {
    pokemonBuscar() {
      console.log(this.pokemonName);
      this.fetchPokemon();
    },

    fetchPokemon() {
      // fetch recibe un 1er parametro que es la url. Luego lo "transforma" de Json a JS
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemonName}`)
        .then((response) => {
          // esto devuelve una promsesa
          return response.json();
        })
        // .then((datosPokemon) => {
        //   console.log({ ConFetch: datosPokemon });
        // });
        .then((json) => (this.pokemon = json));
    },
  },

  computed: {
    moves() {
      return this.pokemon.moves;
    },
    abilities() {
      return this.pokemon.abilities;
    },
  },

  created() {
    // Llamar al metodo fetchPokemon
    this.fetchPokemon();
  },
};
</script>

<style>
body {
  font-family: sans-serif;
  text-align: center;
}
.poke-img {
  display: block;
}
</style>
