<template>
  <div class="WeatherComponent">
    <WeatherComponent/>
  </div>
</template>

<script>
// @ is an alias to /src
import WeatherComponent from '@/components/WeatherComponent.vue'

export default {
  name: 'WeatherApp',
  components: {
    WeatherComponent
  }
}
</script>
