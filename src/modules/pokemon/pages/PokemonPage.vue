<template>
  <h1 v-if="!pokemonCorrecto">Espere por favor ....</h1>
  <div v-else>
    <!--siempre debe posicionarse debajo de una directiva V-IF-->
    <h1>Juego Pokemon</h1>
    <PokemonImg :pokemonid="pokemonCorrecto.id" :muestraPokemon="showPokemon" />
    <PokemonOps
      :opciones="pokeArreglo"
      @seleccionado="revisarSeleccion($event)"
    />
    <div v-if="juegoTerminado" class="game-gana">
      <p>Has ganado!</p>
    </div>
    <div v-if="perdiste" class="game-termina">
      <p>Perdiste!</p>
    </div>

    <p>Intentos: {{ intento }}</p>
    <p>Puntaje: {{ puntajeAcumulado }}</p>

    <button @click="reiniciarJuego" class="reiniciar-button">
      Reiniciar Juego
    </button>
  </div>
</template>

<script>
import PokemonImg from "../components/PokemonImg.vue";
import PokemonOps from "../components/PokemonOps.vue";
import obtenerFachadaPokemons from "../helpers/clientePokemonApi";

export default {
  data() {
    return {
      pokeArreglo: [],
      pokemonCorrecto: null,
      showPokemon: false,
      puntajeAcumulado: 0,
      intento: 3,
      juegoTerminado: false,
      perdiste: false,
    };
  },

  components: {
    PokemonOps,
    PokemonImg,
  },
  methods: {
    async cargaJuegoInicial() {
      const arreglo = await obtenerFachadaPokemons();
      console.log(this.pokeArreglo);
      this.pokeArreglo = arreglo;

      const indicePokemon = Math.floor(Math.random() * 4);
      this.pokemonCorrecto = this.pokeArreglo[indicePokemon];
    },

    revisarSeleccion(idSeleccionado) {
      console.log("evento en el padre");

      if (idSeleccionado == this.pokemonCorrecto.id) {
        this.showPokemon = true;

        if (this.intento === 3) {
          this.puntajeAcumulado = 5;
          this.juegoTerminado = true;
        } else if (this.intento === 2) {
          this.puntajeAcumulado = 2;
          this.juegoTerminado = true;
        } else if (this.intento === 1) {
          this.puntajeAcumulado = 1;
          this.juegoTerminado = true;
        } else if (this.intento <= 0) {
          this.puntajeAcumulado = 0;
          this.perdiste = perdiste;
        }
      }
      this.intento--;
    },

    async reiniciarJuego() {
      this.arreglo = [];
      this.pokemonCorrecto = null;
      this.showPokemon = false;
      this.intento = 3;
      this.puntajeAcumulado = 0;
      (this.juegoTerminado = false), (this.perdiste = false);
      await this.cargaJuegoInicial();
    },
  },

  mounted() {
    console.log("se monto el componente");
    this.cargaJuegoInicial();
  },
};
</script>

<style scoped>
.reiniciar-button {
  margin-top: 10px;
  padding: 8px 16px;
  background-color: #dded85;
  color: white;
  font-size: 14px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
.reiniciar-button:hover {
  background-color: aquamarine;
}

.game-termina {
  margin-top: 20px;
  font-weight: bold;
  color: rgb(255, 0, 0);
}

.game-gana {
  margin-top: 20px;
  font-weight: bold;
  color: blue;
}
</style>