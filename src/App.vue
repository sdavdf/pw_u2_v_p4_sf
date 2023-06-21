<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <h2>Calculadora con VUE</h2>
  <calculadoraCom />
</template>

<script>
import CalculadoraCom from "./components/CalculadoraCom.vue";


export default {
  //Este componente se puede utilizar en diferentes paginas
  //Configurar la opcion components
  name: "App",
  components: {
    CalculadoraCom,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>