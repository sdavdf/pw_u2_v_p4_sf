<template>
  <form action="">
    <input type="text" id="resultado" v-model="entradaUsuario" />
    <button @click="entrada('+')">+</button>
  </form>
</template>

<script>
export default {
  data() {
    let entradaUsuario = "";
    return {
      entradaUsuario,
    };
  },
};
</script>

<style>
</style>