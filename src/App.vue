<template>
<div class="bg-dark text-white p-2">
    <nav>
      <div>
        <router-link class="mt-1 me-2 btn btn-success text-white" to="/">Home</router-link>
        <router-link class="mt-1 btn btn-success text-decoration-none text-white" to="/pokeapp">PokeApp</router-link>
        <router-link class="mt-1 ms-2 btn btn-success text-decoration-none text-white" to="/weatherapp">WeatherApp</router-link>
      </div>
    </nav>
</div>
<div class="container mt-3">
  <div class="d-flex flex-column justify-content-center">
    <router-view/>
  </div>
</div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
