<template>
  <div id="app">
    <p>{{total}}</p>

    <button @click="calcula('-')"> - </button>
    <button @click="calcula('+')"> + </button>

    <p>Nome Computado: {{ nomeFormatado }}</p>
    <label>Input a computar</label>
    <input v-model="nomeFormatado" type="text">

    <p>Nome Iniciado: {{ nome }}</p>
    <p>Nome Filtrado: {{ nome | formataNome }}</p>

    <input v-model="busca" type="text">
    <p v-text="resultado"></p>
    
    <input v-model="nome" type="text">
    <small v-text="nome"></small>

    <button @click="funcao(nome)"> Botao Top </button>
    <p>Numero de caracteres: {{ nome | numeroCaracteres }}</p>
  </div>
</template>

<script>
export default {
  name: 'lv-contador',
  data () {
    return {
      total: 10,
      nome: 'jose antonio',
      resultado: '',
      busca: ''
    }
  },
  watch: {
      busca: function (novoValor, valorAntigo) {
      this.resultado = 'Aguardando o término da digitação...'
      console.log('Novo valor: ' + novoValor)
      this.recolheResposta()
      console.log('Valor antigo: ' + valorAntigo)
    }
  },
  methods: {
    calcula( sinal ) {
      this.total = (sinal == '-') ? this.total - 1 : this.total + 1
    },
    recolheResposta() {
      let valor = this.busca
      setTimeout( () => {
        if(valor == this.busca)
          this.resultado = 'Terminou de digitar...'
      }, 500)
    },
    funcao(nomeDoAmiguinho) {
      console.log(nomeDoAmiguinho + " eh o nome do amiguinho")
    }
  },
  filters: {
    formataNome( valor ) {
      console.log('executando filter')
      valor = valor.toLowerCase()
      let corta = valor.split(' ')
      let resultado = ''
      for (let nome of corta)
      resultado += nome.charAt(0).toUpperCase() + nome.slice(1) + ' '
      return resultado
      
    },
    numeroCaracteres( valor ) {
      return valor.length
    }
  },
  computed: {
    nomeFormatado: {
      get: function() {
        console.log('executando computed')
        return this.nome.toUpperCase()
      },
      set: function(novoValor) {
        this.nome = novoValor.substring(0, 3)
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
