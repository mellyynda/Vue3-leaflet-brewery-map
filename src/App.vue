<template>
  <div class="app">
    <h1>Hello there</h1>
    <p class="intro">Lorem ipsum dolor sit amet consectetur adipisicing elit. Veniam, exercitationem? Commodi beatae molestiae at. Libero corporis, cupiditate sapiente consequatur suscipit dolor quibusdam sunt mollitia expedita voluptas. Pariatur magnam illum quod.</p>
    <Brewerys v-if="showBars" :brewerys="brewerys" />
    <div v-else class="loading">loading...</div>
    <Map></Map>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import Brewerys from './components/Brewerys.vue'
import Map from './components/Map.vue'
import { Bar } from './types/Bar'
import axios from 'axios'

export default defineComponent({
  name: 'App',
  components: { Brewerys, Map },
  setup() {
    const showBars = ref(false)
    const brewerys = ref<Bar[]>()   
      
    axios.get('https://api.openbrewerydb.org/breweries')
      .then(res => {
        showBars.value = true
        brewerys.value = res.data
      })

    return { showBars, brewerys }  
  }
});
</script>

<style>

</style>
