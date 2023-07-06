<template>
  <div>
    <h1>{{ mensaje }}</h1>
    <input v-model="valor" type="text" placeholder="Escribe algo" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      valor: "",
      mensaje: "",
    };
  },
  watch: {
    valor(nuevoValor, antiguoValor) {
    console.log("valor antogiop" + antiguoValor);
      this.mensaje = "El valor ha cambiado: " + nuevoValor;
    },
  },
};
</script>
