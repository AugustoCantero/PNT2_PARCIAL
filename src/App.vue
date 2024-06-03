<template>
  <div class="container mt-3">
    <div class="jumbotron">
        <h1>Parcial</h1>
        <br>


        <h1></h1>
      <form @submit.prevent>
        <label for="texto"></label>
        <input v-model="texto" id="texto" type="text" />
      </form>

      <div>
        <h3>Cantidad de caracteres: {{ cantidadCaracteres }}</h3>
      </div>

      <div v-if="texto">
        <h2></h2>
        <ul>
          <li><strong>Codificado:</strong> {{ codificarTexto(texto) }}</li>
          <li><strong>Todo en mayúscula:</strong> {{ texto.toUpperCase() }}</li>
          <li><strong>Todo en minúscula:</strong> {{ texto.toLowerCase() }}</li>
          <li><strong>Intercalado (mayúscula primero):</strong> {{ alternarTexto(texto, true) }}</li>
          <li><strong>Intercalado (minúscula primero):</strong> {{ alternarTexto(texto, false) }}</li>
        </ul>
      </div>
    </div>
  </div>

  <p>respuestas: - 1:C y creo que la d pero siempre uso la c. - 2:C - 3:A </p>
</template>

<script>
export default {
  data() {
    return {
      texto: ''
    };
  },
  computed: {
    cantidadCaracteres() {
      return this.texto.length;
    }
  },
  methods: {
    codificarTexto(texto) {
      const vocales = {
        'a': 'u',
        'e': 'o',
        'i': 'i',
        'o': 'e',
        'u': 'a'
      };
      return texto.toLowerCase().split('').map(char => vocales[char] || char).join('');
    },
    alternarTexto(texto, mayusculaInicial) {
      return texto.split('').map((char, index) => {
        if (mayusculaInicial) {
          return index % 2 === 0 ? char.toUpperCase() : char.toLowerCase();
        } else {
          return index % 2 === 0 ? char.toLowerCase() : char.toUpperCase();
        }
      }).join('');
    }
  }
};
</script>

<style>
  h1 {
    color: crimson;
  }
  h2 {
    color: blue;
  }
</style>
