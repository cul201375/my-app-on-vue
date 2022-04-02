<template>
  <div id="PokeApp">
    <div class="bg-dark container p-3">
      <div class="d-flex flex-column">
        <label for="pokemon"
          ><p class="text-success text-uppercase">Buscar un pokemon</p></label
        >
        <div class="d-flex flex-row">
          <input
            class="form-control me-2"
            type="text"
            name="pokemon"
            splaceholder="Nombre del pokemon"
            aria-label="pokemon"
            v-model="q"
          />
          <button
            class="btn btn-outline-success"
            type="submit"
            v-on:click="getPokemon()"
          >
            Buscar
          </button>
        </div>
      </div>
      <h1 class="text-warning p-1">ESTO ES LA API DE POKEMON</h1>

      <div v-if="pokedata != undefined">
        <div class="overflow-auto">
          <table class="table table-responsive table-bordered border-primary">
            <thead class="text-white">
              <tr class="border-success">
                <th scope="col">IMAGEN</th>
                <th scope="col">NOMBRE</th>
                <th scope="col">HABILIDADES</th>
                <th scope="col">TIPOS</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <th><img class="img-fluid" :src="pokedata.img" /></th>
                <td>
                  <p class="text-success">{{ pokedata.name }}</p>
                </td>
                <td>
                  <ul class="text-success">
                    <li
                      v-for="ability in pokedata.abilities"
                      v-bind:key="ability"
                    >
                      {{ ability.ability.name }}
                    </li>
                  </ul>
                </td>
                <td>
                  <ul class="text-success">
                    <li v-for="type in pokedata.types" v-bind:key="type">
                      {{ type.type.name }}
                    </li>
                  </ul>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
      <div v-if="pokedata.error != null">
        <div class="alert alert-danger" role="alert">
          Poke{{ pokedata.error }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "PokeApp",
  el: "#PokeApp",
  data() {
    return {
      pokedata: {
        name: "",
        img: "",
        abilities: {},
        types: [],
        error: null,
      },
      q: "",
      error: {},
    };
  },
  created() {},
  methods: {
    getPokemon() {
     this.q = this.q.toLowerCase();
      axios
        .get("https://pokeapi.co/api/v2/pokemon/" + this.q)
        .then((response) => {
          this.getSprites(
            response.data.sprites.other.dream_world.front_default
          ),
            this.getName(response.data),
            this.getAbilities(response.data),
            this.getType(response.data.types);
        })
        .catch((error) => {
          this.pokedata.error = error;
        });
    },
    getSprites(sprites) {
      this.pokedata.img = sprites;
      console.log(this.pokedata.img);
    },
    getName(data) {
      this.pokedata.name = data.name;
      console.log(this.pokedata.name);
    },
    getAbilities(data) {
      this.pokedata.abilities = data.abilities;
      console.log(this.pokedata.abilities);
    },
    getType(data) {
      this.pokedata.types = data;
      console.log(this.pokedata.types);
    },
  },
};
</script>