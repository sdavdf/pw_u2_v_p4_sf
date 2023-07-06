<template>
  
  <div class="contenedorOpciones">
    <ul>
        <!--
            <li>p1</li>
        <li>p2</li>
        <li>p3</li>
        <li>p4</li>
        -->
        <li v-for="pokemon in opciones" :key="pokemon.id" @click="$emit('seleccionado',pokemon.id)">{{ pokemon.nombre }}</li>
    </ul>
  </div>
    
</template>

<script>
export default {

    data() {
    return {
      intentos: 0, // Nueva propiedad para rastrear los intentos
      puntos: 0, // Nueva propiedad para almacenar la puntuación acumulada
    };
  },

    props:{
        opciones:{
            type: Array,
            required: true
        }
    },

    methods:{
        pruebaEvento(){
            console.log('prueba de evento')
        }
    },

    revisarSeleccion(idSeleccionado) {
      // ...

      this.intentos++; // Incrementar el número de intentos

      // Calcular y asignar los puntos según el número de intentos
      switch (this.intentos) {
        case 1:
          this.puntos += 5;
          break;
        case 2:
          this.puntos += 2;
          break;
        case 3:
          this.puntos += 1;
          break;
      }

        this.$emit('seleccionado', idSeleccionado);
    }

}
</script>

<style>

ul{
    list-style-type: none;
}

li{
    border: 1px solid rgba(0,0,0,0.2);
    border-radius: 4px;
    background-color: white;
    margin-bottom: 10px;
    height: 30px;
    width: 200px;
    cursor: pointer;
    
       
}

li:hover{
    background-color: cornflowerblue;
}

.contenedorOpciones{
    display: flex;
    justify-content: center;
}

</style>