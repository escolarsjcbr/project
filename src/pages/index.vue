<template>
  <q-page>

    <div class="row">
      <div class="col-md-12 q-ma-sm">
        <p>Exibindo motoristas próximos a você:</p>
      </div>
    </div>

    <div class="row">
      <div v-for="n in 10" :key="n" class="col-md-3">
        <q-card inline class="bigger q-ma-sm">
          <q-card-media>
            <img src="~assets/van.jpeg">
          </q-card-media>
          <q-card-title class="relative-position">
            <q-btn fab color="primary" icon="place" class="absolute" style="top: 0; right: 8px; transform: translateY(-50%);" />

            <div class="ellipsis">Cafe Basilico</div>
            <q-rating slot="subtitle" v-model="stars" :max="5" />
            <div slot="right" class="row items-center">
              <q-icon name="place" /> 2,5 km
            </div>
          </q-card-title>
          <q-card-main>
            <p>$・Italian, Cafe</p>
            <p class="text-faded">Small plates, salads & sandwiches in an intimate setting.</p>
          </q-card-main>
          <q-card-separator />
          <q-card-actions>
            <q-btn flat round icon="event" />
            <q-btn flat>5:30PM</q-btn>
            <q-btn flat>7:30PM</q-btn>
            <q-btn flat>9:00PM</q-btn>
            <q-btn flat color="primary">Reserve</q-btn>
          </q-card-actions>
        </q-card>
      </div>
    </div>

  </q-page>
</template>

<style>
</style>

<script>
import {
  Loading,

  // optional!, for example below
  // with custom spinner
  QSpinnerPuff
} from 'quasar'

export default {
  name: 'PageIndex',
  data () {
    return {
      stars: 5
    }
  },
  created () {
    Loading.show({
      spinner: QSpinnerPuff,
      message: 'Identificando sua localização. Permita encontrarmos sua localição.',
      messageColor: 'white',
      spinnerSize: 250,
      spinnerColor: 'white',
      customClass: 'bg-primary'
    })

    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(showPosition, showError)
    } else {
      alert('Geolocation is not supported by this browser.')
    }

    function showPosition (position) {
      // x.innerHTML = "Latitude: " + position.coords.latitude +
      // "<br>Longitude: " + position.coords.longitude;
      console.log(position)
      Loading.hide()
    }

    function showError (error) {
      switch (error.code) {
        case error.PERMISSION_DENIED:
          console.log('User denied the request for Geolocation.')
          break
        case error.POSITION_UNAVAILABLE:
          console.log('Location information is unavailable.')
          break
        case error.TIMEOUT:
          console.log('The request to get user location timed out.')
          break
        case error.UNKNOWN_ERROR:
          console.log('An unknown error occurred.')
          break
      }
    }
  }
}
</script>
