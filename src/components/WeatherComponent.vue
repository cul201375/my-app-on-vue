<template>
  <div id = "ClimaApp" class="w-100">
    <div class="bg-dark container p-3 mb-5">

    <div class="d-flex flex-column">
        <label for="Latitud"><p class="text-success text-uppercase">Buscar el clima de una ciudad</p></label>
        <div class="d-flex flex-row">
            <input class="form-control me-2" type="text" name="Latitud" placeholder="Latitud" aria-label="Latitud" v-model="lat">
            <input class="form-control me-2" type="text" name="Longitud" placeholder="Longitud" aria-label="Longitud" v-model="lon">
            <button class="btn btn-outline-success" type="submit" v-on:click="getWeather()">Buscar</button>
        </div>
    </div>
        <div class="container-fluid mt-5">
            <div class="d-flex justify-content-center">
                    <div class="appclima">
                        <div v-if="weather.main != undefined">
                            <h1>{{weather.weather[0].main}}</h1>
                            <h6>{{weather.weather[0].description}}</h6>
                            <h3>{{weather.main.temp}}</h3>
                            <h6>{{weather.name}}, {{weather.sys.country}}</h6>
                        </div>
                    </div>
            </div>
        </div>
        <div class="container-fluid mt-5">
                <div class="alert alert-danger" role="alert" v-if="error != undefined">
                   Error: Code: {{error.code}} Message: {{error.message}}
                </div>
        </div>
        <div>
            <span class="text-white">puedes darle en <strong>Ampliar el mapa</strong> para buscar coordenas de papises</span>
            <br>
            <br>
            <br>
            <iframe
                height="400"
                style="border:0; width: 100%;"
                loading="lazy"
                allowfullscreen
                referrerpolicy="no-referrer-when-downgrade"
                src="https://www.google.com/maps/embed/v1/place?key=AIzaSyCtCRmM0Q8pMGuy7_hUIeGUcxg9Wh_TLEE&q=Space+Needle,Seattle+WA">
            </iframe>
        </div>
    </div>
  </div>
</template>

<script>
//import axios from "axios";
export default {
  name: "WeatherComponent",
  data(){
    return{
        lat: '',
        lon: '',
        weather: {},
        error: null
    }
  },
  methods:{
        getWeather(){
            fetch('https://api.openweathermap.org/data/2.5/weather?lat='+this.lat+'&lon='+this.lon+'&appid=0c7ef183a5dee617fade05e411bcf808')
            .then( response =>  response.json())
            .then(data => this.setResult(data))
            .catch(this.error = {code: '400', message:'Nada para geolocalizar'});
        },
        setResult (res){
            this.weather = res;
        }
  }
};
</script>

<style>
.appclima{
    width: 360px;
    background-image: url('https://images.wallpaperscraft.com/image/single/horizon_sunrise_sea_sun_118911_360x640.jpg');
    height: 640px;
}
.appclima div h1{
    color: white;
    font-family: 'Rubik', sans-serif;
}
.appclima div h3{
    color: white;
}
.appclima div h6{
    color: white;
}
</style>