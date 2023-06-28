<template>
  <EjemploApi />
</template>

<script>
import EjemploApi from "./components/EjemploApi.vue";

export default {
  //Este componente se puede utilizar en diferentes paginas
  //Configurar la opcion components
  components: {
    //ExampleSelective,
    //ExampleFor,
    EjemploApi,
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