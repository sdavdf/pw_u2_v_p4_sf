<template>
  <h1>Caracola Mágica</h1>
  <img v-if="rutaImagen" :src="rutaImagen" alt="No hay imagen" />

  <div class="bg-dark"></div>

  <div class="contenedor">
    <input v-model="pregunta" type="text" placeholder="Hazme una pregunta" />

    <p>Recuerda terminar con un enter la pregunta</p>
   

    <div>
      <h2>{{ pregunta }}</h2>
      <h1>{{ respuestaP }}</h1>
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
    };
  },

  watch: {
    pregunta(value, oldValue) {
      console.log(value);
      console.log(oldValue);

      if (value.includes("?")) {
        console.log("Consumir el API");
        this.respuestaP = "Esperando....."
        this.consumirAPI();
      }
      this
      
    },
  },

  methods: {
    async consumirAPI() {
      const respuesta = await fetch("https://yesno.wtf/api").then((r) =>
        r.json()
      );
      console.log(respuesta);

      const { answer, image } = respuesta;
      console.log(answer);
      console.log(image);

      this.respuestaP = answer;
      this.rutaImagen = image;
      this.pregunta = '';

      
    },
  },
};
</script>

<style>
img, .bg-dark {
  height: 100vh;
  width: 100vw;
  left: 0px;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  top: 0px;
}

.bg-dark {

  background-color: rgba(0, 0, 0, 0.4);
}

.contenedor{
  position: relative;

}

input{
  width: 250xp;
  padding: 10px 15px;
  border-radius: 5px;
  border: none;

}

p, h1, h2{
  color: white;
  font-family: Arial, Helvetica, sans-serif;
}

p{
  font-size: 40px;
  margin-top: 0px;
}


</style>