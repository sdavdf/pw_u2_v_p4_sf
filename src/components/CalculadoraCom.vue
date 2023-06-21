<template>
  <div class="calculadora">
    <input type="text" id="resultado" v-model="entradaUsuario" />
    <button @click="entrada('+')">+</button>
    <button @click="entrada(7)">7</button>
    <button @click="entrada(8)">8</button>
    <button @click="entrada(9)">9</button>
    <button @click="entrada('/')">/</button>
    <button @click="entrada(4)">4</button>
    <button @click="entrada(5)">5</button>
    <button @click="entrada(6)">6</button>
    <button @click="entrada('*')">*</button>
    <button @click="entrada(1)">1</button>
    <button @click="entrada(2)">2</button>
    <button @click="entrada(3)">3</button>
    <button @click="entrada('-')">-</button>
    <button @click="entrada(0)">0</button>
    <button @click="limpiarEntrada()">C</button>
    <button @click="calculoResultado()">=</button>
  </div>
</template>

<script>
export default {
  name: "CalculadoraCom",
  data() {
    return {
      entradaUsuario: "",
    };
  },
  computed: {
    resultado() {
      try {
        console.log("Entro al metodo calcular el resultado computado");
        return eval(this.entradaUsuario);
      } catch (error) {
        return "";
      }
    },
  },
  methods: {
    entrada(valor) {
      if (valor === "=") {
        this.calculoResultado();
      } else {
        this.entradaUsuario += String(valor);
      }
    },
    limpiarEntrada() {
      this.entradaUsuario = "";
    },
    calculoResultado() {
      this.entradaUsuario = String(this.resultado);
    },
  },
};
</script>




<style>
.calculadora {
  max-width: 300px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  text-align: center;
  background-color: cadetblue;
  padding: 20px;
  border-radius: 20px;
  box-shadow: 5px 10px 10px 0px black;
}

.calculadora input {
  width: 100%;
  margin-bottom: 10px;
  padding: 5px;
  font-size: 18px;
}

.calculadora button {
  width: 50px;
  height: 50px;
  margin: 10px;
  font-size: 18px;
}

h1 {
  text-align: center;
  background-color: rgb(189, 219, 148);
}
</style>