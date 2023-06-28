<template>
  <h1 v-if="edad < 18">eres menor</h1>
  <h1 v-else>eres mayor</h1>
</template>

<script>
export default {
  data() {
    let edad = 10;

    return {
      edad,
    };
  },

};
</script>

<style>
</style>