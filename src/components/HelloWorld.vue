<template>
  <div class="cotainer-fluid">
    <h1>{{ msg }}</h1>
    <div class="container-fluid w-50">
      <p>
        Este proyecto esta hecho completamente con <a target="_blank" href="https://v2.vuejs.org/">Vue.js</a> y con las librerias de 
        <a target="_blank" href="https://nodejs.dev/">Node npm Axios</a> para peticiones Https a la <a target="_blank" href="https://pokeapi.co/">Pokeapi</a> y 
        <a target="_blank" href="https://developer.mozilla.org/es/docs/Web/API/Fetch_API/Using_Fetch">Fetch</a> para <a target="_blank" href="https://openweathermap.org/current">Weather</a>.
        <span>Aplicaciones web hechas por <a target="_blank" href="https://github.com/cul201375">Emanuel Castillo</a></span>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
