<template>
  <div class="app">
    <h1>Hello there</h1>
    <p class="intro">Lorem ipsum dolor sit amet consectetur adipisicing elit. Veniam, exercitationem? Commodi beatae molestiae at. Libero corporis, cupiditate sapiente consequatur suscipit dolor quibusdam sunt mollitia expedita voluptas. Pariatur magnam illum quod.</p>
    <Brewerys :brewerys="brewerys" />
    <Map></Map>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from 'vue'
import Brewerys from './components/Brewerys.vue'
import Map from './components/Map.vue';
import { Bar } from './types/Bar';

export default defineComponent({
  name: 'App',
  components: { Brewerys, Map },
  setup() {
    const brewerys = ref<Bar[]>([
        {
        "id": 11767,
        "obdb_id": "ironbark-brewery-jackson",
        "name": "Ironbark Brewery",
        "brewery_type": "micro",
        "street": "2610 Kibby Rd",
        "address_2": null,
        "address_3": null,
        "city": "Jackson",
        "state": "Michigan",
        "county_province": null,
        "postal_code": "49203-4908",
        "country": "United States",
        "longitude": "-84.43762976",
        "latitude": "42.2188971",
        "phone": "5177487988",
        "website_url": null,
        "updated_at": "2018-08-24T00:00:00.000Z",
        "created_at": "2018-07-24T00:00:00.000Z"
        }
      ])   
      
    onMounted( () => {
      console.log('component mounted')
      
    })

    return { brewerys }  
  }
});
</script>

<style>

</style>
