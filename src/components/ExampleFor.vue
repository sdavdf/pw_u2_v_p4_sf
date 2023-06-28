<template>
  <ul>
    <li v-for="(a,i) in countries" v-bind:key="a"> {{i}} -{{ a.code }} - {{ a.name }}</li>
  </ul>
</template>

<script>
export default {
  data() {
    let countries = [
      {
        code: "es",
        name: "Spaine",
      },
      {
        code: "en",
        name: "UK",
      },
      {
        code: "fr",
        name: "France",
      },
      {
        code: "it",
        name: "Italy",
      },
    ];
    return {
      countries,
    };
  },
};
</script>

<style>
</style>