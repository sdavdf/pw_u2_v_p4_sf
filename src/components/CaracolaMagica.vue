<template>
  <div class="magic-ball">
    <h1 class="title">Caracola Mágica</h1>
    <img v-if="rutaImagen" :src="rutaImagen" alt="No hay imagen" />
    <div class="overlay"></div>

    <div class="container">
      <input v-model="pregunta" type="text" placeholder="Hazme una pregunta" />
      <p>Recuerda terminar con un enter la pregunta</p>

      <div class="question-container">
        <h2>{{ pregunta }}</h2>
        <h1>{{ respuestaP }}</h1>
      </div>
    </div>

    <div class="results-container">
      <div class="result">
        <h3>Intentos de "Sí": {{ conteoSi }}</h3>
      </div>
      <div class="result">
        <h3>Intentos de "No": {{ conteoNo }}</h3>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pregunta: "",
      respuestaP: "",
      rutaImagen: null,
      conteoSi: 0,
      conteoNo: 0,
    };
  },

  watch: {
    pregunta(value) {
      if (value.includes("?")) {
        this.respuestaP = "Esperando...";
        this.rutaImagen = null;
        this.consumirAPI();
      }
    },
  },

  methods: {
    consumirAPI() {
      fetch("https://yesno.wtf/api")
        .then((response) => response.json())
        .then((data) => {
          const { answer, image } = data;
          this.respuestaP = answer;
          this.rutaImagen = image;
          this.pregunta = "";

          if (answer === "yes") {
            this.conteoSi++;
          } else if (answer === "no") {
            this.conteoNo++;
          }

          if (this.conteoSi === 3) {
            this.respuestaP = "¡Has ganado el juego!";
            this.conteoSi = 0;
            this.conteoNo = 0;
          } else if (this.conteoNo === 3) {
            this.respuestaP = "Has perdido el juego :(";
            this.conteoSi = 0;
            this.conteoNo = 0;
          }
        })
        .catch((error) => {
          console.error(error);
          this.respuestaP = "Error al consultar la API";
          this.rutaImagen = null;
        });
    },
  },
};
</script>

<style>
.magic-ball {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background-color: #222;
  color: #fff;
}

.title {
  font-size: 2rem;
  margin-bottom: 1rem;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.4);
  z-index: -1;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 2rem;
}

input {
  width: 250px;
  padding: 10px 15px;
  border-radius: 5px;
  border: none;
  margin-bottom: 1rem;
}

p {
  font-size: 1.2rem;
  margin: 0;
}

.question-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 2rem;
  padding: 1rem;
  background-color: #333;
  border-radius: 5px;
  width: 300px;
}

.question-container h2 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
}

.question-container h1 {
  font-size: 2rem;
  margin-top: 0;
}

.results-container {
  display: flex;
  justify-content: center;
}

.result {
  margin: 0 1rem;
}

.results-container h3 {
  font-size: 1.2rem;
  margin: 0;
}
</style>
